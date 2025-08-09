---
title: Installing Mods
description: A beginners guide on how to correctly install mods for SPT.
published: true
date: 2025-08-09T11:48:49.772Z
tags: guide, mods
editor: markdown
dateCreated: 2025-06-12T18:59:03.228Z
---

# Installing Mods
Below is a guide on how to install mods for Single Player Tarkov, as well as common issues which users encounter and how to fix them.

## Before installing your mods
You can find mods for SPT on [The Forge](https://forge.sp-tarkov.com/). The Forge is the main hub of mods for SPT, and is the only place to get mods which are supported in the SPT Discord.

It is **highly recommended** that you download and install [7-Zip](https://www.7-zip.org/) before you proceed to install mods. Other archiving programs such as WinRAR are known to have corrupt files upon extracting without telling you. [7-Zip](https://www.7-zip.org/) has a much lower chance of this happening, as well as informing you should there be an issue.

[Notepad++](https://notepad-plus-plus.org/) is another useful tool to have installed. It simplifies editing config files, and will let you know if there's any formatting issues with the edits you made.

Make sure that **you have already loaded SPT up to the main menu** or stash as outlined in the [Installation Guide](/Installation_Guide).

When selecting the mods you want to install, make sure that you **only install mods that have been updated to your SPT version**. If you are unsure what version of SPT you are on, you can see the SPT version in the top left of the server window or in the bottom left while in-game.

**Read the modpage** of the mods you want to install. The majority of the time the mod page contains important information as to what to expect from the mod, how to install the mod, how to configure the mod and **incompatibilities** with other mods. It is important that you read the modpages as this will help you identify issues you may encounter in game.

**SPT MUST BE FULLY CLOSED BEFORE YOU INSTALL MODS**

## Installing Mods
1. Open the mod archive using 7zip
2. If the mod archive has a `BepInEx` or `user` or *both* folders, drag and drop the contents of the archive to the empty space in your SPT folder
3. If the mod archive has just a folder or files, read the mod page for install instructions
- For mods that go into your `user` folder, drag and drop the mod folder into `user\mods`
- For mods that go into your `BepInEx` or `plugins`, drag and drop the mod folders and files into `BepInEx\plugins` folder 
‎
<img src="/mod-install-v1.gif" alt="mod install" width=400 style="display: block; margin: 0 auto;">

## Profiles
Nearly all mods can be added to an existing profile. However, **removing some mods might be impossible without making a new profile**. Mods that add new traders, quests, or items will require a new profile. Always **read the modpage**, as the author should specify if a mod is unsafe to remove from a profile.

If you removed a mod that broke your profile, you can attempt to fix it by changing `removeModItemsFromProfile` and `removeInvalidTradersFromProfile` to `true` inside `SPT_Data\Server\configs\core.json`. **This is not guaranteed to work**. SPT will do the best it can to remove any item that's in your profile from the removed mod, but some mods make irreversable changes to your profile.

## Load order
You do not need to edit your load order manually unless a mod specifies you to do so. By default, with an empty `order.json` SPT loads mods alphabetically from A to Z. __Mods expect to be loaded in that order.__

Mods that load first get overridden by those loaded later. However, they will only override the values they both alter, not the entire mod.

If you need to edit it, you should use a tool like [Load Order Editor](https://forge.sp-tarkov.com/mod/803/loe-load-order-editor) or [Load Order Editor Drag-Drop](https://forge.sp-tarkov.com/mod/1390/load-order-editor-drag-drop). Your edited load order should still be A to Z, with only few mods moved.

To create a new, empty load order, delete your `user\mods\order.json`. SPT will create a new one the next time you run it.

**Note**: Mods like SVM can override/break any mod loaded before it, so it's recommended to load it first.
# See also
[Mod Types](/Mod_Types)