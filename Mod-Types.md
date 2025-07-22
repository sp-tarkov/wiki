---
title: Understanding mod types
description: Learn the difference between server mods and client mods
published: true
date: 2025-07-22T08:23:52.210Z
tags: mods
editor: markdown
dateCreated: 2025-07-22T08:23:52.210Z
---

# Mod types
SPT mods are divided into two categories: server mods, and client mods. Server mods, which are installed in the `user\mods` folder, and client mods, which are installed in the `BepInEx` folder.
## Server mods
Server mods interact with the SPT server, which handles everything a live EFT server would: your profiles, traders, quests, items, the flea etc, etc. While less "powerful" than client mods, they still let mod authors create custom traders, quests, weapons and items. They can also tweak things like insurance rates, skill gain or bot spawning.
Server mods are installed in the `user\mods` folder. They are configured either by `config` files, or by a mod-included configuration tool.
As of SPT `3.11`, server mods are written in Typescript. `4.0` will have mods be written in C# to match client mods.
## Client mods
Client mods interact directly with the game. They are capable of changing anything in it given enough effort. The most comprehensive mods are usually client mods. They are capable of completely altering bot behaviour, adding new animations and mechanics or adding new elements to the HUD.
Client mods are installed in the `BepInEx\plugins` folder. Few mods also include a `prepatcher` file that goes into the `BepInEx\patchers` folder. The vast majority of client mods are configured from the `F12` menu ingame. Some have a dedicated button for opening their configuration menu. Few include config files inside `Bepinex\plugins` for manual editing.
All client mods are written in C#.
## Combination mods
Some mods include both a server mod and a client mod. Some changes are easier to make in one or the other. While most let you configure the client-side settings in the `F12` menu, they tend to have seperate config files inside their folder in `user\mods`. **Always read the mod page to learn how to configure a mod.**

## Making mods
The easiest mods to start with are server mods. With basic knowledge of Typescript, you can open any of the provided [mod examples](https://github.com/sp-tarkov/mod-examples) and make your mod from them.
The best place to get guidance is in our Discord's `#mod-development` channel. Note that it's a channel dedicated only to mod developers, not users. Make best effort to describe the issue you have in detail, provide a snippet of the code you're working on, and one of the many knowledgable modders will be happy to help you.

Wiki page on mod resources coming soon^tm^.