---
title: Mod Types
description: Learn the difference between server mods and client mods.
published: true
date: 2025-10-18T08:15:37.678Z
tags: guide, mods
editor: markdown
dateCreated: 2025-07-22T08:23:52.210Z
---

> This page applies to SPT version `4.0`
{.is-info}


SPT mods are divided into two categories: server mods, and client mods. Server mods, which are installed in the `[game folder]\SPT\user\mods` folder, and client mods, which are installed in the `BepInEx` folder.

## Server mods
Server mods interact with the SPT server, which handles everything a live EFT server would: your profiles, traders, quests, items, the flea etc, etc. While less "powerful" than client mods, they still let mod authors create custom traders, quests, weapons and items. They can also tweak things like insurance rates, skill gain or bot spawning.

Server mods are installed in the `[game folder]\SPT\user\mods` folder. They are configured either by `config` files, or by a mod-included configuration tool. **Your game and server must be closed** to configure server mods.

Most server mods can be added to an existing profile. However, **removing some mods might be impossible without making a new profile**. Mods that add new traders, quests, or items fall under that category. Always **read the modpage**, as the author should specify if a mod is unsafe to remove from a profile.

Only server mods will show up in your Server console and Launcher.

Server mods made for SPT `4.0` are written in C#.

## Client mods

Client mods interact directly with the game. They are capable of changing anything in it given enough effort. The most comprehensive mods are usually client mods. They are capable of completely altering bot behaviour, adding new animations and mechanics or adding new elements to the HUD.

Client mods are installed in the `\BepInEx\plugins` folder. Few mods also include a `prepatcher` file that goes into the `\BepInEx\patchers` folder. The vast majority of client mods are configured from the <kbd>F12</kbd> menu in-game. Some have a dedicated button for opening their configuration menu. Few include config files inside `Bepinex\plugins` for manual editing. Changes made in the <kbd>F12</kbd> menu should apply immediately to your game unless the setting states otherwise.

Client mods will only show up in your <kbd>F12</kbd> menu if they have settings to configure. Some client mods don't, which means there's no good way to check if they are installed and running or not, except to see if they do what they are meant to.

Nearly all client mods can be added to an existing profile. Always **read the modpage**, as the author should specify if a mod is unsafe to remove from a profile.

All client mods are written in C#.

## Combination mods
Some mods include both a server and a client component. Some changes are easier to make in one or the other. While you can configure the client-side settings in the <kbd>F12</kbd> menu, they can have separate config files inside their folder in `user\mods`. 

## Making mods
The easiest mods to start with are server mods. With basic knowledge of Typescript, you can open any of the provided [mod examples](https://github.com/sp-tarkov/mod-examples) and make your mod from them.

The best place to get guidance is in our Discord's [`#mod-development`](https://discord.com/channels/875684761291599922/875803116409323562) channel. Note that it's a channel dedicated only to mod developers, not users. Make best effort to describe the issue you have in detail, provide a snippet of the code you're working on, and one of the many knowledgeable modders will be happy to help you.

# See also
[Installing Mods](/Installing_Mods)
[Uninstalling Mods](/Uninstalling_Mods)
[Modding Resources](/Modding_Resources)
[Profiles](/Profiles)