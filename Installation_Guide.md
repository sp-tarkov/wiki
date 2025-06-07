---
title: Installation Guide
description: A step by step guide on how to install and initially setup Single Player Tarkov.
published: true
date: 2025-06-07T18:31:09.075Z
tags: 
editor: markdown
dateCreated: 2025-06-05T14:00:12.568Z
---

# Single Player Tarkov Installation Guide
Below you will find information and a guide on how to correctly install and set-up Single Player Tarkov. Common installation issues and the fixes are at the bottom of the page.


## What you need to do before you install Single Player Tarkov
Verify that your Escape From Tarkov is fully up-to-date, through the BSG Launcher.
SPT requires that your EFT is on the latest version. This is so the downpatcher can copy your EFT files and patch them down to the same EFT client version that SPT runs on.

Verify that your Escape From Tarkov works, and that you can load up to at least the main menu or stash.
This is particularly important if you have just installed Escape From Tarkov so all necessary files can be generated.

## Installing and running Single Player Tarkov
1. Download the [SPT Installer](https://ligma.waffle-lord.net/SPTInstaller.exe). 
- The installer will always download the latest SPT version, it **does not** update a current SPT install.
2. Locate where the SPT Installer was downloaded to and run it.
3. Read the Installer Info page, then click next.
4. Select an install path. 
- **DO NOT** install to a protected location such as Documents or Desktop. Create a folder in the root of a drive and call it SPT. C:\SPT as an example
5. Click 'Start Install' and wait for it to complete.
- Once complete you will be asked if you want to open the Install Folder or Add a Desktop Shortcuts. Tick or untick to your preference. Select 'Add Desktop Shortcuts' if you intend on running SPT from outside of the folder.
6. Navigate to your SPT install and run `SPT.Server`.
- Wait for the green text to say "Happy Playing". This may take several minutes on first startup.
7. Run `SPT.Launcher` and follow the onscreen instructions.
- If you want to copy over your Live Game settings, click OK. 
- You can use any username you want. It is recommend that you **do not** use your Live account username. Especially if you plan on recording or streaming SPT.
- 'Login Automatically' will always log into the first profile you created, or the last profile you loaded. You can disable this by clicking Logout in the bottom right then unchecking the option.
- Select your desired game version, each version has a description box telling you a summary of what is included, then click Register.
8. Push 'Start Game' and load into the main menu and stash.
Once you have completed the above, you can now play SPT and install mods found on [The Forge](https://forge.sp-tarkov.com/).

## Common Installation and Start-up Issues
Below you can find some common issues that users encounter when installing or first starting SPT and how to fix them. If your issue is not here then feel free to ask for help in the [SPT-Support](https://discord.com/channels/875684761291599922/1172730102119944222) discord channel

**Installer Errors**

![installernewpatch.png](/installernewpatch.png)

- There is a new EFT update and either the SPT Development Team needs to update the downpatcher or you have not updated your EFT via the BSG Launcher.

<details>
<summary>The application had a critical error and failed to run "Watermark" error</summary>
<br>

![failedshortcuts.png](/failedshortcuts.png)

This happens because you have moved the `SPT.Server` and/or the `SPT.Launcher`, out of your SPT install folder. 
You will need to move these back into your SPT install folder and create desktop shortcuts of these. You can do this by right-clicking the executables and then Send To > Desktop (Shortcut).
</details>