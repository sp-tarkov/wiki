---
title: Performance Tuning
description: Tips for improving FPS and stability.
published: true
date: 2025-10-12T23:14:53.261Z
tags: guide, performance
editor: markdown
dateCreated: 2025-07-22T03:38:27.428Z
---

## Introduction
Compared to live PVP, the performance in SPT will always be worse. When you're playing PVP, or an online PVE raid, bots (scavs, PMCs, bosses) run on BSG's servers. In SPT, local PVE, and practice raids, bots run on your computer. They are very unoptimised, running on a single CPU thread.

You might have noticed that when playing SPT your CPU and GPU usage is never at 100%. Your GPU cannot run at full power because it's busy waiting on instructions from your CPU, and your CPU cannot run at full power because it has to slowly process all the bots. To see this in action, disable bots in either Pre-Raid Settings, or the bot spawning mod you installed.

Only CPUs with powerful single-threaded performance will improve your in-game FPS. AMD's X3D CPUs are the most optimal as they let a single thread process more data at once.

## Optimisations
- Use [Waypoints](https://forge.sp-tarkov.com/mod/827/waypoints-expanded-navmesh)^3.11^ to optimise AI pathfinding.
- Use [RAM Cleaner Fix](https://forge.sp-tarkov.com/mod/1311/ram-cleaner-fix) to prevent crashes from overfilled memory.
- Use [VRAM Cleaner](https://forge.sp-tarkov.com/mod/2173/vram-cleaner)^3.11^ to free up VRAM usage of your GPU.
- Use [Body Disposal](https://forge.sp-tarkov.com/mod/1159/bdsm-body-disposal-service-maid)^3.11^ to clean bodies from the map.
- Set the vaulting from `Press` to `Auto` in the in-game settings.
- Disable `Nvidia Reflex` in the graphics settings.
- Disable `V-Sync` in the graphics settings.
- Use `Low texture mode for Streets` to further minimise memory usage.
- If you're using [Vulkan](https://en.wikipedia.org/wiki/Vulkan) on Windows, do not use the `Unheard` menu background.
  - It's not an issue on Linux.
- Remove mods that add new functions to AI.
  - As bots are the main cause of performance issues, mods that add new functions to them will impact performance.
- Use [AI Limit](https://forge.sp-tarkov.com/mod/1945/ai-limit)^3.11^.
  - AI Limit works by disabling distant AIs. This will have an impact on gameplay, but will improve performance.
  - [Questing Bots](https://forge.sp-tarkov.com/mod/1109/questing-bots)^3.11^ already includes an AI limiter.
- Tweak your bot spawning mod to spawn less bots.
  - Less bots mean less demand on your system, but it will make raid feel "less alive" if lowered too much.

## Boot.config
Editing your `boot.config` file might marginally help with performance. While no extensive testing has been done on its effectiveness, some report an improvement after tweaking them.

Your `boot.config` file is located in `[game folder]\EscapeFromTarkov_Data` . You can edit it using Notepad or any text editor.
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

First, change `gc-max-time-slice=3` to `gc-max-time-slice=10`. 
Then, add these below:

```
gfx-disable-mt-rendering=1
vr-enabled=0
job-worker-count=[your CPU's number of threads - 1]
```
You can easily check how many threads your CPU has by pressing <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Esc</kbd> to open your Task Manager, and seeing how many `Logical processors` there are in `Performance` > `CPU`.

Finally, in the in-game menu, enable `Only use physical cores` in the `GAME` tab.

## Pagefile
EFT extensively uses your pagefile, which is a cache for programs to use alongside your RAM. It's unlikely you will encounter issues with it being overfilled, which will lead to crashes, if you have at least the recommended amount of RAM per [System Requirements](/system-requirements).

If you're under those requirements, or have a heavily modded game and are experiencing random crashing, manually increasing your pagefile might alleviate them.

To manually increase your pagefile:

1. Press <kbd>Win</kbd> and search for "View advanced system settings" and open the link. 
2. Under `Performance`, go into `Settings`, then the `Advanced` tab.
3. Under `Virtual memory` press `Change`.
4. Select your fastest drive, and set the `Custom size` values to the following:

| Your amount of RAM | Initial Size (MB) | Maximum Size (MB) |
|---|---|---|
| 16 GB | 24000 | 32000 |
| 32 GB | 48000 | 64000 |
| 64 GB | 64000 | 96000 |

5. Press `Set` then `OK`.

> You should still use the [RAM Cleaner Fix](<https://forge.sp-tarkov.com/mod/1311/ram-cleaner-fix>) even with an increased pagefile.
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

> While Project Fika is a mod available on the Forge, we do not offer support with it installed. If you wish to receive support for Fika, you must seek support from Fika's [Discord server](https://discord.gg/project-fika).
{.is-warning}

As stated in the introduction, the main performance impact on your game is bots. EFT does not efficiently utilise your system resources, using the same CPU thread to process bots and render your game. When you play an online raid in EFT, all bot processing happens on BSG's servers, letting your CPU "concentrate" on rendering the game.

[Fika](https://forge.sp-tarkov.com/mod/2326/project-fika) allows you to host a raid on a different computer as the one you're playing on. This lets you recreate the conditions of a live EFT raid while still using SPT. It's also possible to host the raid on the same computer as the one you're playing on, letting one part of your CPU render the game, while another processes the bots.

To set up a headless client, [follow this guide](https://project-fika.gitbook.io/wiki/advanced-features/headless-client).

# See also
[System Requirements](/system-requirements)