---
title: Mod Web Pages
description: Adding Blazor pages, static assets and config editor entries to a server mod.
published: true
date: 2026-07-21T00:00:00.000Z
tags: modding, web
editor: markdown
dateCreated: 2026-07-21T00:00:00.000Z
---

> This page applies to SPT version `4.1`
{.is-info}

The server hosts a web interface. Mods can add their own pages to it, serve static files, expose API endpoints, and register their config so users can edit it in the browser instead of hand-editing JSON.

Everything here is opt-in. A mod that doesn't implement `IModBlazorMetadata` is untouched by any of it.

## Opting in

Implement `IModBlazorMetadata` alongside `IModMetadata` on your metadata class.

```csharp
public sealed class MyModMetadata : IModMetadata, IModBlazorMetadata
{
    public string ModGuid { get; init; } = "com.example.my-mod";
    // ... rest of IModMetadata

    public string? WWWRootUrl { get; init; }
    public string? HomePage { get; init; } = "/my-mod";
    public string? HomePageDescription { get; init; } = "Settings for My Mod";
}
```

The interface is just a marker. Implementing it tells the server to link your `wwwroot` directory, register your Blazor components and pages for routing, and register your MVC controllers.

| Property | What it does |
| --- | --- |
| `WWWRootUrl` | URL segment your static files are served under. Leave `null` to use your assembly name. |
| `HomePage` | Path to your page. Setting this puts a card for your mod in the SIC mod links section. Leave `null` for no card. |
| `HomePageDescription` | The description shown on that card. |

Your project also needs `Microsoft.NET.Sdk.Web` rather than the plain SDK, a reference to `SPTarkov.Server.Web`, and `<OutputType>Library</OutputType>`.

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <OutputType>Library</OutputType>
  </PropertyGroup>
  <ItemGroup>
    <ProjectReference Include="..\Libraries\SPTarkov.Server.Web\SPTarkov.Server.Web.csproj" />
  </ItemGroup>
</Project>
```

## Adding a page

Blazor pages go anywhere in your project. The server picks them up from your assembly.

```razor
@using Microsoft.AspNetCore.Components.Web
@rendermode InteractiveServer
@page "/my-mod"

<h3>My Mod</h3>

<p>Current count: @count</p>
<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    private int count = 0;

    private void IncrementCount()
    {
        count++;
    }
}
```

Make the `@page` route match the `HomePage` you set in your metadata, otherwise the card links nowhere.

Pick a route that won't collide with another mod. Prefixing everything with your mod name is usually enough.

## Static files

Put files in a `wwwroot` folder in your mod directory and they're served under `/<WWWRootUrl>/`, or `/<AssemblyName>/` if you left `WWWRootUrl` null.

```razor
<img src="/MyMod/logo.png" alt="My Mod" />
```

Two mods claiming the same `wwwroot` URL is a hard startup failure, not a warning. If you set `WWWRootUrl` manually, make it specific.

Your build needs to copy `wwwroot` to the mod's output folder alongside the DLL. It's easy to forget and the symptom is just missing files.

## API endpoints

Standard MVC controllers work, and are registered from your assembly automatically.

```csharp
public class MyModController : Controller
{
    [HttpGet("/my-mod/ping")]
    public IActionResult Ping()
    {
        return Content("Pong");
    }
}
```

These are strictly for your own endpoints, things your web page calls, or tooling you're exposing outside the game.

Anything the game client talks to still goes through the router system. If you're handling a Tarkov route, overriding one of ours, or responding to something the client sends, write a router. See [Routers](/modding/SPT_411/Server_4.0_to_4.1#routers).

## Registering your config for editing

Register a config object and it becomes editable in the server's config editor, with changes written back to your JSON file. You need two things: the config class itself, and a provider that describes it.

**The config**

A plain class. Use `[JsonPropertyName]` so the names in the file stay stable if you rename things in code.

```csharp
public class MyModConfig
{
    [JsonPropertyName("enabled")]
    public bool Enabled { get; set; } = true;

    [JsonPropertyName("spawnMultiplier")]
    public double SpawnMultiplier { get; set; } = 1.25;

    [JsonPropertyName("allowedMaps")]
    public List<string> AllowedMaps { get; set; } = ["factory4_day", "bigmap"];

    [JsonPropertyName("features")]
    public Dictionary<string, bool> Features { get; set; } = new() { ["someFeature"] = false };
}
```

Give every setting a getter and a setter. Applying an edit copies the changed values onto the instance you registered, but only properties that are both readable and writable get copied. An `init` or get-only property is skipped without complaint.

Don't put `[Injectable]` on the config class if it's loaded from a file. That has the container build a fresh instance from your defaults and your JSON is never read. Load it yourself and register the instance through `IOnDIConstruct`, covered in [Registering your config into DI](/modding/SPT_411/Server_4.0_to_4.1#registering-your-config-into-di).

**The provider**

Implement `IConfigEditorConfigProvider` and hand back a registration.

```csharp
[Injectable(InjectionType.Singleton)]
public class MyModConfigEditorProvider(MyModConfig config) : IConfigEditorConfigProvider
{
    public IEnumerable<ConfigEditorConfigRegistration> GetConfigs()
    {
        yield return ConfigEditorConfigRegistration.Create(
            "com.example.my-mod",
            "My Mod Config",
            config,
            Path.Combine("user", "mods", "MyMod", "config.json")
        );
    }
}
```

`Create` takes an id (use your mod GUID), the display name shown in the editor, the config instance, and the path to persist to. The path is relative to the server folder.

`GetConfigs` returns a sequence, so a mod with several config files can `yield return` one registration per file.

The editor builds its UI from your config's shape, so you don't write any UI for it. If you want something more custom than what it gives you, make your own page instead.

Applying and saving are separate. Applying copies the edited values onto your live instance, saving writes them to your file. A user can do one without the other, so don't assume an edit you can see in memory has been persisted, or the reverse.

`Create` covers the common case. If you need to hide sections from the structured editor, or take over how the config is loaded, saved or applied, construct `ConfigEditorConfigRegistration` directly and set the optional members on it. Note that the load, save and apply hooks replace the default behaviour rather than running alongside it.

## Related

- [Server Mod Migration - 4.0 to 4.1](/modding/SPT_411/Server_4.0_to_4.1), where `IModWebMetadata` was renamed to `IModBlazorMetadata`
