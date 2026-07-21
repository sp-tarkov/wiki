---
title: Server Mod Migration - 4.0 to 4.1
description: What changed for server mods between SPT 4.0 and 4.1, and how to fix it.
published: true
date: 2026-07-21T00:00:00.000Z
tags: modding, migration
editor: markdown
dateCreated: 2026-07-21T00:00:00.000Z
---

> This page applies to SPT version `4.1`
{.is-info}

> Every 4.0 server mod needs rebuilding against 4.1. The server checks which version of `SPTarkov.Server.Core` your mod was built against and refuses to load it if that doesn't match.
{.is-warning}

A rundown of what changed for server mods between 4.0 and 4.1, and what to do about each one.

## Metadata

`AbstractModMetadata` was an abstract record. It's now an interface, which makes what a mod has to provide clearer.

**4.0**
```csharp
public record MyModMetadata : AbstractModMetadata
{
    public override string ModGuid { get; init; } = "com.example.my-mod";
    public override Range SptVersion { get; init; } = new("~4.0.0");
    public override bool? IsBundleMod { get; init; }
    // ...
}
```

**4.1**
```csharp
public record MyModMetadata : IModMetadata
{
    public string ModGuid { get; init; } = "com.example.my-mod";
    public Range SptVersion { get; init; } = new("~4.1.0");
    // ...
}
```

Remove every `override`, and remove `IsBundleMod`.

## Load and update

Both lifecycle methods are async and receive a token that's cancelled when the server shuts down (CTRL+C).

**4.0**
```csharp
public Task OnLoad() { ... }
public Task<bool> OnUpdate(long secondsSinceLastRun) { ... }
```

**4.1**
```csharp
public Task OnLoadAsync(CancellationToken cancellationToken) { ... }
public Task<bool> OnUpdateAsync(long secondsSinceLastRun, CancellationToken cancellationToken) { ... }
```

Propagate the token to anything that takes one, such as file I/O, HTTP calls and delays, so the server can shut down smoothly. For long synchronous work, call `cancellationToken.ThrowIfCancellationRequested()` periodically.

Let `OperationCanceledException` propagate. Cancellation is not an error.

## Load order

Load order matters a lot less than it used to. The database and config files are already loaded by the time anything starts, so there's no stage where the data isn't there yet.

If your mod ran on `PostDBModLoader`, run it on `PostLoad`.

Full list, low to high: `Watermark`, `Preload`, `GameCallbacks`, `TraderRegistration`, `Routers`, `HandbookCallbacks`, `SaveCallbacks`, `TraderCallbacks`, `PresetCallbacks`, `RagfairCallbacks`, `PostLoad`.

The gaps between values are 100000, so there's room to slot in between stages if you do need to.

### Routers

Routers now respect priority. They were always registered through DI, but the priority you gave them was ignored. Every built-in router sits on `OnLoadOrder.Routers` exactly, so you position yours relative to that.

Which offset you want depends on whether you're overriding one of SPT's routes or adding a new one.

**A custom route**, on a URL SPT doesn't already handle, always goes one above:

```csharp
[Injectable(TypePriority = OnLoadOrder.Routers + 1)]
```

Nothing of ours answers that URL, so there's nobody to order against and no reason to sit below us. Use whatever offset your mod needs, `Routers + 1`, `Routers + 5`, and so on, but always base it on `OnLoadOrder.Routers` rather than picking a raw number.

**Overriding an SPT route**, on a URL we already handle, is where the choice matters:

```csharp
[Injectable(TypePriority = OnLoadOrder.Routers - 1)] // you handle it first
[Injectable(TypePriority = OnLoadOrder.Routers + 1)] // SPT handles it first
```

Go below if you want to take the request before SPT sees it, for example to replace the response entirely. Go above if you want SPT to do its work first and then act on the result.

Be aware that two mods overriding the same route are ordering against each other as well as against us, and the one that wins is whoever ended up first.

### Every route action takes a CancellationToken

