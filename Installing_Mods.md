---
title: Installing Mods
description: General guide on adding mods to your game.
published: true
date: 2025-10-18T08:03:41.601Z
tags: guide, mods
editor: markdown
dateCreated: 2025-06-12T18:59:03.228Z
---

> This page applies to SPT version `4.0`
{.is-info}


## Before installing your mods

- **Read the mod pages** of the mods you want to install. They include information on how to install, configure and **incompatibilities** with other mods.

- [The Forge](https://forge.sp-tarkov.com/mods) is the main source for finding and downloading mods for SPT. We only offer support for mods downloaded from it.

- Install [7-Zip](https://www.7-zip.org/) to open and extract mod archives. Other archiving programs, such as WinRAR or Windows itself, are known to corrupt files upon extracting without telling you.

- [Notepad++](https://notepad-plus-plus.org/) is another useful tool to have installed. It simplifies editing config files, and will let you know if there's any formatting issues with the edits you made.

- Make sure that **you have already loaded SPT up to the main menu** before installing mods.

- **Only install mods that are marked compatible with your version of SPT.** Mods for older SPT versions will not work, and will break things. If you are unsure what version of SPT you are on, you can see the SPT version in the top left of the server window or in the bottom left while in-game.

- **Close everything SPT related** when installing or removing mods. Your server needs to be closed when configuring [server mods](https://wiki.sp-tarkov.com/en/Mod_Types#server-mods).

## Installing mods

1. Open the mod archive using 7zip.
2. If the mod archive has a `SPT`, `BepInEx` or *both* folders, drag and drop the contents of the archive to the empty space in your SPT folder as seen in the image below.
3. If the mod archive **isn't** structured like that, read the mod page for install instructions:
	- For mods that go into `[game folder]\SPT\user`, drag and drop the mod folder into your `[game folder]\user\mods`.
	- For mods that go into `BepInEx\plugins`, drag and drop the mod folders and files into your `\BepInEx\plugins` folder.

&nbsp;
<img src="/mod-install-v2.gif" alt="mod install" width=600 style="display: block; margin: 0 auto;">

## Profiles

Nearly all mods can be added to an existing profile. However, **removing some mods might be impossible without making a new profile**. Mods that add new traders, quests, or items fall under that category. Always **read the modpage**, as the author should specify if a mod is unsafe to remove from a profile.

If you removed a mod that broke your profile, SPT can try fixing it. **This is not guaranteed to work**. SPT will do the best it can to remove any item that's in your profile from the removed mod, but some mods make irreversible changes to your profile.

1. Open `[game folder]\SPT\SPT_Data\Server\configs\core.json` in a text editor.
2. Set `removeModItemsFromProfile` from `false` to `true`.
3. Set `removeInvalidTradersFromProfile` from `false` to `true`.
4. Save your changes.
5. Launch SPT.

> The above should be viewed as a "last resort" solution. Even a profile "fixed" by this method can exhibit issues like random crashing, bots not spawning, and some maps being unloadable.
{.is-info}

## Updating mods

Most mods can be updated by simply reinstalling their files, overriding any files when prompted.

However, some mods move, delete or rename files between versions. While the mod authors should make a note of it, sometimes it's missed.

If you are experiencing issues after updating a mod, or a mod has a large number of individual files, you should delete and reinstall it.

# See also

[Uninstalling Mods](/Uninstalling_Mods)
[Mod Types](/Mod_Types)
[Profiles](/Profiles)