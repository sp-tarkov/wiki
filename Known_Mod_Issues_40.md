---
title: Known Mod Issues
description: Known EFT issues and possible fixes for SPT 4.0.
published: true
date: 2025-11-04T05:34:45.208Z
tags: 
editor: markdown
dateCreated: 2025-10-10T12:36:39.787Z
---

> This page applies to SPT version `4.0`
{.is-info}


## Screen going blank after selecting map
Redownload and reinstall [SVM](https://forge.sp-tarkov.com/mod/236/server-value-modifier-svm).

## BTR Driver chat instantly closes
Update [Fika](https://forge.sp-tarkov.com/mod/2326/project-fika).

## Raid doesn't get saved after extracting/dying
If enabled, turn off `Practice Mode` in [SVM](<https://forge.sp-tarkov.com/mod/236/server-value-modifier-svm>)'s `Raid Settings > Raid startup settings`.


## With [SAIN](<https://forge.sp-tarkov.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement>) bots don't move nor react unless shot at or grenaded 
If you're using the any custom preset from the Forge, try using one of the default presets instead.

## `Error handling request: /client/repeatalbeQuests/activityPeriods`, unable to launch profile
Update [Quest Tweaks](<https://forge.sp-tarkov.com/mod/1537/sgtlaggys-quest-tweaks>), and restore a backup of your profile per the [Backups](<https://wiki.sp-tarkov.com/Profiles#backups>) section.

## ``Error adding locale `ID` to en, duplicate key``
[Update your SPT.](/Updating_SPT)

## `An item with the same key has already been added` when using [Expanded Task Text](<https://forge.sp-tarkov.com/mod/2389/expanded-task-text>) and [Gilded Key Storage](<https://forge.sp-tarkov.com/mod/865/gilded-key-storage>)
Update [Gilded Key Storage](<https://forge.sp-tarkov.com/mod/865/gilded-key-storage>).

## [Task Automation](<https://forge.sp-tarkov.com/mod/2238/task-automation>) stops working
Remove [Expanded Task Text](<https://forge.sp-tarkov.com/mod/2389/expanded-task-text>).

## `ReflectionTypeLoadException` error while [UnityToolkit](<https://forge.sp-tarkov.com/mod/1426/unitytoolkit>) is installed
Delete `[game folder]\BepInEx\patchers\FixPluginTypeSerialization` folder.

## No Hideout crafts when using [Skills Extended](<https://forge.sp-tarkov.com/mod/2383/skills-extended>) and [UI Fixes](<https://forge.sp-tarkov.com/mod/1342/ui-fixes>) when not using English locale
Issue with Skills Extended. Update it. If it's still doing it, and you want to change your locales, open `[game folder]\SPT\SPT_Data\Server\configs\locale.json` in a text editor like Notepad, and change `gameLocale` & `serverLocale` to `en`. Note that this is the only file we recommend manually editing, and only those two values.

## Empty flea with `404 not found` errors
[Update SPT](<https://wiki.sp-tarkov.com/Updating_SPT>).

## `Disable ongoing events` doesn't work in [SVM](<https://forge.sp-tarkov.com/mod/236/server-value-modifier-svm>).
Update [SVM](<https://forge.sp-tarkov.com/mod/236/server-value-modifier-svm>).

## `Critical exception, stopping server... at raidrecord_v0._5.` on SPT 4.0.3
Remove [Raid Record](<https://forge.sp-tarkov.com/mod/2341/raidrecord>).

## SAIN and zombies
[SAIN](<https://forge.sp-tarkov.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement>) is incompatible with zombies. It causes zombies to be unable to melee, and scavs to be stuck in a slide-crouch loop.
Enabling `Vanilla Scavs` in `Home > General > Vanilla Bot Behaviour Settings` will prevent the slide-crouch loop, but will not fix zombies' melee.


# See also
[Frequently Asked Questions](/FAQs_40)