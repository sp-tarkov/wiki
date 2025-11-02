---
title: Known EFT Issues
description:  Known EFT issues and possible fixes for SPT 4.0.
published: true
date: 2025-11-02T22:15:16.062Z
tags: 
editor: markdown
dateCreated: 2025-10-10T12:31:17.069Z
---

> This page applies to SPT version `4.0`
{.is-info}

## [Github tracked issues](<https://github.com/sp-tarkov/build/wiki/Known-non-SPT-issues>)
- BSG have blacklisted a lot of high-level items from the flea. You can disable this blacklist by using a mod.
- Rogues are insanely difficult, their behaviour is the same as live.
- Tagging items in raid with special characters, e.g. `,` or `"` can corrupt the profile on exiting the raid.
- Using horde mode on maps such as Customs will cause large numbers of sniper scavs to spawn together in clumps, avoid using horde mode on all maps except factory.
- `Receive All` shows when nothing can be collected from mail.
- The first time you turn the generator on inside the hideout causes a bug where the client asks for it to be switched off instead of on, clicking the power button on/off again fixes this.
- Completing some quests does not immediately open up another quest. Some quests have multi-hour waits before appearing on a traders quest page.
- Buying an equipment preset that contains a weapon does not purchase the weapon base, only the attachments.
  - Ensure you have `Show only functional items` un-ticked.
- When in a trader buy screen, purchasing an item causes the players inventory filter icons to stop working.
- The Streets and Ground zero navigation mesh has issues, this can cause bots to become stuck and causes the game logging hundreds of bot navigation errors, resulting in very low FPS until raid exit.
- Cancelled offers on flea get stuck until game is restarted.
- It's possible to pick up the hard drive quest item without triggering `Access the office` in the quest `Saving the mole` by entering the room through a route other than the door.
- M4 bb magazines can be found as loot.
- Money must be in pockets or tactical vest to be used for in-raid services.
- New areas in Woods/Labs has reduced loot.
- Many wooden medical crates appear as technical crates.
- Clicking the 'eye' icon multiple times to view inventory while loading into a raid causes the secure container to disappear.
- BSG run a lot of code on a bots death, this causes a lot of stuttering.
- A `Threshold durability should never be negative on an active repair buff` error occurs in client log.
- Searching a container in raid sometimes shows 3 duplicates.
- ZSH helmet + plague mask appear together on bots, BSG have not flagged this combo as incompatible.
- Locales are replaced with long strings of letters and numbers when creating a character.

## Game crashing when the deploy timer hits 0?
Disable any applications that add overlays to EFT such as Blitz.

## Extreme stuttering in-raid, very high RAM usage
If you have `Texture Quality` set to `High` or `Ultra`, try `Medium` or `Low`.

## When inspecting trader items `Compatible with available` is blank
No known fix.

## Transits to Labs or Labyrinth consume two keycards
Only have one of the necessary items in your inventory when transiting to those locations.
Alternatively, install [Gilded Key Storage](<https://forge.sp-tarkov.com/mod/865/gilded-key-storage>).

## Bots phase through doors
BSG's attempt at fixing bots getting stuck on doors. [SAIN](<https://forge.sp-tarkov.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement>) fixes it, however it will make bots get stuck on doors instead.

## Can't click `Select Weapon` in the Build menu
No known fix. To apply builds to a weapon, right click it and press `Edit build`.




# See also
[Frequently Asked Questions](/FAQs_40)