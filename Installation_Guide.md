---
title: Installation Guide
description: A step by step guide on how to install and initially setup Single Player Tarkov.
published: true
date: 2025-09-06T17:49:37.476Z
tags: 
editor: markdown
dateCreated: 2025-06-05T14:00:12.568Z
---

## What you need to do before you install Single Player Tarkov
Verify that your Escape From Tarkov is fully up-to-date, through the BSG Launcher.
SPT requires that your EFT is on the latest version. This is so the downpatcher can copy your EFT files and patch them down to the same EFT client version that SPT runs on.

Verify that your Escape From Tarkov works, and that you can load up to at least the main menu or stash.
This is particularly important if you have just installed Escape From Tarkov so all necessary files can be generated.

## Installing and running Single Player Tarkov
1. Download the [SPT Installer](https://ligma.waffle-lord.net/SPTInstaller.exe).
- The installer will always download & install the latest SPT version, it **does not** update a current SPT install.
2. Run the SPT Installer.
3. Read the Installer Info page, then click next.
- This page contains information as to what the installer does and does not do. It also answers many common questions that users have which is why it is there.
4. Select an install path. 
- **DO NOT** install to a protected location such as Documents or Desktop. An example of a suitable installation folder is to the root directory of a drive such as `C:\SPT` or `C:\Games\SPT`.
5. Click 'Start Install' and wait for it to complete.
- Once complete you will be asked if you want to open the Install Folder or Add a Desktop Shortcuts. Tick or untick to your preference. Select "Add Desktop Shortcuts" if you intend on running SPT from outside of the SPT folder. This will also stop you from encountering the "Watermark" error outlined in the Common Installation and Start-up Issues section below.
6. Navigate to your SPT install and run `SPT.Server`.
- Wait for the green text to say "Happy Playing". This may take several minutes on first startup.
7. Run `SPT.Launcher` and follow the onscreen instructions.
- If you want to copy over your Live Game settings, click OK. 
- You can use any username you want. It is recommend that you **do not** use your Live account username. Especially if you plan on recording or streaming SPT.
- 'Login Automatically' will always log into the last profile you loaded. You can disable this by clicking 'Logout' in the bottom right, then unchecking the option.
- Select your desired game version. Each version has a description box summarising what is included. Once you have picked your chosen game version click 'Register'. You can pick *any* game version you want from the profile list, you do not need to own the corresponding EFT version. Once chosen, you cannot change a the edition a profile is using.
8. Click 'Start Game' and load into the main menu.

Once you have completed the above, you can now play SPT and install mods found on [The Forge](https://forge.sp-tarkov.com/). You can find a guide on how to correctly install SPT mods on the [Installing Mods](https://wiki.sp-tarkov.com/Installing_Mods) Wiki page.

## Common Installation and Start-up Issues
Below you can find some common issues that users encounter when installing or first starting SPT, along with the solution to fixing it. If your issue is not here then feel free to ask for help in the [SPT-Support](https://discord.com/channels/875684761291599922/1172730102119944222) discord channel.

<details>
<summary>Could not find a downgrade patcher for the version of EFT you have installed.</summary>
<br>
<img src="/installernewpatch.png" style="border: 2px solid grey;" alt="Patcher Error">

  There is a new EFT update and either the SPT Development Team needs to update the downpatcher or you have not updated your EFT via the BSG Launcher.

</details>

<details>
<summary>The application had a critical error and failed to run "Watermark" error</summary>
<br>
<img src="/failedshortcuts.png" style="border: 2px solid grey;" alt="Watermark Error">

This happens because you have moved the `SPT.Server` and/or the `SPT.Launcher`, out of your SPT install folder. 
You will need to move these back into your SPT install folder and create desktop shortcuts of these. You can do this by right-clicking the executables and then Send To > Desktop (Shortcut).
</details>

# See also
[System Requirements](/system-requirements)
[Updating SPT](/Updating_SPT)
[Installing Mods](/Installing_Mods)
[Frequently Asked Questions](/FAQs)