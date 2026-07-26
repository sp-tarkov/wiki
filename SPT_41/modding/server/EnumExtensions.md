---
title: Enum Extensions
description: Modifying SPTarkov.Server.Core before it loads, using Mono.Cecil.
published: true
date: 2026-07-26T06:42:01.253Z
tags: modding, patching
editor: markdown
dateCreated: 2026-07-21T14:20:18.887Z
---

> This page applies to SPT version `4.1`
{.is-info}

A prepatch adds constants, fields, or other image data to an assembly before the assembly containing that code is loaded.

SPT supports enum prepatching on both sides:

- Server enum constants are declared in a JSON file and added to `SPTarkov.Server.Core`.
- Client enum constants are registered by a server mod, sent to the client as JSON, and added to `Assembly-CSharp`.

Prepatchers are declarative. You no longer create a prepatcher DLL, inherit `AbstractPrepatch`, or edit assemblies directly with Mono.Cecil.

## Do you actually need one?

Enum fields are compile time constants that are baked in when code is compiled, so a new named constant must be added before the relevant assembly loads.

You may need one, when for example you do any of the following:
- When you want to add a new bot type.
- When you want to add a new skill.
- Anything else that requires a new Enum entry.

> The server and client definitions are separate. A JSON file in `user\patchers` is not automatically sent to the client.
{.is-warning}

## Server-side prepatching

### Folder layout

Server prepatch definitions live in `[game folder]\SPT\user\patchers\`, not `user\mods`.

Each mod gets a directory named after its GUID:

```text
user\patchers\com.example.my-mod\MyModPrepatch.json
```

The directory name must match the mod's `ModGuid`. The directory must contain exactly one JSON file at its top level. The filename itself can be anything.

If the mod ships a server enum extension declaration, set `HasEnumExtensions = true` in your mod's metadata:

```csharp
public sealed class MyModMetadata : IModMetadata
{
    // ...
    public bool HasPrepatcher { get; init; } = true;
}
```

### Writing the definition

The file must contain a non-empty JSON array:

```json
[
  {
    "enumType": "SPTarkov.Server.Core.Models.Enums.SkillTypes",
    "constantName": "MySkill",
    "constantValue": 99
  }
]
```

Each entry supports the following properties:

| Property | Required | Description |
| --- | --- | --- |
| `enumType` | Yes | Fully qualified name of the enum to extend |
| `constantName` | Yes | Name of the new enum constant |
| `constantValue` | Yes | Numeric value of the new constant |
| `jsonEnumName` | No | Client-only serialization name; ignored by the server patcher |

For nested enum types, separate the containing and nested types with `+`:

```json
{
  "enumType": "Some.Namespace.ContainingType+NestedEnum",
  "constantName": "MyValue",
  "constantValue": 100
}
```

`constantValue` is read as a signed 64-bit integer and converted to the enum's actual underlying type. Startup reports an error if the value does not fit that type.

### How it works

Before loading server mods, the server:

1. Reads the prepatch directories.
2. Loads `SPTarkov.Server.Core` into memory.
3. Applies definitions in deterministic order by mod GUID and definition path.
4. Writes `SPTarkov.Server.Core.Patched.dll` and its `.pdb`.
5. Starts the server using the patched Core assembly.

The patched assembly and symbols are deleted and rebuilt on every start. Removing the prepatch directory therefore restores an unmodified server on the next run.

Definitions are processed before mod assemblies load, so a server prepatch cannot run mod code, resolve dependencies, access the database, or perform arbitrary Mono.Cecil edits.

### Packaging the definition

For example, a project can copy its definition after building:

```xml
<ItemGroup>
  <PrepatchDefinition Include="$(ProjectDir)MyModPrepatch.json" />
</ItemGroup>

<Target Name="CopyPrepatchDefinition" AfterTargets="Build">
  <Copy
    SourceFiles="@(PrepatchDefinition)"
    DestinationFolder="$(GamePath)\SPT\user\patchers\com.example.my-mod"
  />
</Target>
```

Adjust `$(GamePath)` to match your project setup.

### Verifying the server Enum extension

Your mod loads against the patched Core, so it can verify that the new constant exists:

```csharp
[Injectable(TypePriority = OnLoadOrder.PostLoad + 1)]
public class MyMod(ISptLogger<MyMod> logger) : IOnLoad
{
    public Task OnLoadAsync(CancellationToken cancellationToken)
    {
        if (Enum.TryParse<SkillTypes>("MySkill", out var injected))
        {
            logger.Info($"Server prepatch applied: MySkill = {(int)injected}");
        }
        else
        {
            logger.Warning("Server prepatch NOT applied: MySkill is missing");
        }

        return Task.CompletedTask;
    }
}
```

## Client-side Enum extensions

Client enum definitions are registered by a server mod through the `ClientEnumDefinitions` service.

When the game starts, SPT's built-in client prepatcher requests the registered definitions from the server and applies them to `Assembly-CSharp` before that assembly loads.

> Do not place a custom prepatcher DLL in BepInEx for this purpose.
{.is-info}

### Registering client definitions

Inject `ClientEnumDefinitions` into a server mod class and register the entries during server startup:

```csharp
using SPTarkov.DI.Annotations;
using SPTarkov.Server.Core.DI;
using SPTarkov.Server.Core.Models.Spt.Mod;

