---
title: FAQs
description: Answers to frequently asked questions.
published: true
date: 2025-10-05T22:19:05.664Z
tags: 
editor: markdown
dateCreated: 2025-08-09T12:45:37.740Z
---

# SPT 3.11
### Is performance better on 3.11 than 3.10?
Users in both the live and SPT communities have reported an improvement in performance over version 0.15.5 and a decrease in stutters.

### What version of Tarkov is SPT running?
Version 0.16.1.3.35392, released 5 March 2025.

### Is (insert content here) in SPT now?
Refer to the previous question. If you're curious about something specific, please see the official [Tarkov changelog](<https://escapefromtarkov.fandom.com/wiki/Changelog>).

### Is Labyrinth in SPT?
No. Labyrinth came out after 5 March 2025.

### Will 3.11 be updated to include the latest EFT patches?
No. EFT patches made after the release of SPT v3.11 will only be available in SPT 4.0, which is still in active development.

### Can I use my profile and mods from 3.10?
***If*** the `3.10` profile was ***un-modded***, yes. Otherwise A new profile will be required. None of your `3.10` mods are compatible.
See the guide on [Updating SPT](/Updating_SPT) for more details.

### I miss 3.10, can I re-download it?
No. Support for 3.10 is gone. If you plan on updating to 3.11 just remember that you do not have to delete your old files.

### How do I install 3.11?
Follow the [Installation Guide](/Installation_Guide).

### When is (insert mod here) going to update to 3.11?
Nobody knows when certain mods are going to update, not even the authors themselves. Do not pester mod authors about updates to their mods.

### Bots keep spawning endlessly? How do bot spawns work?
BSG made changes in the way the bot spawn system works which means that bots will continue to spawn in an attempt to keep the raid full for the duration of the raid. 
At raid start, bots will spawn until the max defined value for each map is reached (Approximately 20 bots, though it varies per map). When enough bots have been killed (4), more bots will be spawned in to get the bot count back up to the defined maximum value.

