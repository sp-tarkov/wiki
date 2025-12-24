---
title: Manual Installation Instructions for SPT 3.11
description: 
published: true
date: 2025-12-24T16:31:39.411Z
tags: 
editor: markdown
dateCreated: 2025-10-10T18:56:40.239Z
---

> This page applies to SPT version `3.11`
{.is-info}

## What you need to do before you install Single Player Tarkov
Verify that your Escape From Tarkov is fully up-to-date, through the BSG Launcher.
SPT requires that your EFT is on the latest version. This is so the downpatcher can patch them down to the same EFT client version that SPT 3.11 runs on.

Verify that your Escape From Tarkov works, and that you can load up to at least the main menu or stash.
This is particularly important if you have just installed Escape From Tarkov so all necessary files can be generated.

## Manually installing and running SPT 3.11

1. You will need to download a patcher to downgrade your game files. 
	- Each version of SPT requires a specific version of EFT. `SPT 3.11.4` requires `EFT 16.1.3.35392`. The following downgrade is currently available:
	- [](PATCHER)[1.0.1.0.42625 to 16.1.3.35392](https://spt-legacy.modd.in/Patcher_1.0.1.0.42625_to_16.1.3.35392.7z)
  - If live is newer than the above downgrade patch, **please wait**, a new downgrade patch will be created eventually.
2. Create a new folder for SPT. A good location would be `C:\Games\SPT 3.11`.
3. Copy the content of your live Escape From Tarkov game folder into your `SPT` folder.
	- **DON'T** delete the original EFT installation to save space, it must remain in the original install location for SPT to function.
4. Extract the contents of the downgrade patcher into your `SPT 3.11` folder, and run `patcher.exe`.
	- Make sure to use the tool [7Zip](https://www.7-zip.org/) to do this.
5. Download the [`SPT 3.11.4` release archive](https://github.com/sp-tarkov/build/releases/download/3.11.4/SPT-3.11.4-35392-96e5b73.7z).
6. Extract the contents of the SPT release archive into your `SPT 3.11` folder.
7. Open your `SPT 3.11` folder.
8. Run `SPT.Server`.
 - Wait for the green text that says `Server has started, happy playing`.
9. Run `SPT.Launcher` and follow the onscreen instructions.
 - If you want to copy over your EFT in-game settings, click `OK`. 
 - You can use any username you want. It is recommend that you **do not** use your EFT account username. Especially if you plan on recording or streaming SPT.
 - `Login Automatically` will always log into the last profile you loaded. You can disable this by clicking `Logout` in the bottom right, then unchecking the option.
 - Select your desired game version. Each version has a description box summarising what is included. Once you have picked your chosen game version click `Register`. You can pick *any* game version you want from the profile list, you do not need to own the corresponding EFT version. Once chosen, you cannot change the edition a profile is using.
10. Click `Start Game` and load into the main menu.

Once you have completed the above, you can now play SPT and install mods found on [The Forge](https://forge.sp-tarkov.com/). 
Make sure to download the `3.11` versions of mods. You can see old version of mods in the `Versions` tab on their mod pages.

## Common Installation and Start-up Issues
Below you can find some common issues that users encounter when installing or first starting SPT, along with the solution to fixing it. If your issue is not listed then join our [Discord Server](http://discord.sp-tarkov.com/) and ask in the [`#support-3-11`](https://discord.com/channels/875684761291599922/1172730102119944222) channel.

<details>
<summary>The application had a critical error and failed to run "Watermark" error.</summary>

<img src="/failedshortcuts.png" style="border: 2px solid grey;" alt="Watermark Error">

This happens because you have moved the `SPT.Server` and/or the `SPT.Launcher`, out of your `SPT` folder. 
You will need to move these back into your `SPT` folder and create desktop shortcuts of these. You can do this by right-clicking the executables and then `Send To > Desktop (create shortcut)`.
</details>




