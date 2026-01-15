---
title: FAQs
description: Answers to frequently asked questions.
published: true
date: 2026-01-15T19:04:25.705Z
tags: 
editor: markdown
dateCreated: 2025-10-10T12:23:08.957Z
---

> This page applies to SPT version `4.0`
{.is-info}

## Why are there so many files in the new `\SPT` folder?
To allow modders to use method patching, all the DLLs need to be 'loose' and not stored inside the server executable.

## Why are `SPT.Launcher` and `SPT.Server` shortcuts?
As part of the restructuring explained above.
The actual exe files are in your `[game folder]\SPT` folder, and the installer creates shortcuts in your `[game folder]` for your convenience.

## Where is my `user` folder?
Also in `[game folder]\SPT`.

## What version of Tarkov is SPT running?
Version `0.16.9.0.40087`, released 2 October 2025.

## Is (insert content here) in SPT now?
Refer to the previous question. If you're curious about something specific, please see the official [Tarkov changelog](<https://escapefromtarkov.fandom.com/wiki/Changelog>).

## Is Labyrinth in `4.0`?
Yes.
<https://escapefromtarkov.fandom.com/wiki/The_Labyrinth>

## Is the Softcore/Hardcore wipe in SPT? 
No. The hardcore wipe only made changes to the PVP mode. SPT `4.0` is using EFT version `0.16.9.0.40087` which came before the softcore wipe changes were added to PVE.
You can easily recreate either using mods.

## Will `4.0` be updated to include the latest EFT patches?
No. EFT patches made after the release of SPT `4.0` will only be available in SPT `4.1`.

## Is performance better in `4.0` than in `3.11`?
Short answer: A bit.
Long answer: BSG optimised culling on several maps, and alongside other changes, did somewhat improve performance between EFT `0.16.1.3.35392` and `0.16.9.0.40087`. It's most noticeable if your SPT is GPU limited and will vary. The [Performance Tuning](/Performance_Tuning) guide is still relevant even on `4.0`.

## Can I use my profile and mods from `3.11`?
***If*** the `3.11` profile was ***un-modded***, yes. Otherwise A new profile will be required. None of your `3.11` mods are compatible.
See the guide on [Updating SPT](/Updating_SPT) for more details.

