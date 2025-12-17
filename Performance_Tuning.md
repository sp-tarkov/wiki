---
title: Performance Tuning
description: Tips for improving FPS and stability.
published: true
date: 2025-12-17T17:42:52.562Z
tags: guide, performance
editor: markdown
dateCreated: 2025-07-22T03:38:27.428Z
---

> This page applies to any SPT version
{.is-info}

SPT's performance will generally be worse than a live PVP or online PVE raid, where bot AI logic (scavs, PMCs, bosses) is running on BSG servers. SPT runs all of the bot AI logic locally on your PC, which has a significant impact on your performance.

This is due to poor optimisation and a lack of multithreading. 

CPUs with powerful single-threaded performance will improve your in-game FPS the most. AMD's X3D CPUs are optimal for this reason.

## Optimisations
- Use [Waypoints](https://forge.sp-tarkov.com/mod/827/waypoints-expanded-navmesh) to optimise AI pathfinding.
- Use [VRAM Cleaner](https://forge.sp-tarkov.com/mod/2173/vram-cleaner) to free up VRAM usage of your GPU.
- Use [Remove The Dead](https://forge.sp-tarkov.com/mod/1551/remove-the-dead) to clean bodies from the map.
- If using [Dynamic Maps](https://forge.sp-tarkov.com/mod/1431/dynamic-maps) disable the minimap.
- Set vaulting from `Auto` to `Press` in the in-game settings.
- Disable `Nvidia Reflex` in the graphics settings.
- Disable `V-Sync` in the graphics settings.
- Set your texture quality to `Low` or `Medium`.
- Use `Low texture mode for Streets` to further minimise memory usage.
- If you're using Vulkan on Linux or DXVK on Windows, do not use the `Unheard` menu background.
- Remove mods that add new functions to AI.
  - As bots are the main cause of performance issues, mods that add new functions to them will impact performance.
- Use [AI Limit](https://forge.sp-tarkov.com/mod/1945/ai-limit).
  - AI Limit works by disabling distant AIs. This will have an impact on gameplay, but will improve performance.
  - [Questing Bots](https://forge.sp-tarkov.com/mod/1109/questing-bots)^3.11^ already includes an AI limiter.
- Tweak your bot spawning mod to spawn less bots.
  - Less bots mean less demand on your system, but it will make raid feel "less alive" if lowered too much.

## Boot.config
Your `boot.config` file is located in `[game folder]\EscapeFromTarkov_Data`. 
Editing it brings **no performance improvements**.
By default, it contains this:

```
gfx-enable-gfx-jobs=1
gfx-enable-native-gfx-jobs=1
wait-for-native-debugger=0
hdr-display-enabled=0
gc-max-time-slice=3
single-instance=
build-guid=[some ID]
```

That's what it should look like to avoid any issues.

## Pagefile

The pagefile in Windows is used as "storage" for your RAM. If your RAM is filling up, Windows will start moving files to and from it. Even an SSD will be much slower than RAM, hence why it's used sparingly. Windows should automatically increase it as required.

Your pagefile should be set to `Automatically manage paging file size for all drives`. To check if it is:

1. Press <kbd>Win</kbd> and search for "View advanced system settings" and open the link. 
2. Under `Performance`, go into `Settings`, then the `Advanced` tab.
3. Under `Virtual memory` press `Change`.
4. Ensure you have `Automatically manage paging file size for all drives` enabled.

If you experience crashes related to memory, make sure your drives have more than 30GB of free space available.

`RAM Cleaner Fix` at best won't help you with any issues you might have, and at worst will cause your pagefile to be overused, which will instead cause issues. You shouldn't use it.

However, if you still have crashes due to running out of memory even when the pagefile is automatically managed, then there's an underlying issue with your Windows install. You should try to fix it by verifying your Windows files. However, you can manually set your pagefile as a temporary fix:

> Manually setting your pagefile can lead to system crashes if it gets overfilled.
{.is-warning}

1. Follow the above steps to get to the pagefile settings.
2. Disable `Automatically manage paging file size for all drives`.
3. Select your fastest drive and select `Custom size`.
4. Set the `Initial size` and `Maximum size` according to the amount of RAM you have:

| - | - |
| Amount of RAM | Initial size | Maximum size |
| 16 GB | 16000 | 40000 |
| 32 GB | 32000 | 80000 |

> If you encounter system crashes or BSODs after setting your pagefile manually, you should revert those changes by enabling automatic management as described in the beginning of this section.
{.is-info}


## Further tweaks
- You will see minor improvements by changing your graphic settings. Follow any graphics guide for EFT.
- In the case you're severely GPU limited, [CWX's MegaMod](https://forge.sp-tarkov.com/mod/1454/cwx-megamod)'s `GrassCutter` and `EnvironmentEnjoyer` features might help your performance.
- Enabling Nvidia's `Smooth motion` (for 40 and 50 series GPUs), or AMD's `Fluid Motion Frames` for EFT will let your GPU interpolate extra frames, using the unused part of your GPU.
  - If neither are available to you, use [Lossless Scaling](https://store.steampowered.com/app/993090/Lossless_Scaling)'s Frame Generation.
  - Any form of frame generation will result in some increase in latency.
- For further tweaks and discussion, visit the [Optimization Megathread](https://discord.com/channels/875684761291599922/1163777314862149683) in our [Discord server](http://discord.sp-tarkov.com/).

## Headless client

> This is an advanced setup requiring technical knowledge and an understanding of how SPT works.
{.is-warning}

> While Project Fika is a mod available on the Forge, we do not offer support with it installed. If you wish to receive support while you are using Fika, you must seek support from Fika's [Discord server](https://discord.gg/project-fika). 
{.is-warning}

As stated in the introduction, the main performance impact on your game is bots. EFT does not efficiently utilise your system resources, using the same CPU thread to process bots and render your game. When you play an online raid in EFT, all bot processing happens on BSG's servers, letting your CPU "concentrate" on rendering the game. If your game is not processing the bots, SPT's performance becomes much closer to Live EFT. You should then become GPU bottlenecked, so your graphics will become the primary source of your performance.

[Fika](https://forge.sp-tarkov.com/mod/2326/project-fika) allows you to host a raid on a different computer as the one you're playing on. This lets you recreate the conditions of a live EFT raid while still using SPT. To set up a headless client, [follow this guide](https://project-fika.gitbook.io/wiki/advanced-features/headless-client).


It's also possible to use it to the raid on the same computer as the one you're playing on, letting one part of your CPU render the game, while another processes the bots. You could further use a program like Process Lasso to manually delegate your CPU cores if you are an advanced user, but it's not necessary. Please note that **support from Project Fika is limited if you choose to run the headless client on the same PC where you are playing SPT**. This is not the officially supported configuration and may lead to:
- Performance degradation.
- Increased incidence of crashes.
- Significant increase in page file usage.
- General instability that may adversely affect the entire PC or operating system.

# See also
[System Requirements](/system-requirements)