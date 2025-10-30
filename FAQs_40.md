---
title: FAQs
description: Answers to frequently asked questions.
published: true
date: 2025-10-30T18:04:25.906Z
tags: 
editor: markdown
dateCreated: 2025-10-10T12:23:08.957Z
---

> This page applies to SPT version `4.0`
{.is-info}

# SPT 4.0
### Why are there so many files in the new `\SPT` folder?
To allow modders to use method patching, all the DLLs need to be 'loose' and not stored inside the server executable.

### Why are `SPT.Launcher` and `SPT.Server` shortcuts?
As part of the restructuring explained above.
The actual exe files are in your `[game folder]\SPT` folder, and the installer creates shortcuts in your `[game folder]` for your convenience.

### Where is my `user` folder?
Also in `[game folder]\SPT`.

### What version of Tarkov is SPT running?
Version `0.16.9.0.40087`, released 2 October 2025.

### Is (insert content here) in SPT now?
Refer to the previous question. If you're curious about something specific, please see the official [Tarkov changelog](<https://escapefromtarkov.fandom.com/wiki/Changelog>).

### Is Labyrinth in `4.0`?
Yes.
<https://escapefromtarkov.fandom.com/wiki/The_Labyrinth>

### Is the Softcore/Hardcore wipe in SPT? 
No. The hardcore wipe only made changes to the PVP mode. SPT `4.0` is using EFT version `0.16.9.0.40087` which came before the softcore wipe changes were added to PVE.
You can easily recreate either using mods.

### Will `4.0` be updated to include the latest EFT patches?
No. EFT patches made after the release of SPT `4.0` will only be available in SPT `4.1`.

### Is performance better in `4.0` than in `3.11`?
Short answer: A bit.
Long answer: BSG optimised culling on several maps, and alongside other changes, did somewhat improve performance between EFT `0.16.1.3.35392` and `0.16.9.0.40087`. It's most noticeable if your SPT is GPU limited and will vary. The [Performance Tuning](/Performance_Tuning) guide is still relevant even on `4.0`.

### Can I use my profile and mods from `3.11`?
***If*** the `3.11` profile was ***un-modded***, yes. Otherwise A new profile will be required. None of your `3.11` mods are compatible.
See the guide on [Updating SPT](/Updating_SPT) for more details.

### I miss `3.11`, can I re-download it?
Yes. `SPT 3.11` is in Long Term Distribution. However, you will need to manually install it and we offer no support for it.
See [this guide](https://github.com/sp-tarkov/build/wiki/3.11-Manual-Installation-Instructions) for instructions.

### When is (insert mod here) going to update to `4.0`?
Nobody knows when certain mods are going to update, not even the authors themselves. Do not pester mod authors about updates to their mods.

### Will a mod marked compatible for `4.0.0` work on future versions of `4.0`?
It should. Mods known to be incompatible with be stated in the `Mod compatibility` section of SPT's [Release page](<https://github.com/sp-tarkov/build/releases/latest>). 
Mods discovered to not work will also be noted in <#1424144572858110052>.
For an explanation of how SPT versions work and how to update your SPT, read through the [Updating SPT](/Updating_SPT) page.

## Halloween Event
The Infected Halloween event is enabled by default in SPT `4.0`. It runs from the 28th of October to the 9th of November. You can see the maps infection level on the pre-raid screen.
SPT uses last year's zombie system, which has several issues:
- Zombies might not spawn on maps even with a high infection level.
- The ceasefire doesn't always apply to bots.
- Some bots might not be hostile to zombies.
- Due to bots having vastly fewer targets, they will tend to stay where they spawned.
- Disabling bosses will also disable zombies. This will be fixed in SPT `4.0.3`.
- [SAIN](<https://forge.sp-tarkov.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement>) is incompatible with zombies. It causes zombies to be unable to melee, and scavs to be stuck in a slide-crouch loop.
  - Enabling `Vanilla Scavs` in `Home > General > Vanilla Bot Behaviour Settings` will prevent the slide-crouch loop, but will not fix zombies' melee.
  - Make sure to not have `Disable ceasefire` enabled in SVM if you decide to disable zombies/Halloween.
- Having [ABPS](<https://forge.sp-tarkov.com/mod/2097/abps-acids-bot-placement-system>) installed will prevent zombies from spawning.

If you want to play with zombies, it's recommended to disable the ceasefire in [SVM](<https://forge.sp-tarkov.com/mod/236/server-value-modifier-svm>) by enabling `Raid Settings > Events > Disable ceasefire`.
If instead you want to disable just zombies, enable `Raid Settings > Events > Disable zombies` in SVM. To disable Halloween completely, enable `Raid Settings > Events > Disable ongoing events`.

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
