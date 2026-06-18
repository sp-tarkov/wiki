---
title: Bleeding Edge Install Instructions
description: 
published: false
date: 2026-06-18T18:13:14.154Z
tags: 
editor: markdown
dateCreated: 2026-06-18T15:17:35.260Z
---

> This page applies to `BLEEDING EDGE` SPT versions. 
{.is-warning}

## Testing Only

Bleeding Edge installations are for testing only! If you are attempting to install a Bleeding Edge version to play casually, you are going to have a very bad time. Please do yourself a favour and instead use a [stable released version](/en/Installation_Guide). The stable version is happy fun time!

## No Support

This document is the **only support** that you will find for installing the Bleeding Edge version. If you attempt to contact the Single Player Tarkov support team, staff members, moderators, or the general Discord community about installing the Bleeding Edge version, you may end up blocked from downloading Bleeding Edge versions in the future with no warning. And we will laugh at you. We use this version for fast iteration of core development and we do not have the resources to support users on these versions.

## Prerequisites

- A system above the [minimum system requirements](/system-requirements). The live Escape From Tarkov install must remain (80GB) as well as a complete copy (+80GB).
- You must have the latest version of Escape from Tarkov installed using either the Battlestate Games Launcher or Steam.
- You must have started Escape From Tarkov and loaded the main menu.
- You must be willing to submit bugs to the [GitHub issues board](https://github.com/sp-tarkov/server-csharp/issues/new/choose) or to the [#BE-Testing](https://discord.com/channels/875684761291599922/980558564693274694) channel on Discord.

## Software Requirements
- [.Net 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net472-developer-pack-offline-installer)
- [.NET Runtime 9.0](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-desktop-9.0.17-windows-x64-installer)
- [ASP.NET 9.0](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-aspnetcore-9.0.17-windows-x64-installer)
- [.NET Runtime 10.0](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-desktop-10.0.9-windows-x64-installer)
- [ASP.NET 10.0](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-aspnetcore-10.0.9-windows-x64-installer)
- [7-Zip](https://www.7-zip.org/)

## Installation Instructions

These instructions are specific and tedious. **Do no more or no less than what is written.** If for any reason something doesn't work, delete what you have and start over. *Slower.*
{.is-warning}

1. Ensure your Escape from Tarkov is updated to the latest version.
1. Create a new directory for the BE SPT install. A good location would be anywhere that does not require administrative privileges. For example: `C:\Games\SPT-4.1-BE`, or `C:\Users\USERNAME\Games\SPT-4.1-BE`
1. Download the [patcher for SPT 4.0](https://mirror.spt.dev/patchers/). This file you need is based on the current version of Escape from Tarkov, but will look like this `Patcher_1.0.X.X.XXXXX_to_16.9.0.40087.7z`; the newest file that ends in `40087.7z`.
1. Extract the contents of this 7z archive into the root of your `SPT-4.1-BE` directory. Note that the `patcher.exe` and the `SPT_Patches` directory must be in the root of the `SPT-4.1-BE` directory: `SPT-4.1-BE\patcher.exe`.
    ![Install Patcher](https://i.imgur.com/JnZT5ty.gif =600x)
1. Run the `patcher.exe`, and let it finish patching your Escape from Tarkov to version 40087.
1. Download the [patcher for SPT 4.1](https://mirror.spt.dev/patchers/Patcher_16.9.0.40087_to_16.9.5.40743.7z).
1. Extract the contents of this 7z archive into the root of your `SPT-4.1-BE` directory, overwriting any files when prompted.
1. Run the `patcher.exe`, and let it finish patching your Escape from Tarkov to version 40743.
1. Download the Bleeding Edge SPT version from the [#BE-Testing](https://discord.com/channels/875684761291599922/980558564693274694) channel on Discord.
1. Extract the contents of this 7z archive into the root of your `SPT-4.1-BE` directory.

At this point, you should have a fully installed Bleeding Edge version of Single Player Tarkov 4.1 installed on your system.

## Common Questions

Remember, this document is your only avenue of support for Bleeding Edge builds.
<details>
<summary>I was playing the game normally, no mods, fresh profile, and I encountered an error</summary>
We are extremely interested in these types of clean issues. Please submit these types of bugs to the <a href="https://github.com/sp-tarkov/server-csharp/issues/new/choose">GitHub issues board</a> or to the <a href="https://discord.com/channels/875684761291599922/980558564693274694">#BE-Testing</a> channel on Discord. Thank you for helping us build SPT.
</details>

<details>
<summary>Why is there a watermark on my screen? Can I get rid of it?</summary>
If I could reach through my monitor and slap you, I would. No, you can't get rid of it. It's a watermark. We put it there. We want it there. This build is for testing. This is not stable. What are you doing here?
</details>

<details>
<summary>The server doesn't start</summary>
Delete everything and start over. Read slower.
</details>

<details>
<summary>The launcher doesn't start</summary>
Delete everything and start over. Read slower.
</details>

<details>
<summary>The game does not load to the main menu</summary>
Delete everything and start over. Read slower.
</details>

<details>
<summary>My SPT 4.0 profile does not work</summary>
It's not supposed to.
</details>

<details>
<summary>I tried to install a mod and it won't work</summary>
Good.
</details>

Thank you for your help testing and making Single Player Tarkov better for everyone.
&mdash; Developers & Staff