---
title: Uninstalling Mods
description: A guide on uninstalling SPT mods.
published: true
date: 2025-10-23T08:52:06.583Z
tags: guide, mods
editor: markdown
dateCreated: 2025-09-25T10:46:32.773Z
---

> This page applies to SPT version `4.0`
{.is-info}

## Uninstalling mods

1. Close your game, launcher and server.
2. **Read the mod page of the mod you're uninstalling**. Some, like Realism, Raid Overhaul or SVM, have extra steps you'll need to do beforehand.
3. Generally, to uninstall a mod, move or delete its files from `[game folder]\SPT\user\mods`, `\BepInEx\plugins` and/or `\BepInEx\patchers`.
  - The easiest way to see what files a mod has is to look inside its archive you downloaded.
  - **Do not remove** your `\BepInEx\plugins\spt` folder and `\BepInEx\patchers\spt-prepatch.dll` file.


## Profiles

Nearly all mods can be added to an existing profile. However, **removing some mods might be impossible without making a new profile**. Mods that add new traders, quests, or items fall under that category. Always **read the modpage**, as the author should specify if a mod is unsafe to remove from a profile.

If you removed a mod that broke your profile, SPT can try fixing it. **This is not guaranteed to work**. SPT will do the best it can to remove any item that's in your profile from the removed mod, but some mods make irreversible changes to your profile.

For instructions, see the [Mods](https://wiki.sp-tarkov.com/Profiles#mods) section on the [Profiles](/profiles) page.

# See also
[50/50 Method](/5050-method)
[Installing Mods](/Installing_Mods)
[Mod Types](/Mod_Types)
[Profile](/Profiles)