## I miss `3.11`, can I re-download it?
Yes. `SPT 3.11` is in Long Term Distribution. However, you will need to manually install it and we offer no support for it.
See [this guide](https://github.com/sp-tarkov/build/wiki/3.11-Manual-Installation-Instructions) for instructions.

## When is (insert mod here) going to update to `4.0`?
Nobody knows when certain mods are going to update, not even the authors themselves. Do not pester mod authors about updates to their mods.

## Will a mod marked compatible for `4.0.0` work on future versions of `4.0`?
Mods made for previous hotfix versions should work on the latest version. Those that don't might have received an update to address that.
Mods known to be incompatible with be stated in the `Mod compatibility` section of SPT's [Release page](<https://github.com/sp-tarkov/build/releases/latest>) and in [Known Mod Issues](/Known_Mod_Issues_40).
For an explanation of how SPT versions work and how to update your SPT, read through the [Updating SPT](<https://wiki.sp-tarkov.com/Updating_SPT>) Wiki page.

## Why do bots spawn right on top of me?
Base SPT uses EFT's PVE spawning system, which does not check the distance to you or other bots. Use a [bot spawning mod](<https://wiki.sp-tarkov.com/Recommended_Mods_40#mods-for-better-bot-spawns>) to address it.

## Need space on your drive? Don't play live?
After you install SPT, you cannot completely uninstall live EFT, but you can delete the `EscapeFromTarkov_Data` folder from your live EFT folder if you really need the space.

You **will** have to validate files through the BSG launcher if you need to reinstall SPT again by going into the BSG Launcher's `Game Settings` and clicking on `Integrity check`.

## RAM Usage
It's [recommended](<https://wiki.sp-tarkov.com/en/system-requirements>) to have at least 32gb of RAM to play SPT without issues.
EFT has over the years become more demanding on system resources. In the past, 16gb was just enough to play without issue. Nowadays it's not.

Some people are still able to play SPT with 16gb of RAM. That's due to the pagefile, which is a cache located on your storage device. If your RAM is filling up, Windows will start moving files to and from it. It will lead to stuttering and overall lower performance, as even the fastest NVMe SSD is much slower than RAM.

For an even smaller subset of people there’s an underlying issue with their Windows install, where the pagefile does not work as intended. While this should be fixed, it can be [set manually as a temporary fix](<https://wiki.sp-tarkov.com/Performance_Tuning#pagefile>).

## Why are bots not moving from their spawn location?
Bots in EFT are not programmed to move from their spawn location outside of combat. Only PMC bots are given tasks to loot areas, if they spawned near them. By design, bots will stand where they spawned until they spot the player. This is a design decision made by BSG and not SPT.

There are currently no mods for SPT `4.0` that make bots move around the map. 

[SAIN](<https://forge.sp-tarkov.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement>) **doesn't** make bots move around the map, as it *only* affects combat behaviour.

# EFT 1.0
### Will we have `1.0` soon in SPT?
There is no active development effort targeting EFT's `1.0` update.
### Is it possible to install SPT with EFT `1.0`?
Yes. You can [install SPT](<https://wiki.sp-tarkov.com/en/Installation_Guide>) while having EFT `1.0` installed.
### Is it possible to install SPT with the Steam copy of EFT?
Yes. See the [install guide](<https://wiki.sp-tarkov.com/en/Installation_Guide>).
### Can I update EFT or will that break my existing SPT install?
That's not how SPT works. The installer makes a **copy** of your EFT files to a **separate** location. Update EFT as much as you want.


# Troubleshooting tips
- Do not install mods until you've launched SPT at least once. Verify your SPT install works, then install mods.
- Do not install out of date mods.
- Do not install multiple mods at once (unless they're dependencies). Install mods one at a time or in small batches. That way when something goes wrong, you'll know exactly what mod is responsible.
- Read mod pages. Not only is it just common courtesy to read the mod page __before__ asking for help, chances are the mod page has exactly the information you need. What the mod does, how to install it, how to use it, and known issues or incompatibility with other mods.

##### "I'm still having issues and it wasn't the last mod I installed, what do I do?" 
Start removing mods one at a time, or if you have a lot of mods, follow the [50/50 Method](<https://wiki.sp-tarkov.com/en/5050-method>).
If none of that helps, then it's time to create a support ticket. Join our [Discord Server](http://discord.sp-tarkov.com/) and read through the [#support-guidelines](https://discord.com/channels/875684761291599922/1172733248317694022) for instructions.

# Old versions of SPT
We currently host two version of SPT: version `4.0`, using EFT version `0.16.9.0.40087`, released `2 October 2025` and a Long Term Distribution version of SPT: version `3.11.4` released `1 September 2025`, using EFT version `0.16.1.3.35392` released `5 March 2025`.

While you can install version `4.0` using the [SPT Installer](<https://forge.sp-tarkov.com/installer>), installing `3.11.4` can only be done manually by following [this guide](/SPT_311/Manual-Installation-Instructions_311). We do not offer support for `3.11.4`.

We do not host older versions of SPT because each SPT version is specifically designed to work with a particular version of EFT. Since EFT is a live service game that receives frequent updates, every SPT version requires a dedicated patcher to downgrade your local EFT installation to the compatible version. Maintaining multiple older SPT versions would necessitate actively maintaining multiple downgrade patchers, which includes updating these patchers after each and every EFT update. Our team simply does not have the time to dedicate to this level of ongoing maintenance.

# Known Issues
- [Known EFT Issues](/Known_EFT_Issues_40)
- [Known SPT Issues](/Known_SPT_Issues_40)
- [Known Mod Issues](/Known_Mod_Issues_40)
