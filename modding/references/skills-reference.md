---
title: Skills Reference Sheet
description: A reference for skill related things
published: true
date: 2025-11-02T03:53:01.081Z
tags: client, reference, server, skills
editor: markdown
dateCreated: 2025-11-02T03:49:55.394Z
---

# Skill Reference Sheet
### Skill Enums
Skills are defined as enum constants. The client uses `ESkillId` while the server uses `SkillTypes`. The integer constants and the naming are the same between them although the type name varies. Not all skills are implemented thus some of these values are unused.

| Enum Name | Constant | Localized Name |
| :--- | :--- | :--- | 
| Endurance | 0 | Endurance
| Strength | 1 | Strength
| Vitality | 2 | Vitality
| Health | 3 | Health
| StressResistance | 4 | Stress Resistance
| Metabloism | 5 | Metabolism
| Immunity | 6 | Immunity
| Perception | 7 | Perception
| Intellect | 8 | Intellect
| Attention | 9 | Attention
| Charisma | 10 | Charisma
| Memory | 11 | Memory
| MagDrills | 12 | Mag Drills
| Pistol | 13 | Pistol
| Revolver | 14 | Revolver
| SMG | 15 | Submachine Guns
| Assault | 16 | Assault Rifles
| Shotgun | 17 | Shotguns
| Sniper | 18 | Bolt-action Rifles
| LMG | 19 | Light Machine Guns
| HMG | 20 | Heavy Machine Guns
| Launcher | 21 | Grenade Launchers
| AttachedLauncher | 22 | Underbarrel Launchers
| Throwing | 23 | Throwables
| Misc | 24 | Misc
| Melee | 25 | Melee
| DMR | 26 | DMRs
| DrawMaster | 27 | Draw Master
| AimMaster | 28 | Aim Master
| RecoilControl | 29 | Recoil Control
| TroubleShooting | 30 | Troubleshooting
| Sniping | 31 | Sniping
| CovertMovement | 32 | Covert Movement
| ProneMovement | 33 | Prone Movement
| FirstAid | 34 | First Aid
| FieldMedicine | 35 | Field Medicine
| Surgery | 36 | Surgery
| LightVests | 37 | Light Vests
| HeavyVests | 38 | Heavy Vests
| WeaponModding | 39 | Weapon Modding
| AdvancedModding | 40 | Advanced Modding
| NightOps | 41 | Night Ops
| SilentOps | 42 | Silent Ops
| Lockpicking | 43 | Lockpicking
| Search | 44 | Search
| WeaponTreatment | 45 | Weapon Maintenance
| Freetrading | 46 | Free Trading
| Auctions | 47 | Auctions
| Cleanoperations | 48 | Clean Operations
| Barter | 49 | Barter
| Shadowconnections | 50 | Shadow Connections
| Taskperformance | 51 | Task Performance
| BearAssaultoperations | 52 | BEAR Assault Operations
| BearAuthority | 53 | BEAR Authority
| BearAksystems | 54 | BEAR AK Systems
| BearHeavycaliber | 55 | BEAR Heavy Caliber
| BearRawpower | 56 | BEAR Raw Power
| UsecArsystems | 57 | NOT LOCALIZED
| UsecDeepweaponmodding | 58 | NOT LOCALIZED
| UsecLongrangeoptics | 59 | NOT LOCALIZED
| UsecNegotiations | 60 | NOT LOCALIZED
| UsecTactics | 61 | NOT LOCALIZED
| BotReload | 62 | NOT LOCALIZED
| BotSound | 63 | NOT LOCALIZED
| AimDrills | 64 | Aim Drills
| HideoutManagement | 65 | Hideout Management
| Crafting | 66 | Crafting