[Injectable(TypePriority = OnLoadOrder.PostLoad + 1)]
public class MyMod(ClientEnumDefinitions clientEnumDefinitions) : IOnLoad
{
    public Task OnLoadAsync(CancellationToken cancellationToken)
    {
        clientEnumDefinitions.Add(
            "com.example.my-mod",
            new EnumEntryDefinition
            {
                EnumType = "EFT.EBuffId",
                ConstantName = "MyBuff",
                ConstantValue = 10000,
                JsonEnumName = "my_buff",
            }
        );

        return Task.CompletedTask;
    }
}
```

The key passed to `Add` should be the mod's GUID.

Use `AddRange` to register several definitions:

```csharp
clientEnumDefinitions.AddRange(
    "com.example.my-mod",
    [
        new EnumEntryDefinition
        {
            EnumType = "EFT.EBuffId",
            ConstantName = "MyFirstBuff",
            ConstantValue = 10000,
            JsonEnumName = "my_first_buff",
        },
        new EnumEntryDefinition
        {
            EnumType = "EFT.EBuffId",
            ConstantName = "MySecondBuff",
            ConstantValue = 10001,
            JsonEnumName = "my_second_buff",
        },
    ]
);
```

A mod that only registers client definitions does not need `HasPrepatcher = true` or a directory under `user\patchers`.

### Client definition fields

Client definitions use the same `EnumEntryDefinition` model:

| Property | Description |
| --- | --- |
| `EnumType` | Fully qualified enum type from `Assembly-CSharp`, such as `EFT.EBuffId` |
| `ConstantName` | Name of the new enum field |
| `ConstantValue` | Numeric value assigned to the field |
| `JsonEnumName` | Optional value for EFT's `JsonEnumNameAttribute` |

When `JsonEnumName` is set, the client prepatcher attaches `EFT.JsonEnumNameAttribute` to the new field. Use it when the enum has a separate string representation in JSON. It may be different from `ConstantName`.

### How client definitions reach the game

The client prepatcher:

1. Reads the backend URL passed by the SPT Launcher.
2. Requests `/singleplayer/customEnumEntries` from the server.
3. Deserializes the returned JSON definitions.
4. Adds them to their target enums in `Assembly-CSharp`.
5. Allows the game to continue loading with the patched assembly.

The server must be running and the definitions must be registered before the game starts.

### Verifying the client patch

A normal client plugin loads after `Assembly-CSharp` has been patched, so it can verify the constant with `Enum.TryParse`:

```csharp
if (Enum.TryParse<EFT.EBuffId>("MyBuff", out var injected))
{
    Logger.LogInfo($"Client prepatch applied: MyBuff = {(int)injected}");
}
else
{
    Logger.LogError("Client prepatch NOT applied: MyBuff is missing");
}
```

## Using matching server and client values

When the same logical value exists on both sides, register it separately for each assembly and keep the name and number synchronized.

For example, the server definition could contain:

```json
[
  {
    "enumType": "SPTarkov.Server.Core.Models.Enums.SomeServerEnum",
    "constantName": "MyValue",
    "constantValue": 100
  }
]
```

The server mod would register the corresponding client definition:

```csharp
clientEnumDefinitions.Add(
    "com.example.my-mod",
    new EnumEntryDefinition
    {
        EnumType = "EFT.SomeClientEnum",
        ConstantName = "MyValue",
        ConstantValue = 100,
        JsonEnumName = "MyValue",
    }
);
```

The server and client enum types do not need to have the same fully qualified name, but their numeric values must agree if the value crosses the client/server boundary.

## Things to know

**Names and values must be unique.** Both patchers reject an entry when the target enum already contains its name or numeric value.

**Values must fit the enum's underlying type.** For example, a value outside the range of a byte-backed enum is rejected.

**Type and constant names are case-sensitive.** Use the exact names from the target assembly.

**Your changes are global.** A patched enum affects every mod using that server or client assembly.

**Other mods may patch the same enum.** Do not rely on another mod's definition being applied before yours. Coordinate enum value ranges when mods extend shared types.

**Keep server and client definitions synchronized.** A mismatched numeric value can serialize correctly on one side but be interpreted as a different value on the other.

**Prepatching is for enum constants only.** Arbitrary IL changes and the old `AbstractPrepatch` helpers are no longer supported. Use Harmony for behavioral changes.

## Related

- [Server Mod Migration - 4.0 to 4.1](/SPT_41/Server_4.0_to_4.1#prepatching), where prepatching was added
