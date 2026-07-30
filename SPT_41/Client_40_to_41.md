---
title: Client Mod Migration - 4.0 to 4.1
description: What changed for client mods between SPT 4.0 and 4.1, and how to fix it.
published: true
date: 2026-07-21T00:00:00.000Z
tags: modding, migration, client
editor: markdown
dateCreated: 2026-07-21T00:00:00.000Z
---

> This page applies to SPT version `4.1`
{.is-info}

> Every 4.0 client mod needs rebuilding against 4.1. The game assemblies your mod references have changed, so a 4.0 build will not load.
{.is-warning}

## Everything got its real name back

The 4.0 client was obfuscated. Classes were named `GClass680`, `GStruct80` and so on, with no namespaces, and 4.0 shipped a partial rename layer that turned some of them into flat aliases like `LoggerClass`.

4.1 deobfuscates the client. Types now have real names and live in real namespaces. `GClass680` is `ABotProfileCreator`, `GStruct80` is `AbsolutDecals.DecalMeshVertexData`, and so on.

This is the one change that touches nearly every client mod. Anywhere your code names a game type, whether directly or in a Harmony patch target, that name has changed. The build errors will point you at each one.

The full old-to-new list is on its own page:

- [Client Class Name Mappings](/en/SPT_41/modding/client/Class_Name_Mappings)

Work through the mappings table for each type your mod references and swap the old name for the new one. Because types now sit in namespaces, you will also need the matching `using` for wherever the type ended up.
