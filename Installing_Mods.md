---
title: Installing Mods
description: General guide on adding mods to your game.
published: true
date: 2025-09-30T23:12:23.166Z
tags: guide, mods
editor: markdown
dateCreated: 2025-06-12T18:59:03.228Z
---

## Before installing your mods

**Read the mod pages** of the mods you want to install. They include information on how to install, configure and **incompatibilities** with other mods.

[The Forge](https://forge.sp-tarkov.com/) is the main source for finding and downloading mods for SPT. We only offer support for mods downloaded from it.

Install [7-Zip](https://www.7-zip.org/) to open and extract mod archives. Other archiving programs, such as WinRAR or Windows itself, are known to corrupt files upon extracting without telling you.

[Notepad++](https://notepad-plus-plus.org/) is another useful tool to have installed. It simplifies editing config files, and will let you know if there's any formatting issues with the edits you made.

Make sure that **you have already loaded SPT up to the main menu** before installing mods.

**Only install mods that are marked compatible with your version of SPT.** Mods for older SPT versions will not work, and will break things. If you are unsure what version of SPT you are on, you can see the SPT version in the top left of the server window or in the bottom left while in-game.

**Close everything SPT related** when installing or removing mods. Your server needs to be closed when configuring [server mods](https://wiki.sp-tarkov.com/en/Mod_Types#server-mods).

## Installing mods

1. Open the mod archive using 7zip.
2. If the mod archive has a `BepInEx` or `user` or *both* folders, drag and drop the contents of the archive to the empty space in your SPT folder.
3. If the mod archive has just a folder or files, read the mod page for install instructions:
- For mods that go into your `user` folder, drag and drop the mod folder into `user\mods`.
- For mods that go into your `BepInEx` or `plugins`, drag and drop the mod folders and files into `BepInEx\plugins` folder.
&nbsp;
<img src="/mod-install-v1.gif" alt="mod install" width=400 style="display: block; margin: 0 auto;">

## Profiles

Nearly all mods can be added to an existing profile. However, **removing some mods might be impossible without making a new profile**. Mods that add new traders, quests, or items fall under that category. Always **read the modpage**, as the author should specify if a mod is unsafe to remove from a profile.

If you removed a mod that broke your profile, SPT can try fixing it. **This is not guaranteed to work**. SPT will do the best it can to remove any item that's in your profile from the removed mod, but some mods make irreversable changes to your profile.

1. Open `SPT_Data\Server\configs\core.json` in a text editor.
2. Set `removeModItemsFromProfile` from `false` to `true`.
3. Set `removeInvalidTradersFromProfile` from `false` to `true`.
4. Save your changes.
5. Launch SPT.

## Load order

You do not need to edit your load order manually unless a mod specifies you to do so. By default, with an empty `order.json` SPT loads mods alphabetically from A to Z. __Mods expect to be loaded in that order.__

Mods that load first get overridden by those loaded later. However, they will only override the values they both alter, not the entire mod.

If you need to edit it, you should use a tool like [Load Order Editor](https://forge.sp-tarkov.com/mod/803/loe-load-order-editor) or [Load Order Editor Drag-Drop](https://forge.sp-tarkov.com/mod/1390/load-order-editor-drag-drop). Your edited load order should still be A to Z, with only few mods moved.

To create a new, empty load order, delete your `user\mods\order.json`. SPT will create a new one the next time you run it.

**Note**: Mods like SVM can override/break any mod loaded before it, so it's recommended to load it first.

## Updating mods

Most mods can be updated by simply reinstalling their files, overriding any files when prompted.

However, some mods move, delete or rename files between versions. While the mod authors should make a note of it, sometimes it's missed.

If you are experiencing issues after updating a mod, or a mod has a large number of individual files, you should delete and reinstall it.

# See also

[Uninstalling Mods](/Uninstalling_Mods)
[Mod Types](/Mod_Types)