Route actions gained a `CancellationToken` parameter, sourced from `HttpContext.RequestAborted`. This applies to every router, so all of your actions need the extra parameter whether you use it or not.

```diff
- (url, info, sessionId, output) => { ... }
+ (url, info, sessionId, output, cancellationToken) => { ... }
```

Pass it on to anything that accepts one so a dropped request doesn't leave work running.

`RouteAction<TRequest>` is also constrained to `IRequestData` now, where before it was any `class`.

### Typed route bodies

`RouteAction<TRequest>` and `ItemRouteAction<TRequest>` carry the body type, so the body arrives already typed and you don't cast it yourself.

For item event routers this is new. In 4.0 you were handed a `BaseInteractionRequestData` and wrote `body as MyActionRequest` at the top of every case. Declare the type on the route instead and the cast is gone, along with the separate converter registration that used to be needed to make the deserialisation work at all.

If a body doesn't match the declared type you get an exception naming the route and both types, rather than a null from a failed cast surfacing somewhere later.

## Item event routers

Item event routers were rewritten. If you have one, it needs restructuring.

`ItemEventRouterDefinition` is now `ItemEventRouter`, in `SPTarkov.Server.Core.DI.Routing`. Instead of overriding two methods and switching on the URL, you pass your routes to the base constructor as `ItemRouteAction` records.

**4.0**
```csharp
[Injectable]
public class MyItemEventRouter(MyCallbacks callbacks) : ItemEventRouterDefinition
{
    protected override List<HandledRoute> GetHandledRoutes()
    {
        return [new("MyAction", false)];
    }

    protected override ValueTask<ItemEventRouterResponse> HandleItemEventInternal(
        string url,
        PmcData pmcData,
        BaseInteractionRequestData body,
        MongoId sessionID,
        ItemEventRouterResponse output
    )
    {
        switch (url)
        {
            case "MyAction":
                return new ValueTask<ItemEventRouterResponse>(callbacks.DoThing(pmcData, body as MyActionRequest, sessionID));
            default:
                throw new Exception($"MyItemEventRouter being used when it cant handle route {url}");
        }
    }
}
```

**4.1**
```csharp
[Injectable(TypePriority = OnLoadOrder.Routers)]
public sealed class MyItemEventRouter(MyCallbacks callbacks)
    : ItemEventRouter([
        new ItemRouteAction<MyActionRequest>(
            "MyAction",
            async (url, pmcData, body, sessionID, output, cancellationToken) => await callbacks.DoThing(pmcData, body, sessionID)
        ),
    ]) { }
```

The URL switch, the `GetHandledRoutes` override and the default-case throw all go away. Routes are declared once and dispatched for you.

### BaseInteractionRequestDataConverter is gone

`BaseInteractionRequestDataConverter` has been removed, and with it `RegisterModDataHandler`.

In 4.0 the converter owned a switch over every action, mapping it to the request type to deserialise into. A custom item event meant registering a handler with it separately from writing the router, and forgetting to do so threw at deserialise time complaining the converter didn't handle your action.

```csharp
BaseInteractionRequestDataConverter.RegisterModDataHandler(
    "MyAction",
    json => JsonSerializer.Deserialize<MyActionRequest>(json)
);
```

All of that folded into the router. `ItemRouteAction<MyActionRequest>` already states the type, so the route is the single place your action is declared. Delete the registration call and the handler with it.

## Registering your config into DI

New in 4.1. `IOnDIConstruct` lets a mod add to the service collection before the provider is built.

Use this for your config files. Load your config, register the instance, and every class in your mod can then take it as a constructor parameter through DI injection, the same way SPT's own configs work.

```csharp
public class MyModConfigRegistration : IOnDIConstruct
{
    public static async Task OnDIConstructAsync(IServiceCollection serviceCollection)
    {
        MyModConfig config = await LoadConfigFromDiskAsync();
        serviceCollection.AddSingleton(config);
    }
}
```

Anything in your mod can then take it:

```csharp
[Injectable]
public class MyService(MyModConfig config)
{
    // config is the instance registered above
}
```

`OnDIConstructAsync` is `static abstract` on the interface, so it runs before anything is constructed.

**This is not the way to register your own classes.** Put `[Injectable]` on them and let the container pick them up, as you would have in 4.0. Reach for `IOnDIConstruct` when you have an object the container can't build for itself, which in practice means your config files or anything else that can't be constructed easily with `[Injectable]`.

## Tables and configs are injectable

**`DatabaseServer`, `DatabaseService` and `ConfigServer` no longer exist.** Every database table and every config is registered in DI as a singleton, so you ask for the one you want in your constructor.

**4.0**
```csharp
[Injectable]
public class MyService(DatabaseService databaseService, ConfigServer configServer)
{
    private readonly InsuranceConfig _config = configServer.GetConfig<InsuranceConfig>();

    public void DoThing()
    {
        var globals = databaseService.GetGlobals();
        var items = databaseService.GetItems();
    }
}
```

**4.1**
```csharp
[Injectable]
public class MyService(GlobalTable globalTable, TemplateTable templateTable, InsuranceConfig insuranceConfig)
{
    public void DoThing()
    {
        // globalTable and templateTable are the objects themselves
    }
}
```

Configs are injected by their concrete type. `configServer.GetConfig<InsuranceConfig>()` becomes an `InsuranceConfig` constructor parameter. If the type isn't mapped to a config file, the server fails at startup instead of when your code first runs.

Tables were also renamed to say what they are. Items live on `TemplateTable`, which is what `GetItems()` returned:

| 4.0 | 4.1 |
| --- | --- |
| `databaseService.GetBots()` | `BotTable` |
| `databaseService.GetGlobals()` | `GlobalTable` |
| `databaseService.GetHideout()` | `HideoutTable` |
| `databaseService.GetLocales()` | `LocaleTable` |
| `databaseService.GetLocations()` | `LocationTable` |
| `databaseService.GetMatch()` | `MatchTable` |
| `databaseService.GetItems()` | `TemplateTable` |
| `databaseService.GetTraders()` | `TradersTable` |
| `databaseService.GetServer()` | `ServerTable` |
| `databaseService.GetSettings()` | `SettingsTable` |

All of them are in `SPTarkov.Server.Core.Models.Spt.Tables`.

There is no replacement for `GetTables()`. If you genuinely need several, list them all as parameters.

Because these are singletons, edits you make during `OnLoadAsync` apply server-wide, same as before. Do your database edits at `OnLoadOrder.PostLoad` so the data is loaded by the time you touch it.

## Namespace moves

`Helpers`, `Services` and `Generators` were flat folders with 60+ files each. They're grouped by domain now. This is the change most likely to bury you in `CS0246`, and it's a find-and-replace fix.

The common ones:

| 4.0 | 4.1 |
| --- | --- |
| `Helpers.ItemHelper` | `Helpers.Items.ItemHelper` |
| `Helpers.ProfileHelper` | `Helpers.Profile.ProfileHelper` |
| `Helpers.InventoryHelper` | `Helpers.Profile.InventoryHelper` |
| `Helpers.HideoutHelper` | `Helpers.Profile.HideoutHelper` |
| `Helpers.QuestHelper` | `Helpers.Quest.QuestHelper` |
| `Helpers.TraderHelper` | `Helpers.Traders.TraderHelper` |
| `Helpers.BotHelper` | `Helpers.Bot.BotHelper` |
| `Helpers.ModHelper` | `Helpers.Server.ModHelper` |
| `Services.Mod.CustomItemService` | `Services.Modding.Custom.CustomItemService` |
| `Services.Mod.CustomQuestService` | `Services.Modding.Custom.CustomQuestService` |
| `Services.ServerLocalisationService` | `Services.Locales.ServerLocalisationService` |
| `Models.Eft.Common.Globals` | `Models.Spt.Tables.GlobalTable` |

<details>
<summary>Everything else that moved</summary>