# Troubleshooting tips
- Do not install mods until you've launched SPT at least once. Verify your SPT install works, then install mods.
- Do not install out of date mods.
- Do not install multiple mods at once (unless they're dependencies). Install mods one at a time or in small batches. That way when something goes wrong, you'll know exactly what mod is responsible.
- Read mod pages. Not only is it just common courtesy to read the mod page __before__ asking for help, chances are the mod page has exactly the information you need. What the mod does, how to install it, how to use it, and known issues or incompatibility with other mods.
### "I'm still having issues and it wasn't the last mod I installed, what do I do?" 
Start removing mods one at a time until you find the mod causing the issue. When you've identified the mod responsible, check the mod page to see if it's actually an issue or an intended feature. Check the comments section to see if anyone else reported the same problem you're experiencing. 
If none of that helps, then it's time to create a support ticket. Join our [Discord Server](http://discord.sp-tarkov.com/) and read through the [#support-guidelines](https://discord.com/channels/875684761291599922/1172733248317694022) for instructions.

# Old versions of SPT
We do not host old versions of SPT because each SPT version is specifically designed to work with a particular version of EFT. Since EFT is a live service game that receives frequent updates, every SPT version requires a dedicated patcher to downgrade your local EFT installation to the compatible version. Maintaining multiple older SPT versions would necessitate actively maintaining multiple downgrade patchers, which includes updating these patchers after each and every EFT update. Our team simply does not have the time to dedicate to this level of ongoing maintenance.

This decision is firm and will not be changed by further requests or complaints. Repeatedly asking or arguing about this will unfortunately result in administrative action.

**HOWEVER**, we are pleased to announce that the SPT 3.11 release has been designated as a Long-Term Support (LTS) version. This means it will be maintained and available for download (along with its corresponding downgrade patcher) for an extended period.

# SPT 4.0 Bleeding Edge test build
***It is for testing purposes only***. You will not get any help __installing__ or __using__ it. It is assumed that if you are running the Bleeding Edge built of SPT that you already know what you're doing. No one has time to hold your hand. The watermark is there ***on purpose*** and cannot be removed.

- Do not ask for help installing 4.0 BE
- 3.11 mods will not work on 4.0 BE. You shouldn't even be *trying* to load mods. You're supposed to be finding bugs.
- Do not ask if mod authors will update their mods for 4.0
- Do not attempt to load your 3.11 profile on 4.0 BE and do not expect to keep your profile after 4.0 leaves testing

### How can I contribute to the Bleeding Edge test build?
- Join our [Discord Server](http://discord.sp-tarkov.com/)
- Obtain the BE Tester role in the [Info channel](https://discord.com/channels/875684761291599922/875758493351694396)
- Visit [#dev-build](https://discord.com/channels/875684761291599922/1324955991393177631) for the latest version of BE files
- Visit [#be-testing](https://discord.com/channels/875684761291599922/980558564693274694) for discussion concerning BE
- Report any bugs you find while testing on [Github](<https://github.com/sp-tarkov/server-csharp/issues>)

Users found abusing the Bleeding Edge test program will be __removed__ from the program and could lose access to other channels as well. It's not for playing, it's for __testing__.

# Known mod issues
> Always read the mod pages of the mods you're installing.
{.is-info}
### Spawning in the same spot every raid
Remove the custom player spawn points from [MOAR](https://forge.sp-tarkov.com/mod/789/moar-bagels-ultra-lite-spawn-mod)'s `user\mods\DewardianDev-MOAR\config\spawns\playerspawns.json`. Make each entry look like this:
```json
"bigmap": [],
"factory4_day": [],
...
```
### Partisan spawning right next to you
Also [MOAR](https://forge.sp-tarkov.com/mod/789/moar-bagels-ultra-lite-spawn-mod). Tweak it or disable Partisan.
### Random crashing
If using [Simple Declutter](https://forge.sp-tarkov.com/mod/2139/simple-declutter), disable `Decal Declutter`.
If that didn't help it, remove that mod.
If you're still crashing, join our [Discord Server](http://discord.sp-tarkov.com/) and read through the [#support-guidelines](https://discord.com/channels/875684761291599922/1172733248317694022) for instructions on making a support ticket.
### Bots freeze after death
Update [Quests Extended](https://forge.sp-tarkov.com/mod/2106/quests-extended).
### Glitchy grenades
Update [Borkel's NVGs](https://forge.sp-tarkov.com/mod/954/borkels-realistic-night-vision-goggles-nvgs-and-t-7).
### Weird movement after using a key
Update [Plant Time Modifier](https://forge.sp-tarkov.com/mod/1965/plant-time-modifier-updated-by-crocodilejonesy).
### SAIN is throwing errors about bot brains
Remove any mod marked incompatible on [SAIN](https://forge.sp-tarkov.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement)'s mod page.
### Item cards have some info with `blablabla`
Remove [Volkov Trader](https://forge.sp-tarkov.com/mod/2009/volkov-trader). Follow the instructions for [removing trader mods from a profile](https://wiki.sp-tarkov.com/Installing_Mods#profiles).
If there's no info on the card other than the `blablabla`, join our [Discord Server](http://discord.sp-tarkov.com/) and read through the [#support-guidelines](https://discord.com/channels/875684761291599922/1172733248317694022) for instructions on making a support ticket.
### Random black flickering / flashing in game
This is an issue with [Questing Bots](https://forge.sp-tarkov.com/mod/1109/questing-bots) and AI spawning in. Mod author is aware.
### PMCs missing or grey faces
Set [ALP](https://forge.sp-tarkov.com/mod/1015/alp-algorithmic-level-progression)'s `leveledClothing` to false in `user\mods\AlgorithmicLevelProgression\config\config.json`.
### Audio cuts out
Update [SAIN](https://forge.sp-tarkov.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement). If that doesn't fix it, then it's a binaural audio bug. Recent update force-enabled it for everyone.
### Unable to complete SSL connection
A mod is overloading the SPT server with requests. Mods that display the value of items are the most common cause.
### Error converting value `#xxxxxx` to type `JsonType.TaxonomyColor`
Install [Color Converter API](https://forge.sp-tarkov.com/mod/1090/color-converter-api)
### Could not convert string to double: `Infinity0.1234`
Run your profile through the [Profile Fixer](<https://drakiaxyz.github.io/spt-profile-fix/>)
### All bots converge on me after I fire my gun
If you're using [SAIN](https://forge.sp-tarkov.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement), decrease bots' maximum hearing range and/or aggressiveness.
### Traders are unclickable because they are behind the profile
Install [Kaeno's Trader Scrolling](https://forge.sp-tarkov.com/mod/1089/kaeno-traderscrolling) or enable `Intermediate trader menu` in your game settings.

### Bot brains being destroyed when running Realism, SAIN and Questing Bots
Edit `user\mods\SPT-Realism\db\bots\pmcTypes.json` so the initial section has all instances of `"assault"` changed to `"assaultGroup"`:
```json
    "playerScavBrainType": {
        "factory4_day": {
            "assaultGroup": 1
...
```

### `An attempt was made to transition a task...` error message when using WTT - W.A.A.C.
Having any of the custom voices enabled causes this error. There's no known fix except to not use those custom voices.

# Known EFT issues
> Always read the mod pages of the mods you're installing.
{.is-info}
### Stuck animations? Can't Interact with anything
Bug named *busy hands*. Close SPT or extract from raid as it cannot be fixed mid raid. Use the [HandsAreNotBusy](<https://forge.sp-tarkov.com/mod/1298/handsarenotbusy>) mod to help avoid the bug in the future. Do note that it does not guarantee a fix for all scenarios of the bug. Closing SPT during raid will revert your profile to pre-raid state.

### AI flying or despawning after you kill them?
An issue with BSGs ragdoll physics. [HollywoodFX](<https://forge.sp-tarkov.com/mod/2003/hollywoodfx>) helps alleviate this.

### Missing secure container when you enter raid?
You pushed the `eye` icon in the pre-raid screen too many times. This is a *visual* bug. Restart your SPT. Closing SPT during raid will revert your profile to pre-raid state.

### In-game headset volume is low?
This is as intended by BSG on the current patch that SPT is on. SPT **does not** touch audio.

### Stuck in place on raid start? Unable to move or use weapons?
Restart SPT and unbind the `Compass` from your hotbar. Closing SPT using <kbd>Alt</kbd>+<kbd>F4</kbd> during raid will revert your profile to pre-raid state.

### Icons loading infinitely?
Disable `Mip Streaming` in your in-game settings.

### Hideout turning white?
Disable `Resampling` in your in-game settings, or use [Un-flashbang Hideout](<https://forge.sp-tarkov.com/mod/1425/un-flashbang-hideout>).

### Bots phasing through doors?
There's no known fix. [SAIN](https://forge.sp-tarkov.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement) attempts to fix it, but there have been reports of bots doing it even with it installed.


