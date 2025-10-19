---
title: Profiles
description: How profiles work in SPT.
published: true
date: 2025-10-19T05:28:27.038Z
tags: guide
editor: markdown
dateCreated: 2025-10-18T07:59:57.279Z
---

## What are profiles?

- In SPT, your profiles are your save files. They store all the information of your in-game character: items, quests, stats, hideout progress, skills etc. It does not contain your in-game or mod settings.

- You can have as many profiles as you want of any edition as you want. There's no restrictions on either, as they are both stored locally on your PC and are only used by SPT. Each profile contains one in-game character.

- You can name your profiles however you want. The name you choose while creating them is only what will be displayed in the SPT Launcher. It will not be your in-game username, as that is set during character creation.

- The SPT Launcher will keep track of all profiles you have. If you want to make or access another profile, simply press `Logout` to go back to the profile selection screen. From there, you can select any profile or make a new one.

## Where are my profiles?

Your profiles are stored in your `[game folder]\SPT\user\profiles` folder. They are in the `.json` format, which is a way of formatting text files. They are named `[profile's ID].json`. You can see which profile is which by opening it in a text editor like Notepad and seeing what `username` it is.

<div style="margin-top: 10px;"></div>
<img src="/profiles/profile top.png" alt="profile" width=400 style="display: block; margin: 0 auto;">
<div style="margin-top: 10px;"></div>
<div style='text-align: center;'>
The first few lines of the profile file.
</div>
<br>

**We do not support manually editing your profiles**. It is extremely easy to mess up and make your profile unusable. Even if you don't make any formatting errors it's extremely easy to edit something that will break your profile. That might manifest long after you made that edit with no way of reverting it.

Your profile file can be copied and moved freely. If you worry about a mod breaking your profile, you can copy and paste it somewhere safe. To go back to that copy, simply copy it back into the `\profiles` folder, overriding the one that's there. Note that SPT must be closed completely while doing so.

## Backups

SPT automatically makes copies of your profiles. They are located in `[game folder]\SPT\user\profiles\backups`. They are in folders named after the date and time they were created on. They also include a `activeMods.json` file, which will display which mods were running when that backup was made.

To restore a backup of a profile:
1. Close your game, launcher and server.
2. Copy your profile from the backup folder you want.
3. Paste it into `[game folder]\SPT\user\profiles`. Override the file when prompted.

## Mods

Nearly all mods can be added to an existing profile. However, **removing some mods might be impossible without making a new profile**. Mods that add new traders, quests, or items fall under that category. Always **read the modpage**, as the author should specify if a mod is unsafe to remove from a profile.

If you removed a mod that broke your profile, SPT can try fixing it. **This is not guaranteed to work**. SPT will do the best it can to remove any item that's in your profile from the removed mod, but some mods make irreversible changes to your profile.

1. Open `[game folder]\SPT\SPT_Data\Server\configs\core.json` in a text editor like Notepad.
2. Set `removeModItemsFromProfile` from `false` to `true`.
3. Set `removeInvalidTradersFromProfile` from `false` to `true`.
4. Save your changes.
5. Launch SPT.

> The above should be viewed as a "last resort" solution. Even a profile "fixed" by this method can exhibit issues like random crashing, bots not spawning, and some maps being unloadable.
{.is-info}