**Generators**
| 4.0 | 4.1 |
| --- | --- |
| `Generators.BotEquipmentModGenerator` | `Generators.Bot.BotEquipmentModGenerator` |
| `Generators.BotGenerator` | `Generators.Bot.BotGenerator` |
| `Generators.BotInventoryGenerator` | `Generators.Bot.BotInventoryGenerator` |
| `Generators.BotLevelGenerator` | `Generators.Bot.BotLevelGenerator` |
| `Generators.BotWeaponGenerator` | `Generators.Bot.BotWeaponGenerator` |
| `Generators.PlayerScavGenerator` | `Generators.Bot.PlayerScavGenerator` |
| `Generators.BotLootGenerator` | `Generators.Loot.BotLootGenerator` |
| `Generators.LocationLootGenerator` | `Generators.Loot.LocationLootGenerator` |
| `Generators.LootGenerator` | `Generators.Loot.LootGenerator` |
| `Generators.PMCLootGenerator` | `Generators.Loot.PMCLootGenerator` |
| `Generators.RagfairAssortGenerator` | `Generators.Ragfair.RagfairAssortGenerator` |
| `Generators.RagfairOfferGenerator` | `Generators.Ragfair.RagfairOfferGenerator` |
| `Generators.RepeatableQuestGeneration.*` | `Generators.RepeatableQuests.*` |
| `Generators.WeaponGen.*` | `Generators.Weapons.*` |
| `Generators.WeatherGenerator` | `Generators.Weather.WeatherGenerator` |
| `Generators.WeatherGen.AbstractWeatherPresetGeneratorBase` | `Generators.Weather.AbstractWeatherPreset` |
| `Generators.WeatherGen.CloudyWeatherGenerator` | `Generators.Weather.CloudyPreset` |
| `Generators.WeatherGen.RainyWeatherGenerator` | `Generators.Weather.RainyPreset` |
| `Generators.WeatherGen.SunnyWeatherGenerator` | `Generators.Weather.SunnyPreset` |

**Helpers**
| 4.0 | 4.1 |
| --- | --- |
| `Helpers.BotDifficultyHelper` | `Helpers.Bot.BotDifficultyHelper` |
| `Helpers.BotGeneratorHelper` | `Helpers.Bot.BotGeneratorHelper` |
| `Helpers.BotWeaponGeneratorHelper` | `Helpers.Bot.BotWeaponGeneratorHelper` |
| `Helpers.DurabilityLimitsHelper` | `Helpers.Bot.DurabilityLimitsHelper` |
| `Helpers.PaymentHelper` | `Helpers.Commerce.PaymentHelper` |
| `Helpers.RewardHelper` | `Helpers.Commerce.RewardHelper` |
| `Helpers.TradeHelper` | `Helpers.Commerce.TradeHelper` |
| `Helpers.CounterTrackerHelper` | `Helpers.InRaid.CounterTrackerHelper` |
| `Helpers.InRaidHelper` | `Helpers.InRaid.InRaidHelper` |
| `Helpers.WeatherHelper` | `Helpers.InRaid.WeatherHelper` |
| `Helpers.PresetHelper` | `Helpers.Items.PresetHelper` |
| `Helpers.DialogueHelper` | `Helpers.Profile.DialogueHelper` |
| `Helpers.HandbookHelper` | `Helpers.Profile.HandbookHelper` |
| `Helpers.HealthHelper` | `Helpers.Profile.HealthHelper` |
| `Helpers.PrestigeHelper` | `Helpers.Profile.PrestigeHelper` |
| `Helpers.ProfileValidatorHelper` | `Helpers.Profile.ProfileValidatorHelper` |
| `Helpers.QuestRewardHelper` | `Helpers.Quest.QuestRewardHelper` |
| `Helpers.RepeatableQuestHelper` | `Helpers.Quest.RepeatableQuestHelper` |
| `Helpers.RagfairHelper` | `Helpers.Ragfair.RagfairHelper` |
| `Helpers.RagfairOfferHelper` | `Helpers.Ragfair.RagfairOfferHelper` |
| `Helpers.RagfairSellHelper` | `Helpers.Ragfair.RagfairSellHelper` |
| `Helpers.RagfairServerHelper` | `Helpers.Ragfair.RagfairServerHelper` |
| `Helpers.RagfairSortHelper` | `Helpers.Ragfair.RagfairSortHelper` |
| `Helpers.RepairHelper` | `Helpers.Ragfair.RepairHelper` |
| `Helpers.HttpServerHelper` | `Helpers.Server.HttpServerHelper` |
| `Helpers.NotificationSendHelper` | `Helpers.Server.NotificationSendHelper` |
| `Helpers.NotifierHelper` | `Helpers.Server.NotifierHelper` |
| `Helpers.AssortHelper` | `Helpers.Traders.AssortHelper` |
| `Helpers.TraderAssortHelper` | `Helpers.Traders.TraderAssortHelper` |

