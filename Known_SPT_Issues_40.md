---
title: Known SPT Issues
description: Known SPT issues and possible fixes for SPT 4.0.
published: true
date: 2025-10-14T23:55:54.834Z
tags: 
editor: markdown
dateCreated: 2025-10-10T12:33:53.585Z
---

> This page applies to SPT version `4.0.0`
{.is-info}


## [Github tracked issues](https://github.com/sp-tarkov/build/wiki/Known-SPT-issues)
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

## `The server has unexpectidely stopped... : Decoded string is not a valid IDN name.`
Remove any trailing symbols from your Computer's name (e.g.: `My-PC-` > `My-PC`). You can rename your PC by searching for `View your PC name` in the Start menu, and clicking on `Rename this PC`.

## Server doesn't launch or closes immediately
Install **BOTH** of the below. If it tells you that you already have them installed, then use the repair option. Restart your PC after. 
[Runtime 9.0.9](<https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-9.0.9-windows-x64-installer>) 
[ASP.NET 9.0.9](<https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-aspnetcore-9.0.9-windows-x64-installer>)

## Server mods don't appear in the SPT Launcher
A harmless visual bug. They are still loaded in if they were installed correctly. You can confirm this by viewing the server mods in the SPT Server window.
Note that [Client mods](https://wiki.sp-tarkov.com/en/Mod_Types) won't show up in the SPT Server nor Launcher.