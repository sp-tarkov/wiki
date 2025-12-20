---
title: Installation Guide
description: A step by step guide on how to install and initially setup Single Player Tarkov.
published: true
date: 2025-12-20T03:41:04.264Z
tags: 
editor: markdown
dateCreated: 2025-06-05T14:00:12.568Z
---

> This page applies to SPT version `4.0`
{.is-info}


## What you need to do before you install Single Player Tarkov
Verify that your Escape From Tarkov is fully up-to-date, through the BSG Launcher or Steam.
SPT requires that your EFT is on the latest version. This is so the downpatcher can copy your EFT files and patch them down to the same EFT client version that SPT runs on.

Verify that your Escape From Tarkov works, and that you can load up to at least the main menu or stash.
This is particularly important if you have just installed Escape From Tarkov so all necessary files can be generated.

## Installing and running Single Player Tarkov

1. Download the [SPT Installer](https://forge.sp-tarkov.com/installer).
 - The installer will always download & install the latest SPT version, it **does not** update a current SPT install.
2. Run the SPT Installer.
3. Read the Installer Info page, then click next.
 - This page contains information as to what the installer does and does not do. It also answers many common questions that users have which is why it is there.
4. Select an install path. 
 - **DO NOT** install to a protected location such as Documents or Desktop as you might encounter Windows permission issues. **DO NOT** install into your Live EFT folder. A good location would be `C:\Games\SPT`.
5. Click 'Start Install' and wait for it to complete.
 - Once complete you will be asked if you want to open the Install Folder or Add a Desktop Shortcuts. Tick or untick to your preference.
  - If you decide against the shortcuts, you can run the `SPT.Server` and `SPT.Launcher` from inside your SPT folder. They are shortcuts which you can copy to any location on your computer.
6. Run `SPT.Server`.
 - Wait for the green text that says `Server has started, happy playing`.
 - Your server needs to be running while you play. It can just be closed when you are done playing.
7. Run `SPT.Launcher` and follow the onscreen instructions.
 - If you want to copy over your EFT in-game settings, click `OK`. 
 - You can use any username you want. It is recommend that you **do not** use your EFT account username. Especially if you plan on recording or streaming SPT.
 - `Login Automatically` will always log into the last profile you loaded. You can disable this by clicking `Logout` in the bottom right, then unchecking the option.
 - Select your desired game version. Each version has a description box summarising what is included. Once you have picked your chosen game version click `Register`. You can pick *any* game version you want from the profile list, you do not need to own the corresponding EFT version. Once chosen, you cannot change the edition a profile is using.
8. Click `Start Game` and load into the main menu.

Once you have completed the above, you can now play SPT and install mods found on [The Forge](https://forge.sp-tarkov.com/). You can find a guide on how to correctly install SPT mods on the [Installing Mods](https://wiki.sp-tarkov.com/Installing_Mods) Wiki page.

## Common Installation and Start-up Issues
Below you can find some common issues that users encounter when installing or first starting SPT, along with the solution to fixing it. If your issue is not listed then join our [Discord Server](http://discord.sp-tarkov.com/) and ask in the [`#spt-support`](https://discord.com/channels/875684761291599922/1172730102119944222) channel.

<details>
<summary>Could not find a downgrade patcher for the version of EFT you have installed.</summary>

<img src="/installernewpatch.png" style="border: 2px solid grey;" alt="Patcher Error">

  There is a new EFT update and either the SPT Development Team needs to update the downpatcher or you have not updated your EFT via the BSG Launcher.

</details>

<details>
<summary>SPT Server crashing instantly or not opening up at all?</summary>
  
See the solution [here](https://wiki.sp-tarkov.com/Known_SPT_Issues_40#server-doesnt-launch-or-closes-immediately).

</details>


<details>
<summary>The application had a critical error and failed to run "Watermark" error.</summary>

<img src="/failedshortcuts.png" style="border: 2px solid grey;" alt="Watermark Error">

This happens because you have moved the `SPT.Server` and/or the `SPT.Launcher`, out of your `[game folder]\SPT` folder. 
You will need to move these back into your `[game folder]\SPT` folder and create desktop shortcuts of these. You can do this by right-clicking the executables and then Send To > Desktop (Shortcut). The shortcuts to the two are made by the installer automatically, which you can find in the root folder of your SPT install.
</details>

## Old mods and profiles
You cannot use any of your old mod files in a newer SPT version. If you want to use the same mods, you need to download updated versions of them once they have been updated to the latest SPT version.

Some old profiles can work. See the [version numbers](https://wiki.sp-tarkov.com/Updating_SPT#version-numbers) section for more details.

# See also
[System Requirements](/system-requirements)
[Updating SPT](/Updating_SPT)
[Installing Mods](/Installing_Mods)
[Frequently Asked Questions](/FAQs_40)