---
title: Known SPT Issues
description: Known SPT issues and possible fixes for SPT 4.0.
published: true
date: 2025-10-18T09:05:17.881Z
tags: 
editor: markdown
dateCreated: 2025-10-10T12:33:53.585Z
---

> This page applies to SPT version `4.0.0`
{.is-info}

## [Github tracked issues](<https://github.com/sp-tarkov/build/wiki/Known-SPT-issues>)
- Some quests need PMCs to spawn in map locations with no bot spawns, making them impossible to complete (e.g. kill x PMCs in scav fortress/base).
- Selecting the overview tab as a scav can break your client, alt+f4 to revert the raid.
- Your active flea offers are marked as expired when the server is offline and items are returned in the mail.
- Flea categories don't always show the correct number of offers when filtering by item.
- The server will not load when placed in a folder path containing certain unicode characters (Japanese and Korean characters especially).
- Looting a PMC dogtag doesn't always show their name on the post-raid kill screen.
- Insured quest items that are consumed in a quest can be returned to the player.
- Failed quests that're restarted retain their task completion status until client is restarted (e.g. `Bullshit` - Shooting a scav after collecting the flash drive results in that task remaining completed).
- Using a low hp medpack while extracting can result in a 0 resource item being left in your inventory.
- Lightkeeper does not give rewards in-game, they are sent by mail.
- The bitcoin counter in hideout is slightly desynced to your game client, your game will say a bitcoin is ready to collect but the server is ~5 minutes behind.
- Replacing a daily/weekly quest with another from the same trader will cause a client soft lock, restarting the client fixes the issue.

## Fixed in `4.0.1`
See the Wiki page for [Updating SPT](/Updating_SPT).
- Removed Tagilla from PMC brain pool - caused them to stand still forever
- Updated Customs `bossKnight` spawn chance from 0 to 18%
- Flea will now show `Unlock at level x` instead of offer creators name in while item is tier locked
- Blacklisted unlootable `PMC Origins figurine` from PMCs
- Blacklisted `Corpse room key` and `Rusted bloody key` from rewards
- Fixed Launcher not showing installed mods
- Fixed PMCs not spawning on PMC raid when player disables bosses in pre-raid screen
- Fixed PMCs not always spawning in scav raids
- Fixed inspecting a `required for upgrade` item in hideout causing server error
- Fixed index out of range on probability object array error
- Fixed issue where profiles can become corrupted when server is stopped while saving data
- Fixed `PointsEarnedDuringSession` overflow error on raid end caused by players setting XP gain to absurdly high values in SVM
- Fixed `Commando` bot inheriting all chat commands from other chat bots
- Fixed tiered flea issue. A low level profile can lock items for all other profiles until server restart
- Fixed PMC stats not being persisted during prestige
- Fixed bundles not loading correctly
- Fixed profile migration system error affecting USEC profiles

## `The server has unexpectidely stopped... : Decoded string is not a valid IDN name.`
Remove any trailing symbols from your Computer's name (e.g.: `My-PC-` > `My-PC`). You can rename your PC by searching for `View your PC name` in the Start menu, and clicking on `Rename this PC`.

## Server mods don't appear in the SPT Launcher
[Update your SPT.](/Updating_SPT)
Note that [Client mods](/Mod_Types) won't show up in the SPT Server nor Launcher.

## There are little to no PMCs in my Scav runs
[Update your SPT.](/Updating_SPT)

## Server doesn't launch or closes immediately
Install **BOTH** of the below. If it tells you that you already have them installed, then use the repair option. Restart your PC after. 
[.NET Runtime 9.0.10](<https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-desktop-9.0.10-windows-x64-installer>) 
[ASP.NET 9.0.10](<https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-aspnetcore-9.0.10-windows-x64-installer>)

## Kollontay still spawns on high level Ground Zero
Use a mod like [SVM](<https://forge.sp-tarkov.com/mod/236/server-value-modifier-svm>) to remove their spawn.