**Services**
| 4.0 | 4.1 |
| --- | --- |
| `Services.BotEquipmentFilterService` | `Services.Bot.BotEquipmentFilterService` |
| `Services.BotEquipmentModPoolService` | `Services.Bot.BotEquipmentModPoolService` |
| `Services.BotInventoryContainerService` | `Services.Bot.BotInventoryContainerService` |
| `Services.BotLootCacheService` | `Services.Bot.BotLootCacheService` |
| `Services.BotNameService` | `Services.Bot.BotNameService` |
| `Services.BotWeaponModLimitService` | `Services.Bot.BotWeaponModLimitService` |
| `Services.MatchBotDetailsCacheService` | `Services.Bot.MatchBotDetailsCacheService` |
| `Services.PmcChatResponseService` | `Services.Bot.PmcChatResponseService` |
| `Services.FenceService` | `Services.Commerce.FenceService` |
| `Services.GiftService` | `Services.Commerce.GiftService` |
| `Services.InsuranceService` | `Services.Commerce.InsuranceService` |
| `Services.MailSendService` | `Services.Commerce.MailSendService` |
| `Services.PaymentService` | `Services.Commerce.PaymentService` |
| `Services.RepairService` | `Services.Commerce.RepairService` |
| `Services.TraderPurchasePersisterService` | `Services.Commerce.TraderPurchasePersisterService` |
| `Services.CircleOfCultistService` | `Services.Hideout.CircleOfCultistService` |
| `Services.MapMarkerService` | `Services.Hideout.MapMarkerService` |
| `Services.AirdropService` | `Services.InRaid.AirdropService` |
| `Services.BtrDeliveryService` | `Services.InRaid.BtrDeliveryService` |
| `Services.CustomLocationWaveService` | `Services.InRaid.CustomLocationWaveService` |
| `Services.LocationLifecycleService` | `Services.InRaid.LocationLifecycleService` |
| `Services.MatchLocationService` | `Services.InRaid.MatchLocationService` |
| `Services.OpenZoneService` | `Services.InRaid.OpenZoneService` |
| `Services.RaidTimeAdjustmentService` | `Services.InRaid.RaidTimeAdjustmentService` |
| `Services.RaidWeatherService` | `Services.InRaid.RaidWeatherService` |
| `Services.ItemBaseClassService` | `Services.Items.ItemBaseClassService` |
| `Services.ItemFilterService` | `Services.Items.ItemFilterService` |
| `Services.LocaleService` | `Services.Locales.LocaleService` |
| `Services.InMemoryCacheService` | `Services.Modding.InMemoryCacheService` |
| `Services.Mod.ModItemCacheService` | `Services.Modding.ModItemCacheService` |
| `Services.BackupService` | `Services.Profile.BackupService` |
| `Services.CreateProfileService` | `Services.Profile.CreateProfileService` |
| `Services.ProfileActivityService` | `Services.Profile.ProfileActivityService` |
| `Services.ProfileFixerService` | `Services.Profile.ProfileFixerService` |
| `Services.ProfileValidatorService` | `Services.Profile.ProfileMigrationService` |
| `Services.RagfairCategoriesService` | `Services.Ragfair.RagfairCategoriesService` |
| `Services.RagfairLinkedItemService` | `Services.Ragfair.RagfairLinkedItemService` |
| `Services.RagfairOfferService` | `Services.Ragfair.RagfairOfferService` |
| `Services.RagfairPriceService` | `Services.Ragfair.RagfairPriceService` |
| `Services.RagfairRequiredItemsService` | `Services.Ragfair.RagfairRequiredItemsService` |
| `Services.RagfairTaxService` | `Services.Ragfair.RagfairTaxService` |
| `Services.NotificationService` | `Services.Server.NotificationService` |
| `Services.PostDbLoadService` | `Services.Server.PostDbLoadService` |
| `Services.ReleaseCheckService` | `Services.Server.ReleaseCheckService` |
| `Services.SeasonalEventService` | `Services.Server.SeasonalEventService` |

