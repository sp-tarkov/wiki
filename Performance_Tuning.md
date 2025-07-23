---
title: Performance Tuning
description: Tips for improving FPS and stability.
published: true
date: 2025-07-23T14:24:07.643Z
tags: guide, performance
editor: markdown
dateCreated: 2025-07-22T03:38:27.428Z
---

# Performance Tuning

## Introduction
Compared to live PVP, the performance in SPT will always be worse. When you're playing PVP, or an online PVE raid, bots (scavs, PMCs, bosses) run on BSG's servers. In SPT, local PVE, and practice raids, bots run on your computer. They are very unoptimised, running on a single CPU thread.

You might have noticed that when playing SPT your CPU and GPU usage is never at 100%. Your GPU cannot run at full power because it's busy waiting on instructions from your CPU, and your CPU cannot run at full power because it has to slowly process all the bots. To see this in action, disable bots in either Pre-Raid Settings, or the bot spawning mod you installed.

Only CPUs with powerful single-threaded performance will improve your in-game FPS. AMD's X3D CPUs are the most optimal as they let a single thread process more data at once.
## Optimisations
- Use [Waypoints](https://forge.sp-tarkov.com/mod/827/waypoints-expanded-navmesh) to optimise AI pathfinding.
- Use [RAM Cleaner Fix](https://forge.sp-tarkov.com/mod/1311/ram-cleaner-fix) to prevent crashes from overfilled memory.
- Use [VRAM Cleaner](https://forge.sp-tarkov.com/mod/2173/vram-cleaner) to free up VRAM usage of your GPU.
- Set the vaulting from `Press` to `Auto` in the in-game settings.
- Disable `Nvidia Reflex` in the graphics settings.
- Use `Low texture mode for Streets` to further minimise memory usage.
- If you're using [Vulkan](https://en.wikipedia.org/wiki/Vulkan) on Windows, do not use the `Unheard` menu background.
  - It's not an issue on Linux.
- Remove mods that add new functions to AI.
  - As bots are the main cause of performance issues, mods that add new functions to them will impact performance.
- Use [AI Limit](https://forge.sp-tarkov.com/mod/1945/ai-limit).
  - AI Limit works by disabling distant AIs. This will have an impact on gameplay, but will improve performance.
  - [Questing Bots](https://forge.sp-tarkov.com/mod/1109/questing-bots) already includes an AI limiter.
- Tweak your bot spawning mod to spawn less bots.
  - Less bots mean less demand on your system, but it will make raid feel "less alive" if lowered too much.
- Edit your [boot.config](https://hub.sp-tarkov.com/doc/entry/80-fps-boost-boost-framerate-with-command-line-in-boot-config).
## Further tweaks
- You will see minor improvements by changing your graphic settings. Follow any graphics guide for EFT.
- Enabling Nvidia's `Smooth motion` (for 50 series GPUs), or AMD's `Fluid Motion Frames` for EFT will let your GPU interpolate extra frames, using the unused part of your GPU.
  - If neither are available to you, use [Lossless Scaling](https://store.steampowered.com/app/993090/Lossless_Scaling)'s Frame Generation.
  - Any form of frame generation will result in some increase in latency.
- For further tweaks and discussion, visit the [Optimization Megathread](https://discord.com/channels/875684761291599922/1163777314862149683) in our Discord.