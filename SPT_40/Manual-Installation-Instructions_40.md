---
title: Maunal Installation Instructions for SPT 4.0
description: 
published: true
date: 2026-08-06T19:10:05.697Z
tags: 
editor: markdown
dateCreated: 2026-07-31T22:35:05.885Z
---

## What you need to do before you manually install SPT

Verify that your retail game copy works, and that you can load up to at least the main menu or stash.
This is particularly important if you have just installed the game so all necessary files can be generated.

## Manually installing and running SPT

1. Download the patcher from here: [](PATCHER)[1.1.0.0.46657 to 16.9.0.40087](https://spt-patches.modd.in/Patcher_1.1.0.0.46657_to_16.9.0.40087.7z)
	- If your retail game copy is newer than the above downgrade patch, **please wait**, a new downgrade patch will be created eventually.
	- If your retail game copy is older than the above downgrade patch, update your game through the official Launcher or Steam.
2. Create a new folder for SPT. A good location would be `C:\Games\SPT 4.0`.
3. Copy the contents of your live game folder (For Steam, the files inside the `build` folder) into your `C:\Games\SPT 4.0` folder.
	- **DO NOT** delete the original retail game installation to save space, it must remain in the original install location for SPT to function.
4. Extract the patcher you downloaded in step 1 to your `C:\Games\SPT 4.0` folder (requires [7zip](https://www.7-zip.org/)).
5. Run the `patcher.exe` and wait for it to finish.
6. Download the SPT release archive from [here](https://spt-patches.modd.in/SPT-4.0.13-40087-2891fd4.7z).
7. Extract the contents of the SPT release archive into your `C:\Games\SPT 4.0` folder.
8. Open your `C:\Games\SPT 4.0\SPT` folder.
9. Run `SPT.Server`.
 - Wait for the green text that says `Server has started, happy playing`.
10. Run `SPT.Launcher` and follow the onscreen instructions.
 - You can use any username you want. It is recommend that you **do not** use your retail copy account username. Especially if you plan on recording or streaming SPT.
 - `Login Automatically` will always log into the last profile you loaded. You can disable this by clicking `Logout` in the bottom right, then unchecking the option.
 - Select your desired game version. Each version has a description box summarising what is included. Once you have picked your chosen game version click `Register`. You can pick *any* game version you want from the profile list, you do not need to own the corresponding retail game version. Once chosen, you cannot change the edition a profile is using.
11. To make it easier to launch SPT in the future, you can right click `SPT.Server` and `SPT.Launcher`, select `Send to > Desktop (create shortcut)`. These are located in the `[game folder]\SPT` folder and should not be moved out.
12. Click `Start Game` and load into the main menu.

Once you have completed the above, you can now play SPT and install mods found on [The Forge](https://forge.sp-tarkov.com/). You can find a guide on how to correctly install SPT mods on the [Installing Mods](https://wiki.sp-tarkov.com/Installing_Mods) Wiki page. **Make sure to only install versions of mods made for 4.0 and not 4.1.**

## Common Installation and Start-up Issues
Below you can find some common issues that users encounter when installing or first starting SPT, along with the solution to fixing it. If your issue is not listed then join our [Discord Server](http://discord.sp-tarkov.com/) and ask in the [`#spt-support`](https://discord.com/channels/875684761291599922/1172730102119944222) channel.

<details>
<summary>SPT Server crashing instantly or not opening up at all?</summary>
  

From [here](https://dotnet.microsoft.com/en-us/download/dotnet/9.0) download the latest version of **both**:
- `ASP.NET Core Runtime`
- `.NET Desktop Runtime`

If it tells you that you already have them installed, then use the repair option. Restart your PC after.

If that didn't help, verify that your SPT install path doesn't have any special characters (`;,[]{}` etc.).

</details>

<details>
<summary>The application had a critical error and failed to run "Watermark" error.</summary>

<img src="/failedshortcuts.png" style="border: 2px solid grey;" alt="Watermark Error">

This happens because you have moved the `SPT.Server` and/or the `SPT.Launcher`, out of your `[game folder]\SPT` folder. 
You will need to move these back into your `[game folder]\SPT` folder and create desktop shortcuts of these. You can do this by right-clicking the executables and then `Send To > Desktop (create shortcut)`.
</details>

## Old mods and profiles
You cannot use any of your old mod files in a newer SPT version. If you want to use the same mods, you need to download updated versions of them once they have been updated to the latest SPT version.

Some old profiles can work. See the [version numbers](https://wiki.sp-tarkov.com/Updating_SPT#version-numbers) section for more details.