**Models**
| 4.0 | 4.1 |
| --- | --- |
| `Models.Eft.Common.Globals` | `Models.Spt.Tables.GlobalTable` |
| `Models.Eft.Common.Tables.Match` | `Models.Spt.Tables.MatchTable` |
| `Models.Spt.Bots.Bots` | `Models.Spt.Tables.BotTable` |
| `Models.Spt.Hideout.Hideout` | `Models.Spt.Tables.HideoutTable` |
| `Models.Spt.Server.LocaleBase` | `Models.Spt.Tables.LocaleTable` |
| `Models.Spt.Server.Locations` | `Models.Spt.Tables.LocationTable` |
| `Models.Spt.Server.ServerBase` | `Models.Spt.Tables.ServerTable` |
| `Models.Spt.Server.SettingsBase` | `Models.Spt.Tables.SettingsTable` |
| `Models.Spt.Templates.Templates` | `Models.Spt.Tables.TemplateTable` |
| `Models.Spt.Config.PmcChatResponse` | `Models.Spt.Config.PmcChatResponseConfig` |

</details>

## Logging

`ISptLogger` lives in `SPTarkov.Common` now, not Core.

```diff
- using SPTarkov.Server.Core.Models.Utils;
+ using SPTarkov.Common.Models.Logging;
```

`LogLevel` is now `Microsoft.Extensions.Logging.LogLevel`. SPT's own copy of the enum is gone. Three of the names differ:

| 4.0 | 4.1 |
| --- | --- |
| `Fatal` | `Critical` |
| `Warn` | `Warning` |
| `Info` | `Information` |

`Trace`, `Debug` and `Error` keep their names. The logger's own methods are unchanged, so `logger.Info(...)` and `logger.Warning(...)` still read the same, this only affects levels you pass to `Log()` or `IsLogEnabled()`.

Be careful if you compared levels numerically. SPT's enum started at `Fatal` and counted up to `Trace`; Microsoft's runs the other way, from `Trace` up to `Critical`.

Colours use Spectre.Console now. `LogWithColor` still takes both a text colour and a background colour, but the `LogTextColor` and `LogBackgroundColor` enums are gone and both parameters are a `Spectre.Console.Color`.

```diff
- void LogWithColor(string data, LogTextColor? textColor = null, LogBackgroundColor? backgroundColor = null, Exception? ex = null);
+ void LogWithColor(string data, Color? textColor = null, Color? backgroundColor = null, Exception? ex = null);
```

So the call itself barely changes, only the type you reach for:

```diff
- logger.LogWithColor("Loaded", LogTextColor.Green, LogBackgroundColor.Black);
+ logger.LogWithColor("Loaded", Color.Green, Color.Black);
```

`Log()` takes the same pair of colour parameters and changed the same way.

## Bundles

`IsBundleMod` is gone. The server checks for `bundles.json` in your mod folder instead. The flag was redundant, and a mod that shipped bundles but forgot to set it just silently didn't load them.

## Patching

