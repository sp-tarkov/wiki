---
title: Prepatching
description: Modifying SPTarkov.Server.Core before it loads, using Mono.Cecil.
published: true
date: 2026-07-21T00:00:00.000Z
tags: modding, patching
editor: markdown
dateCreated: 2026-07-21T00:00:00.000Z
---

> This page applies to SPT version `4.1`
{.is-info}

A prepatcher edits `SPTarkov.Server.Core` at the IL level before it is loaded. In practice this means one thing: adding your own constants to Core's enums.

## Do you actually need one?

Only if you need to extend an enum. Enum constants are baked in at compile time, so there's no way to add one to an assembly that's already loaded. The patch has to happen first.

Everything else belongs in a [Harmony patch](/SPT_41/Server_4.0_to_4.1#patching). If you want to change what a method does, runtime patching is simpler and much easier to debug.

Prepatching runs before the server has a logger, a database, or DI. There's no support beyond the console, and a broken prepatcher takes the whole server down before it can tell you why.

## How it works

Prepatchers live in `[game folder]\SPT\user\patchers\`, not `user\mods\`, and each one goes in a folder named for the mod's GUID:

```
user\patchers\com.example.my-mod\MyModPatcher.dll
```

The folder name has to match your `ModGuid` exactly. The server looks for `user\patchers\<ModGuid>\` and fails on startup if it isn't there, naming the directory it expected. The DLL itself can be called anything, the first one found at the top level of that folder is used, so don't put anything else in there.

On startup, before any mod loads, the server collects prepatchers, applies them to an in-memory copy of `SPTarkov.Server.Core`, then reboots itself into a load context using the patched assembly. Every mod that loads afterwards sees the patched Core.

The patched assembly is written out as `SPTarkov.Server.Core.Patched.dll` alongside a `.pdb`, which is what makes debugging a prepatched server possible. Both are deleted and rebuilt on every start, so removing the prepatcher gets you an unmodified server next run.

If your mod ships a prepatcher, set `HasPrepatcher = true` in its metadata.

```csharp
public sealed class MyModMetadata : IModMetadata
{
    // ...
    public bool HasPrepatcher { get; init; } = true;
}
```

## Writing one

Inherit `AbstractPrepatch`. The module you're modifying is handed to you.

```csharp
public class MyPrepatch(ModuleDefinition serverCoreModule) : AbstractPrepatch(serverCoreModule)
{
    public override string ModGuid => "com.example.my-mod";
    public override bool IsActive => true;

    public override void Patch()
    {
        AddNewEnumConstant<SkillTypes>("MySkill", 99);
    }
}
```

`ModGuid` must match the mod the prepatcher belongs to. `IsActive` lets you switch it off without removing the file. `Patch` does the work.

`AddNewEnumConstant<T>(name, value)` is the method you want. Both the name and the number must be unique within that enum. Nothing checks this for you, and a collision gives you an enum that behaves strangely rather than one that fails loudly.

### Other helpers

`AbstractPrepatch` also exposes lookups against the module, for the rare case you need to reach something directly. All of them throw `PatchException` naming what they couldn't find, rather than returning null.

| Method | Returns |
| --- | --- |
| `GetTypeDefinition<T>()` | The `TypeDefinition` for a type |
| `GetMethod<T>(name)` | A `MethodDefinition` on that type |
| `GetField<T>(name)` | A `FieldDefinition` |
| `GetProperty<T>(name)` | A `PropertyDefinition` |

What you do with those is plain [Mono.Cecil](https://github.com/jbevain/cecil).

## Verifying it worked

Your mod loads after the patched Core, so it can check its own prepatch applied:

```csharp
[Injectable(TypePriority = OnLoadOrder.PostLoad + 1)]
public class MyMod(ISptLogger<MyMod> logger) : IOnLoad
{
    public Task OnLoadAsync(CancellationToken cancellationToken)
    {
        if (Enum.TryParse<SkillTypes>("MySkill", out var injected))
        {
            logger.Info($"Prepatch applied: MySkill = {(int)injected}");
        }
        else
        {
            logger.Warning("Prepatch NOT applied: MySkill missing from SkillTypes");
        }

        return Task.CompletedTask;
    }
}
```

## Things to know

**Your changes affect every mod.** You're modifying Core for the entire server, not just for yourself. Change as little as possible.

**Other prepatchers are running too.** They apply to the same module in the same pass. If two prepatchers touch the same type, the result depends on ordering you don't control.

## Related

- [Server Mod Migration - 4.0 to 4.1](/SPT_41/Server_4.0_to_4.1#prepatching), where prepatching was added
