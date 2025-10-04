---
title: Bot Difficulties
description: Learn how SPT and mods handle bots' difficulty.
published: true
date: 2025-10-04T22:48:49.687Z
tags: guide
editor: markdown
dateCreated: 2025-08-28T18:04:16.547Z
---


---
## EFT Pre-Raid Difficulty Settings
Specific bots in EFT can have different difficulty settings unique to other bots in the same raid. This page will refer to a bot's specific difficulty as their *difficulty class*.

There are 4 different *difficulty classes* a specific bot can have:
- *Easy*
- *Medium*
- *Hard*
- *Impossible*

The selected difficulty in the **Pre-Raid Setting** determines which *difficulty classes* are allowed to spawn in your raid:
- **As in online**: Mix of *Easy*, *Medium*, and *Hard* classes can spawn.
- **Easy**: Only *Easy* class bots will spawn.
- **Medium**: Only *Medium* class bots will spawn.
- ...and so on

Note that [SVM](https://forge.sp-tarkov.com/mod/236/server-value-modifier-svm) can be used to change which **difficulty** is selected by default in the **Pre-Raid Setting**. Otherwise, it will always default to **As in online**.

## SAIN Presets
Each preset in [SAIN](https://forge.sp-tarkov.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement)'s <kbd>F6</kbd> menu will alter each *difficulty class* individually. This allows you to separately tweak how hard an *Easy* bot is vs. a *Hard* bot, and so on.

Note that this is **not** the same as changing the **difficulty** in the **Pre-Raid Settings**. This will **not** change which *difficulty classes* can spawn in the raid, it will only alter the behaviours of each *difficulty class*.
&nbsp;
<img src="/sain_presets_v2.png" alt="SAIN Presets" width=600 style="display: block; margin: 0 auto;">

## Spawn mods like ABPS and MOAR:
These mods have configuration options to change the likelihood for each *difficulty class* to spawn when **As in online** is chosen in **Pre-Raid Settings**.

Choosing a specific **difficulty** in **Pre-Raid Settings** will instead make all bots the same *difficulty class*.

## What does this mean for me?
Consider changing settings in multiple places if you are unhappy with how difficult your game is:

*Bots are too difficult?*
- Choose an easier **SAIN Preset** (ex. Baby Bots).
- Set the difficulty to **Easy** or **Medium** in **Pre-Raid Settings** so that there won't be a chance for *Hard* bots to spawn in your raid.
- Reduce the likelihood of *Hard* bots to spawn with a **Spawn Mod**.

*Bots are too easy?*
- Choose a harder **SAIN Preset** (ex. Death Wish).
- Set the difficulty to **Hard** or **Impossible** to ensure that there are no *Easy* or *Medium* bots in your raid.