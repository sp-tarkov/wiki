---
title: Mod Types
description: Learn the difference between server mods and client mods.
published: true
date: 2025-08-29T16:52:59.036Z
tags: guide, mods
editor: markdown
dateCreated: 2025-07-22T08:23:52.210Z
---

SPT mods are divided into two categories: server mods, and client mods. Server mods, which are installed in the `user\mods` folder, and client mods, which are installed in the `BepInEx` folder.
> Always read the mod pages of the mods you're installing.
{.is-info}

## Server mods
Server mods interact with the SPT server, which handles everything a live EFT server would: your profiles, traders, quests, items, the flea etc, etc. While less "powerful" than client mods, they still let mod authors create custom traders, quests, weapons and items. They can also tweak things like insurance rates, skill gain or bot spawning.

Server mods are installed in the `user\mods` folder. They are configured either by `config` files, or by a mod-included configuration tool. **Your game and server must be closed** to configure server mods.

They will show up both in your Server console and Launcher.

As of SPT `3.11`, server mods are written in Typescript. `4.0` will have server mods written in C# to match client mods.

## Client mods

Client mods interact directly with the game. They are capable of changing anything in it given enough effort. The most comprehensive mods are usually client mods. They are capable of completely altering bot behaviour, adding new animations and mechanics or adding new elements to the HUD.

Client mods are installed in the `BepInEx\plugins` folder. Few mods also include a `prepatcher` file that goes into the `BepInEx\patchers` folder. The vast majority of client mods are configured from the <kbd>F12</kbd> menu in-game. Some have a dedicated button for opening their configuration menu. Few include config files inside `Bepinex\plugins` for manual editing. Changes made in the F12 menu should apply immediately to your game unless the setting states otherwise.

Client mods will only show up in your F12 menu if they have settings to configure. Some client mods don't, which means there's no good way to check if they are installed and running or not, except to see if they do what they are meant to.

All client mods are written in C#.

## Combination mods
Some mods include both a server and a client component. Some changes are easier to make in one or the other. While you can configure the client-side settings in the <kbd>F12</kbd> menu, they can have separate config files inside their folder in `user\mods`. 

## Making mods
The easiest mods to start with are server mods. With basic knowledge of Typescript, you can open any of the provided [mod examples](https://github.com/sp-tarkov/mod-examples) and make your mod from them.

The best place to get guidance is in our Discord's [`#mod-development`](https://discord.com/channels/875684761291599922/875803116409323562) channel. Note that it's a channel dedicated only to mod developers, not users. Make best effort to describe the issue you have in detail, provide a snippet of the code you're working on, and one of the many knowledgeable modders will be happy to help you.

# See also
[Installing Mods](/Installing_Mods)
[Modding Resources](/Modding_Resources)