Patches are DI managed now. Mark them `[Injectable]`, then inject `IEnumerable<IRuntimePatch>` and enable them.

```csharp
[Injectable]
public class MyPatch : AbstractPatch
{
    protected override MethodBase GetTargetMethod() { ... }

    [PatchPostfix]
    public static void PatchPostfix() { ... }
}
```

Enable them at `Preload`, so they're applied before any of the code you're patching gets a chance to run:

```csharp
[Injectable(TypePriority = OnLoadOrder.Preload + 1)]
public class MyModPatches(IEnumerable<IRuntimePatch> patches) : IOnLoad
{
    public Task OnLoadAsync(CancellationToken cancellationToken)
    {
        foreach (var patch in patches)
        {
            patch.Enable();
        }

        return Task.CompletedTask;
    }
}
```

Always offset from a stage rather than picking a raw number, and use whatever offset your mod needs.

You get every patch in your own assembly from that one injection, so a single loop covers the lot and adding a patch later needs no extra wiring.

`AbstractPatch` implements the new `IRuntimePatch` interface, which is what the container resolves against. In 4.0 you constructed each patch yourself with `new MyPatch().Enable()`. Now you let the container build them and enable what you're handed.

### Getting dependencies into a patch

**`ServiceLocator` has been removed.** In 4.0 it was the only way for a patch to reach the container, because patches were constructed outside DI. It was marked obsolete in 4.0 with this change already planned.

Patches are constructed by the container now, so ask for what you need in the constructor. Harmony patch methods have to be static, so assign the dependency to a static field:

```csharp
[Injectable]
public class MyPatch : AbstractPatch
{
    private static ISptLogger<MyPatch> _logger = default!;
    private static ItemHelper _itemHelper = default!;

    public MyPatch(ISptLogger<MyPatch> logger, ItemHelper itemHelper)
    {
        _logger = logger;
        _itemHelper = itemHelper;
    }

    protected override MethodBase GetTargetMethod() { ... }

    [PatchPostfix]
    public static void PatchPostfix()
    {
        // _logger and _itemHelper are usable here
    }
}
```

Anything the container knows about works here: helpers and services, tables and configs (see [Tables and configs are injectable](#tables-and-configs-are-injectable)), and your own classes registered through `IOnDIConstruct`.

Replace every `ServiceLocator.ServiceProvider.GetService<T>()` call with a constructor parameter. If a type can't be resolved, the server now fails at startup with a clear error rather than handing your patch a null at runtime.

Ownership is enforced, not assumed. `Enable()` and `Disable()` silently do nothing when called from an assembly that didn't create the patch, and `IsYourPatch` tells you whether you own one.

Patch failures now throw `PatchException` naming the target method, instead of a bare `Exception`.

## Web pages

`IModWebMetadata` is now `IModBlazorMetadata`, in `SPTarkov.Server.Web`. Rename the interface and add the three new properties:

```csharp
public sealed class MyModMetadata : IModMetadata, IModBlazorMetadata
{
    // ...
    public string? WWWRootUrl { get; init; }
    public string? HomePage { get; init; } = "/my-mod";
    public string? HomePageDescription { get; init; } = "My mod's config page";
}
```

`HomePage` and `HomePageDescription` register a card for your mod in the SIC mod links section. Mods implementing this interface also no longer have their `.js` and `.ts` files treated as loadable server content.

There's a lot more to this in 4.1, including a config editor that lets users edit your mod's settings in the browser. See [Mod Web Pages](/SPT_41/modding/server/Mod_Web_Pages).

## Prepatching

New in 4.1. Prepatchers extend Core's enums before it loads, which runtime patching can't do.

Most mods don't need this. If yours does, see [Prepatching](/SPT_41/modding/server/Prepatching).

## Smaller changes

- `ModHelper` can read files relative to your own mod folder, so you don't have to work out your install path yourself.
- Custom items can skip handbook and flea price entries.
- `MongoId` was reworked. Existing usage should be unaffected.
