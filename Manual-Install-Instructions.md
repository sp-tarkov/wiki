---
title: Manual Install Instructions
description: 
published: true
date: 2025-10-30T17:07:53.816Z
tags: 
editor: markdown
dateCreated: 2025-10-21T23:42:29.093Z
---

> This page applies to SPT version `4.0`
{.is-info}

It's always preferable to use the [SPT Installer](/Installation_Guide) instead of manually updating. If you run into issues with it join our [Discord Server](http://discord.sp-tarkov.com/) and ask for support in the [`#spt-support`](https://discord.com/channels/875684761291599922/1172730102119944222) channel.

## What you need to do before you manually install Single Player Tarkov

Verify that your Escape From Tarkov works, and that you can load up to at least the main menu or stash.
This is particularly important if you have just installed Escape From Tarkov so all necessary files can be generated.

## Manually installing and running SPT

1. Create a new folder for SPT. A good location would be `C:\Games\SPT`.
2. Copy the content of your live Escape From Tarkov game folder into your `SPT` folder.
	- **DON'T** delete the original EFT installation to save space, it must remain in the original install location for SPT to function.
3. **If necessary**, download and run a downgrade patcher:
	- If the SPT version you are installing matches live, **DO NOT** run the downgrade patcher. 
	- Each version of SPT needs a specific version of EFT, this version is noted on the [Release page](https://github.com/sp-tarkov/build/releases/latest) of the SPT version.
	- **If necessary**, download the corresponding patcher for your version of EFT from [here](https://spt-mirror.refringe.com/patchers/).
	- Make sure to use the tool [7-Zip](https://www.7-zip.org/) to extract this archive to your `SPT` folder.
	- Run the patcher and wait for it to finish.

4. Download the SPT release archive under the `Direct Download` section of the latest [release page](https://github.com/sp-tarkov/build/releases/latest).
5. Extract the contents of the SPT release archive into your `SPT` folder.
6. Open your `SPT` folder, then the nested `SPT` folder inside of it.
	- To make it easier to launch SPT in the future, you can right click `SPT.Server` and `SPT.Launcher`, select `Send to > Desktop (create shortcut)`
7. Run `SPT.Server`.
 - Wait for the green text that says `Server has started, happy playing`.
8. Run `SPT.Launcher` and follow the onscreen instructions.
 - If you want to copy over your EFT in-game settings, click `OK`. 
 - You can use any username you want. It is recommend that you **do not** use your EFT account username. Especially if you plan on recording or streaming SPT.
 - `Login Automatically` will always log into the last profile you loaded. You can disable this by clicking `Logout` in the bottom right, then unchecking the option.
 - Select your desired game version. Each version has a description box summarising what is included. Once you have picked your chosen game version click `Register`. You can pick *any* game version you want from the profile list, you do not need to own the corresponding EFT version. Once chosen, you cannot change the edition a profile is using.
9. Click `Start Game` and load into the main menu.

Once you have completed the above, you can now play SPT and install mods found on [The Forge](https://forge.sp-tarkov.com/). You can find a guide on how to correctly install SPT mods on the [Installing Mods](https://wiki.sp-tarkov.com/Installing_Mods) Wiki page.

## Common Installation and Start-up Issues
Below you can find some common issues that users encounter when installing or first starting SPT, along with the solution to fixing it. If your issue is not listed then join our [Discord Server](http://discord.sp-tarkov.com/) and ask in the [`#spt-support`](https://discord.com/channels/875684761291599922/1172730102119944222) channel.

<details>
<summary>SPT Server crashing instantly or not opening up at all?</summary>
  
See the solution [here](https://wiki.sp-tarkov.com/Known_SPT_Issues_40#server-doesnt-launch-or-closes-immediately).

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

# See also
[System Requirements](/system-requirements)
[Updating SPT](/Updating_SPT)
[Installing Mods](/Installing_Mods)
[Frequently Asked Questions](/FAQs_40)


