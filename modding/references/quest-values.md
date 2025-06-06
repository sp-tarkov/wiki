---
title: Quest Value References
description: A reference page for mod authors who are interested in quest creation or modification.
published: false
date: 2025-06-06T00:41:37.041Z
tags: mods, quests
editor: markdown
dateCreated: 2025-06-05T22:26:29.852Z
---

# Quest Value Reference

This page contains various values used during quest creation or modification. Please utilize the quick links to jump between various areas.

Updated as of 3.11

## Navigation

-	[General Information](/modding/references/quest-values#general-information)
{.links-list}
	- [Trader IDs](/modding/references/quest-values#trader-ids)
  	- [Location Details](/modding/references/quest-values#location-details)
    - [Quest Types](/modding/references/quest-values#quest-types)
    - [Properties](/modding/references/quest-values#properties)
  	- [Structure](/modding/references/quest-values#quest-structure)
-	[Available For Finish Conditions](/modding/references/quest-values#available-for-finish-conditions)
	- [Handover Item](/modding/references/quest-values#handover-item)
	- [Find Item](/modding/references/quest-values#find-item)
	- [Skill Requirement](/modding/references/quest-values#skill-requirement)
	- [Leave Item](/modding/references//quest-values#leave-item)
	- [Place Beacon](/modding/references//quest-values#place-beacon)
	- [Visit Place](/modding/references//quest-values#visit-place)
	- [Weapon Assembly](/modding/references//quest-values#weapon-assembly)
	- [Kills](/modding/references//quest-values#kills)
	- [Exit Status](/modding/references//quest-values#exit-status)
- [Available For Start Requirements](/modding/references/quest-values#available-for-start-requirements)
- [Fail Conditions](/modding/references/quest-values#fail-conditions)
- [Rewards](/modding/references/quest-values#rewards)
	- [Experience](/modding/references/quest-values#experience)
	- [Item](/modding/references/quest-values#item)
	- [Trader Standing](/modding/references/quest-values#trader-standing)
	- [Skill](/modding/references/quest-values#skill)
	- [Stash Rows](/modding/references/quest-values#stash-rows)
	- [Achievement](/modding/references/quest-values#achievement)

---
## General Information
Below you will find all general information related to quests, including vanilla trader IDs, location information and IDs, quest types, and properties. You will also find an example quest pulled directly from BSG.

### Trader IDs
Trader IDs are used in quest conditions, standing rewards, and quest properties for what trader issues the quest.

>
> Please ensure that you are using a **_valid MongoID_** if you are creating a custom trader, **_the custom trader will not load if it is an invalid MongoID._**
>

| Friendly Name | ID |
| :--- | :---: |
| Prapor | 54cb50c76803fa8b248b4571 |
| Therapist | 54cb57776803fa99248b456e |
| Fence | 579dc571d53a0658a154fbec |
| Skier | 58330581ace78e27b8b10cee |
| Peacekeeper | 5935c25fb3acc3127c3d8cd9 |
| Mechanic | 5a7c2eca46aef81a7ca2145d |
| Ragman | 5ac3b934156ae10c4430e83c |
| Jaeger | 5c0647fdd443bc2504c2d371 |
| Ref (Arena) | 6617beeaa9cfa777ca915b7c |

### Location Details
Location details are used in various locations in quests. There is a ID for the location as well as a coded string for each location. They are used in specific spots in the quest structure.
>
> Friendly Names are not used in code.
> IDs are used for the "location" property on quests.
> Target Names are used when a condition requires a location. **These are case sensitive.**
>
| Friendly Name | ID | Target Name |
| :--- | :--- | :--- |
| Factory (Day) | 55f2d3fd4bdc2d5f408b4567 | factory4_day |
| Factory (Night) | 59fc81d786f774390775787e | factory4_night |
| Customs | 56f40101d2720b2a4d8b45d6 | bigmap |
| Woods | 5704e3c2d2720bac5b8b4567 | Woods |
| Lighthouse | 5704e4dad2720bb55b8b4567 | Lighthouse |
| Shoreline | 5704e554d2720bac5b8b456e | Shoreline |
| Reserve | 5704e5fad2720bc05b8b4567 | RezervBase |
| Interchange | 5714dbc024597771384a510d | Interchange |
| Laboratory | 5b0fc42d86f7744a585f9105 | laboratory |
| Streets Of Tarkov | 5714dc692459777137212e12 | TarkovStreets |
| Ground Zero (Level <= 20) | 653e6760052c01c1c805532f | Sandbox |
| Ground Zero (Level > 20) | 653e6760052c01c1c805532f | Sandbox_high |
| Any Map | any | N/A |

### Quest Types
Quest types are required and will display specific ways on the players Task List as well as in the trader Tasks page.
>
> All quests must have a type.
> Quest types will display the name and BSG Icon on the task list on the players client.
> The type does not have to match the conditions of the quest, but it is encouraged to match it for player clarity.
>
| Type | Description |
| :--- | :--- |
| Prapor | 54cb50c76803fa8b248b4571 |
| Therapist | 54cb57776803fa99248b456e |
| Fence | 579dc571d53a0658a154fbec |
| Skier | 58330581ace78e27b8b10cee |
| Peacekeeper | 5935c25fb3acc3127c3d8cd9 |
| Mechanic | 5a7c2eca46aef81a7ca2145d |
| Ragman | 5ac3b934156ae10c4430e83c |
| Jaeger | 5c0647fdd443bc2504c2d371 |
| Ref | 6617beeaa9cfa777ca915b7c |
### Properties

The below table is a list of all currently known properties for quests. While not all properties are *required* for use, it is best to have every single property whether or not you are utilizing it.

| Property Name | Required? | Example Value | Type |
| :--- | :--- | :--- | :--- |
| QuestName | Yes | "Building Our First Quest!" | string |
| _id | Yes | "68423056128053531e5a5bf6" | MongoID string |
| acceptPlayerMessage | No | "68423056128053531e5a5bf6 acceptPlayerMessage" | string |
| acceptanceAndFinishingSource | No | "eft" | string |
| arenaLocations | No | [] | array |
| canShowNotificationsInGame | Yes | true | boolean |
| changeQuestMessageText | No | "68423056128053531e5a5bf6 changeQuestMessageText" | string |
| completePlayerMessage | No | "68423056128053531e5a5bf6 completePlayerMessage" | string |
| conditions | Yes | | object ([AvailableForFinish](/modding/references/quest-values#available-for-finish-conditions)/[AvailableForStart](/modding/references/quest-values#available-for-start-requirements)/[Fail](/modding/references/quest-values#fail-conditions))|
| declinePlayerMessage | No | "68423056128053531e5a5bf6 declinePlayerMessage" | string |
| description | No | "68423056128053531e5a5bf6 description" | string |
| failMessageText | No | "68423056128053531e5a5bf6 failMessageText" | string |
| gameModes | No | [] | array |
| image | No | "/files/quest/icon/quest_icon.png" | string |
| instantComplete | No | false | boolean |
| isKey | No | false | boolean |
| location | Yes | "5704e4dad2720bb55b8b4567" | string ([Location Details Table](/modding/references/quest-values#location-details)) |
| name | Yes | "68423056128053531e5a5bf6 name" | string |
| note | No | "68423056128053531e5a5bf6 note" | string |
| progressSource | No | "eft" | string |
| rankingModes | No | [] | array |
| restartable | Yes | false | boolean |
| rewards | No |  | object ([Rewards](/modding/references/quest-values#rewards)) |
| secretQuest | No | false | boolean |
| side | Yes | "Pmc" | string |
| startedMessageText | No | "68423056128053531e5a5bf6 name" | string |
| successMessageText | No | "68423056128053531e5a5bf6 name" | string |
| traderId | Yes | "lol" | string ([Trader ID Table](/modding/references/quest-values#trader-ids)) |
| type | Yes | "Skill" | string ([Quest Type Table](/modding/references/quest-values#location-details)) |

### Quest Structure

Blah Blah

[Return To Top](#quick-links)
## Available For Finish Conditions
### Handover Item

Blah blah

### Find Item

Blah blah

### Skill Requirement

blah blah

### Leave Item

Blah blah

### Place Beacon

Blah blah

### Visit Place

Blah blah

### Weapon Assembly

Blah blah

### Kills

Blah blah

### Exit Status

Blah blah

[Return To Top](#quick-links)
## Available For Start Requirements

[Return To Top](#quick-links)
## Fail Conditions

[Return To Top](#quick-links)
## Rewards
### Experience
### Item
### Trader Standing
### Skill
### Stash Rows
### Achievement

[Return To Top](#quick-links)