---
title: Known SPT Issues
description: Known SPT issues and possible fixes for SPT 4.0.
published: true
date: 2025-12-06T03:24:56.721Z
tags: 
editor: markdown
dateCreated: 2025-10-10T12:33:53.585Z
---

> This page applies to SPT version `4.0.0`
{.is-info}

## [Github tracked issues](<https://github.com/sp-tarkov/build/wiki/Known-SPT-issues>)
- Some quests need PMCs to spawn in map locations with no bot spawns, making them impossible to complete (e.g. kill x PMCs in scav fortress/base).
- Selecting the overview tab as a scav can break your client, <kbd>Alt</kbd> + <kbd>F4</kbd> to revert the raid.
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

## The server has unexpectedly stopped... : Decoded string is not a valid IDN name.
Remove any trailing symbols from your Computer's name (e.g.: `My-PC-` > `My-PC`). 
Your PC name should also not use any special characters. Only `a-z`, `A-Z`, `0-9` and `-` are valid (e.g.: `My-PÇ` > `My-PC`). 
You can rename your PC by searching for `View your PC name` in the Start menu, and clicking on `Rename this PC`.
The 15th character of your PC name can't be a symbol either.

## Server mods don't appear in the SPT Launcher
[Update your SPT.](/Updating_SPT)
Note that [Client mods](/Mod_Types) won't show up in the SPT Server nor Launcher.

## There are little to no PMCs in my Scav runs
[Update your SPT](<https://wiki.sp-tarkov.com/Updating_SPT>), and make sure you don't have an extended raid timer, as EFT's spawning system tends to break with them.

## Empty flea with `404 not found` errors
[Update your SPT](<https://wiki.sp-tarkov.com/Updating_SPT>).

## Server doesn't launch or closes immediately
Install **BOTH** of the below. If it tells you that you already have them installed, then use the repair option. Restart your PC after. 
[.NET Runtime 9.0.11](<https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-desktop-9.0.11-windows-x64-installer>) 
[ASP.NET 9.0.11](<https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-aspnetcore-9.0.11-windows-x64-installer>)

## Kollontay still spawns on high level Ground Zero
[Update your SPT.](<https://wiki.sp-tarkov.com/Updating_SPT>)

## Zombies do not spawn on Shoreline
[Re-update your SPT.](<https://wiki.sp-tarkov.com/Updating_SPT>)

## Zombies do not spawn on Ground Zero
[Update your SPT.](<https://wiki.sp-tarkov.com/Updating_SPT>)

## Crisis does not unlock new crafts
[Update your SPT.](<https://wiki.sp-tarkov.com/Updating_SPT>)

## Infinite loading with no mods after copying live settings
Click `Clear Game Settings` in your SPT Launcher's settings. Don't copy your Live settings if they are from EFT `1.0`.
If that doesn't fix it, join our [Discord Server](http://discord.sp-tarkov.com/) and seek support from the [`#spt-support-4-0`](https://discord.com/channels/875684761291599922/1424142649027199148) channel.

## SPT Launcher doesn't do anything when you click Play

Check your SPT Launcher log file under `SPT/user/logs/launcher.log`, if it contains the following error, you are hitting a bug in SPT 4.0.6:

`Could not find a part of the path '<Steam Path>\libraryfolders.vdf'`

You will need to manually create an empty file at the path given in the error.

If the folder path doesn't exist, you'll need to create it. You can create an empty file by right-clicking in that folder, and selecting New -> Text Document, then renaming it to 
`libraryfolders.vdf`




# See also
[Frequently Asked Questions](/FAQs_40)