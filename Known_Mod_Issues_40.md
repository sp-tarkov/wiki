---
title: Known Mod Issues
description: Known EFT issues and possible fixes for SPT 4.0.
published: true
date: 2026-01-10T12:16:38.838Z
tags: 
editor: markdown
dateCreated: 2025-10-10T12:36:39.787Z
---

> This page applies to SPT version `4.0`
{.is-info}

## Infinite loading after installing mods
This happens most often due to installing mods not made for your version of SPT.
- Outdated [**server**](<https://wiki.sp-tarkov.com/en/Mod_Types#server-mods>) mods will either flag red errors in your SPT server terminal and prevent any mods from being loaded, or not load at all.
- Outdated [**client**](<https://wiki.sp-tarkov.com/en/Mod_Types#client-mods>) mods will **not** throw errors in the SPT server terminal window and **will** allow the game to launch, but then might encounter infinite loading or other issues.

When selecting the mods you want to install, make sure that you **only install mods that have been marked compatible with [your SPT version](<https://wiki.sp-tarkov.com/en/Updating_SPT#version-numbers>)**. Mods for incompatible SPT versions will not work, and will break things. If you are unsure what version of SPT you are on, you can see the SPT version in the top left of the server window or in the bottom left while in-game.

Read the [Uninstalling Mods](<https://wiki.sp-tarkov.com/Uninstalling_Mods>) Wiki page to see how to remove your outdated mods.

If you verified all your mods to be compatible with your version of SPT and you still have infinite loading, then join our [Discord server](http://discord.sp-tarkov.com/) and follow the [`#support-guidelines`](https://discord.com/channels/875684761291599922/1172733248317694022) on opening a new support thread.

## Screen going blank after selecting map
Redownload and reinstall [SVM](https://forge.sp-tarkov.com/mod/236/server-value-modifier-svm).

## BTR Driver chat instantly closes
Update [Fika](https://forge.sp-tarkov.com/mod/2326/project-fika).

## Raid doesn't get saved after extracting/dying
If enabled, turn off `Practice Mode` in [SVM](<https://forge.sp-tarkov.com/mod/236/server-value-modifier-svm>)'s `Raid Settings > Raid startup settings`.
Don't use old presets in newer versions of SVM, and make sure you have the latest version of SVM.

## With [SAIN](<https://forge.sp-tarkov.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement>) bots don't move nor react unless shot at or grenaded 
If you're using the any custom preset from the Forge, try using one of the default presets instead.

## `Error handling request: /client/repeatalbeQuests/activityPeriods`, unable to launch profile
Update [Quest Tweaks](<https://forge.sp-tarkov.com/mod/1537/sgtlaggys-quest-tweaks>), and restore a backup of your profile per the [Backups](<https://wiki.sp-tarkov.com/Profiles#backups>) section.

## ``Error adding locale `ID` to en, duplicate key``
[Update your SPT.](/Updating_SPT)

## `An item with the same key has already been added` when using [Expanded Task Text](<https://forge.sp-tarkov.com/mod/2389/expanded-task-text>) and [Gilded Key Storage](<https://forge.sp-tarkov.com/mod/865/gilded-key-storage>)
Update [Gilded Key Storage](<https://forge.sp-tarkov.com/mod/865/gilded-key-storage>).

## [Task Automation](<https://forge.sp-tarkov.com/mod/2238/task-automation>) stops working
Update it and [Expanded Task Text](<https://forge.sp-tarkov.com/mod/2389/expanded-task-text>).

## `ReflectionTypeLoadException` error while [UnityToolkit](<https://forge.sp-tarkov.com/mod/1426/unitytoolkit>) is installed
Delete `[game folder]\BepInEx\patchers\FixPluginTypeSerialization` folder.

## No Hideout crafts when using [Skills Extended](<https://forge.sp-tarkov.com/mod/2383/skills-extended>) and [UI Fixes](<https://forge.sp-tarkov.com/mod/1342/ui-fixes>) when not using English locale
Update [Skills Extended](<https://forge.sp-tarkov.com/mod/2383/skills-extended>).

## `Disable ongoing events` doesn't work in [SVM](<https://forge.sp-tarkov.com/mod/236/server-value-modifier-svm>).
Update [SVM](<https://forge.sp-tarkov.com/mod/236/server-value-modifier-svm>).

## `Critical exception, stopping server... at raidrecord_v0._5.`
Update [Raid Record](<https://forge.sp-tarkov.com/mod/2341/raidrecord>).

## After dying you're frozen, gun detaches from your hands
Update [MoreBotsAPI](<https://forge.sp-tarkov.com/mod/2426/morebotsapi>).

## Empty Ragman inventory with [Pack 'n' Strap](<https://forge.sp-tarkov.com/mod/1278/wtt-pack-n-strap>) and [Peltor TEP-300 backport](<https://forge.sp-tarkov.com/mod/2420/peltor-tep-300-earplugs-backport-and-fixes>) installed
Update [Pack 'n' Strap](<https://forge.sp-tarkov.com/mod/1278/wtt-pack-n-strap>) and [Peltor TEP-300 backport](<https://forge.sp-tarkov.com/mod/2420/peltor-tep-300-earplugs-backport-and-fixes>).

## `Item "PGU-13/B HEI High Explosive Incendiary" traderPrice is null`
Update [Item Info](<https://forge.sp-tarkov.com/mod/2430/odts-item-info-spt-40>).

## Freezing on raid start
Update [Pack n Strap](<https://forge.sp-tarkov.com/mod/1278/wtt-pack-n-strap>).

## `Shared bot type file ruafRifleman not found...` warning in server console
Harmless warning you can ignore.

## `No locale files found or loaded from... \Badger\Locales`
Harmless warning you can ignore.
## `No C# type for taxonomy node with id... Node name: CustomContainerTemplate`
Install [WTT - CommonLib](<https://forge.sp-tarkov.com/mod/2310/wtt-commonlib>) and [Use Items Anywhere](<https://forge.sp-tarkov.com/mod/2386/use-items-anywhere>).

## Error converting value `#xxxxxx` to type `JsonType.TaxonomyColor`
Install [Color Converter API](<https://forge.sp-tarkov.com/mod/1090/color-converter-api>).

## My flea prices are extreme when using [Live Flea Prices](<https://forge.sp-tarkov.com/mod/1131/live-flea-prices>)
Those are the prices of items on the Live flea right now. You can check the Live flea on websites like <https://tarkov.dev/>.
By default, SPT uses the base handbook price of items +/- some variance when simulating the flea.
To get "normal" flea prices:
- Wait for the Live flea prices to stabilise.
- Set `"pvePrices"` to `true` inside Live Flea Prices' config file to use the PvE Live flea prices instead.
- [Uninstall](<https://wiki.sp-tarkov.com/Uninstalling_Mods>) Live Flea Prices.

## Handbook gun descriptions are broken with `So descriptive`
[Uninstall](<https://wiki.sp-tarkov.com/en/Uninstalling_Mods>) [Preview Sizer](<https://forge.sp-tarkov.com/mod/2339/preview-sizer>).

## You are "invisible" to bots
If installed, tweak [Ombarella](<https://forge.sp-tarkov.com/mod/2315/ombarella>). If you can't tweak it to your liking, [uninstall it](<https://wiki.sp-tarkov.com/Uninstalling_Mods>).

## `The given key '67c5412bb032bbdb530201ba Name' was not present in the dictionary`
[Marlin MXLR](<https://forge.sp-tarkov.com/mod/2484/marlin-mxlr-308-me-lever-action-rifle>) is incompatible with many mods, including [Item Info](<https://forge.sp-tarkov.com/mod/2430/odts-item-info-spt-40>). You will need to either [uninstall it](<https://wiki.sp-tarkov.com/en/Uninstalling_Mods>) or any mod that conflicts with it.

## `Method not found:... ArmorDurability ...` error in server console
Update [APBS](<https://forge.sp-tarkov.com/mod/1594/apbs-acids-progressive-bot-system>).

## Bots aren't hostile while using [SAIN](<https://forge.sp-tarkov.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement>) after uninstalling a custom bot mod
Delete your `[game folder]\BepInEx\plugins\SAIN\Default Bot Config Values` folder. SAIN will regenerate it on game launch.

## Trying to reach Prestige 6 from [Content Backport - Prestiges](<https://forge.sp-tarkov.com/mod/2540/content-backport-prestiges>) shows a blank screen
Update [Content Backport - Prestiges](<https://forge.sp-tarkov.com/mod/2540/content-backport-prestiges>).

## `ObjectId must be a 24-character hex string. (Parameter '..._BOOBS...')` when using the Cultist Circle
Issue with [AES](<https://forge.sp-tarkov.com/mod/874/aes>). As it is a trader mod with quests you cannot remove it without starting a new profile.
Do not use the Cultist Circle until AES has been updated

## `Field not found:... EFT.Profile.Hideout` error message
Uninstall Boss Notifier.

## `The given key '[UNTAR/RUAF/blackdiv]' was not present in the dictionary` error after uninstalling a custom bot mod
You did not fully uninstall said mod. See the [Uninstalling Mods](<https://wiki.sp-tarkov.com/Uninstalling_Mods>) Wiki page how and where you should uninstall your mods.




# See also
[Frequently Asked Questions](/FAQs_40)