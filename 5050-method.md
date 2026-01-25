---
title: 50/50 Method
description: How to use the 50/50 Method to find the mod causing your issues.
published: true
date: 2026-01-25T18:29:04.264Z
tags: guide, mods
editor: markdown
dateCreated: 2025-10-05T01:29:38.525Z
---

> This page applies to SPT version `4.0`
{.is-info}


## What is the 50/50 Method.
The 50/50 Method, or a [binary search](https://en.wikipedia.org/wiki/Binary_search), is a method for quickly narrowing down a singular mod that's causing issues. It's a way of quickly checking all your mods if you have a large number installed. It's much faster than individually checking each one, also known as a [linear search](https://en.wikipedia.org/wiki/Linear_search).

If you need to check **50** mods, the 50/50 Method will only take **7** tests, while checking each mod individually could take **50** tests.
If you need to check **100** mods, the 50/50 Method will only take **8** tests, while checking each mod individually could take **100** tests.

## 50/50 Method
First, verify that the issue you have is due to a mod by running SPT without any installed. See the [Uninstalling Mods](/Uninstalling_Mods) page on how to uninstall mods. Note that there's no need to delete your mods, simply move them to a temporary folder, and create a new test profile [so your main profile isn't affected](https://wiki.sp-tarkov.com/Uninstalling_Mods#profiles).
If you have the storage space, you can test if the issue is due to mods by installing a new copy of SPT and seeing if the issue is present without any mods.

1. Copy your `[game folder]/SPT` and `[game folder]/BepInEx` folders to a new folder (e.g.: a new folder called `my mods` on your desktop).
  - This will allow you to restore all your mods, profiles, and settings after you find the issue-causing mod.
2. Make a new test profile.
3. Create a new folder outside of your game folder called `test mods`.
	- It will be helpful to recreate `\SPT\user\mods` and `\BepInEx\plugins` folders inside `test mods`, to avoid accidentally reinstalling a mod in the incorrect location later on.
4. Move half of your installed mods to `test mods`.
  - Some mods have parts in `\SPT\user\mods` and `BepInEx\plugins`. Make sure you move both parts of a mod out of your game folder at the same time.
  - Some mods depend on other mods to function. You can move a mod out of your SPT folder without its dependencies, but don't move a dependency without mods that use it.
  - **Do not move your `\BepInEx\plugins\spt`**. It contains core SPT files and no mod files.
  - Very few mods have files in `\BepInEx\patchers`. If this folder contains only `spt-prepatch.dll`, then you can ignore it. If not, make sure to move the mod files with its other parts.
5. Launch SPT and see if the issue you had is still present.
  - If the issue is still present, the mod at fault is one that's still installed in your SPT.
    - Delete the mod files from `test mods`.
  - If the issue goes away, the mod at fault is one that's inside `test mods`.
	  - Delete your currently installed mods.
    - Reinstall the mods from `test mods` to your SPT.
6. Repeat step 4 and 5 until you're left with a single mod.
7. Move or delete the mod that's causing the issue from your `my mods` folder.
8. Copy the files from `my mods` folder into your SPT folder. This will reinstall all your mods, except the one causing the issue. Override all files when prompted.

After you identified which mod causes your issue, you should report it to the mod author on their [Forge](https://forge.sp-tarkov.com/) mod page.

## Alternative Methods

- While it might be tempting to instead install a new copy of SPT and then install your mods half at a time to it, this new install will not have the same game and mod settings as your main SPT install. If you make every setting match, or manually go through each mod to copy its settings files, you will just end up with a copy of your main SPT install, possibly with small differences you might have missed.
- Instead, if you have the storage space, you can also copy your entire SPT folder elsewhere and perform the 50/50 Method on it instead.
- This method should highlight why it's important to install your mods one at a time or in small batches, as that would let you catch the issue as being one of the mods you recently installed. However, if you didn't install mods gradually, or the issue didn't present itself immediately after installing mods, then the 50/50 Method is your best option.
- If instead you want to find a mod that's incompatible with another, you can also use this method. Leave the mod installed when following the method until you're left with it and the mod that's incompatible. 

# See also
[Installing Mods](/Installing_Mods)
[Uninstalling Mods](/Uninstalling_Mods)