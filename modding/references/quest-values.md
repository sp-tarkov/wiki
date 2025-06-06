---
title: Quest Value References
description: A reference page for mod authors who are interested in quest creation or modification.
published: true
date: 2025-06-06T06:00:43.245Z
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
	- [Useful Links](/modding/references/quest-values#useful-links)
	- [Trader IDs](/modding/references/quest-values#trader-ids)
  	- [Location Details](/modding/references/quest-values#location-details)
  	- [Skill Names](/modding/references/quest-values#skill-names)
    - [Quest Types](/modding/references/quest-values#quest-types)
    - [Quest Status](/modding/references/quest-values#quest-status)
    - [Quest Properties](/modding/references/quest-values#properties)
  	- [Quest Structure](/modding/references/quest-values#quest-structure)
- [Visibility Conditions](/modding/references/quest-values#visibility-conditions)
-	[Available For Finish Conditions](/modding/references/quest-values#available-for-finish-conditions)
	- [Handover Item](/modding/references/quest-values#handover-item)
	- [Find Item](/modding/references/quest-values#find-item)
	- [Skill Requirement](/modding/references/quest-values#skill-requirement)
	- [Leave Item At Location](/modding/references/quest-values#leave-item-at-location)
	- [Place Beacon](/modding/references/quest-values#place-beacon)
	- [Visit Place](/modding/references/quest-values#visit-place)
	- [Weapon Assembly](/modding/references/quest-values#weapon-assembly)
	- [Kills](/modding/references/quest-values#kills)
	- [Exit Status](/modding/references/quest-values#exit-status)
	- [Exit Name](/modding/references/quest-values#exit-name)
	- [Trader Loyalty](/modding/references/quest-values#trader-loyalty)
  	- [Counter Creator](/modding/references/quest-values#counter-creator)
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
### Useful Links
[Item Finder](https://db.sp-tarkov.com/search)
[Vanilla Quest Data](https://github.com/sp-tarkov/server/blob/master/project/assets/database/templates/quests.json)
[Bot Types & Names Reference Sheet](/modding/references/bot-types)


### Trader IDs
Trader IDs are used in quest conditions, standing rewards, and quest properties for what trader issues the quest.

>
> Please ensure that you are using a **_valid MongoID_** if you are creating a custom trader, **_the custom trader will not load if it is an invalid MongoID._**
> You do not need to have a custom trader to create custom quests, you can create quests for vanilla traders.
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

### Skill Names
Below is a table of all currently used or previously used Skill Names for EFT. 
>
>Some values have been removed from the game but at still listed here for clarity for updating mods or modding previous versions of SPT.
>
| Skill Name | Value | Validity |
| :--- | :--- | :--- |
| Bot Reload | `"BotReload"` | Hidden Skill/Do Not Use for Quests |
| Bot Sound | `"BotSound"` | Hidden Skill/Do Not Use for Quests |
| Hideout Management | `"HideoutManagement"` | Valid |
| Crafting | `"Crafting"` | Valid |
| Metabolism | `"Metabolism"` | Valid |
| Immunity | `"Immunity"` | Valid |
| Endurance | `"Endurance"` | Valid |
| Strength | `"Strength"` | Valid |
| Vitality | `"Vitality"` | Valid |
| Health | `"Health"` | Valid |
| StressResistance | `"StressResistance"` | Valid |
| Throwing | `"Throwing"` | Valid |
| Recoil Control | `"RecoilControl"` | Removed as of 3.9 |
| Convert Movement | `"CovertMovement"` | Valid |
| Perception | `"Perception"` | Valid |
| Intellect | `"Intellect"` | Valid |
| Attention | `"Attention"` | Valid |
| Charisma | `"Charisma"` | Valid |
| Memory | `"Memory"` | Removed as of 3.9 |
| Melee | `"Melee"` | Valid |
| Surgery | `"Surgery"` | Valid |
| Aim Drills | `"AimDrills"` | Valid |
| Troubleshooting | `"TroubleShooting"` | Valid |
| First Aid | `"FirstAid"` | Valid |
| Light Vests | `"LightVests"` | Valid |
| Heavy Vests | `"HeavyVests"` | Valid |
| Weapon Treatment | `"WeaponTreatment"` | Valid |
| Mag Drills | `"MagDrills"` | Valid |
| Snipers | `"Sniper"` | Valid |
| Pistols | `"Pistol"` | Valid |
| Revolvers | `"Revolver"` | Valid |
| SMGs | `"SMG"` | Valid |
| Assault Rifles | `"Assault"` | Valid |
| Shotguns | `"Shotgun"` | Valid |
| LMGs | `"LMG"` | Valid |
| DMRs | `"DMR"` | Valid |

### Quest Types
Quest types are required and will display specific ways on the players Task List as well as in the trader Tasks page.
>
> All quests must have a type.
> Quest types will display the name and BSG Icon on the task list on the players client.
> The type does not have to match the conditions of the quest, but it is encouraged to match it for player clarity.
>

>
> I have added typical quest usage to the valid types table below. **_You do not have to follow these suggestions, they are common uses in BSG quests._** 
>You can do whatever you want for quest types _on the quest itself_, but conditions much match properly per the condition types.
{.is-info}

| Type | Typical Quest Usage |
| :--- | :--- |
| PickUp | Find/Handover |
| Elimination | Kill |
| Discover | LeaveItemAtLocation |
| Completion | Multi Conditional |
| Exploration | VisitPlace |
| Levelling | Prestige/Achievement/Level (Unused) |
| Experience | Experience (Unused) |
| Standing | TraderLoyalty |
| Loyalty | Branching quests (Like choosing one trader or another) |
| Merchant | Handing money over to a trader |
| Skill | Skill Requirements |
| Multi | Multi Conditional |
| WeaponAssembly | WeaponAssembly |
| ArenaWinMatch | Unused - Untested if works in SPT |
| ArenaWinRound | Unused - Untested if works in SPT |

### Quest Status
Quest Statuses are set automatically by the condition counters during raids, and out of raids. They can also be used in Available For Start requirements.
>
> All quests will always have a status. This status is stored in the users profile json.
>
| Status | Value | Description |
| :--- | :--- | :--- |
| Locked | 0 | Quest is locked and not available to the player |
| AvailableForStart | 1 | Quest is available to player |
| Started | 2 | Quest is available to the player, and they have accepted it |
| AvailableForFinish | 3 | Quest is available to the player, they have accepted it, and it is ready to turn in |
| Success | 4 | Quest has been completed by the player |
| Fail | 5 | Player has failed the quest and it is not marked restartable |
| FailRestartable | 6 | Player has failed the quest, and can restart it |
| MarkedAsFailed | 7 | Quest has been marked to fail but did not flip to status 5 or 6 yet |
| Expired | 8 | Quest has expired |
| AvailableAfter | 9 | Quest is available, but is delayed from being shown to the player |

### Properties

The below table is a list of all currently known properties for quests. 
>
> While not all properties are *required* for use, it is _best to have every single property, whether or not you are utilizing it_.
>
| Property Name | Required? | Example Value | Type |
| :--- | :--- | :--- | :--- |
| QuestName | Yes | `"Building Our First Quest!"` | string |
| _id | Yes | `"68423056128053531e5a5bf6"` | MongoID string |
| acceptPlayerMessage | No | `"68423056128053531e5a5bf6 acceptPlayerMessage"` | string |
| acceptanceAndFinishingSource | No | `"eft"` | string |
| arenaLocations | No | `[]` | array |
| canShowNotificationsInGame | Yes | `true` | boolean |
| changeQuestMessageText | No | `"68423056128053531e5a5bf6 changeQuestMessageText"` | string |
| completePlayerMessage | No | `"68423056128053531e5a5bf6 completePlayerMessage"` | string |
| conditions | Yes | | object ([AvailableForFinish](/modding/references/quest-values#available-for-finish-conditions)/[AvailableForStart](/modding/references/quest-values#available-for-start-requirements)/[Fail](/modding/references/quest-values#fail-conditions))|
| declinePlayerMessage | No | `"68423056128053531e5a5bf6 declinePlayerMessage"` | string |
| description | No | `"68423056128053531e5a5bf6 description"` | string |
| failMessageText | No | `"68423056128053531e5a5bf6 failMessageText"` | string |
| gameModes | No | `[]` | array |
| image | No | `"/files/quest/icon/quest_icon.png"` | string |
| instantComplete | No | `false` | boolean |
| isKey | No | `false` | boolean |
| location | Yes | `"5704e4dad2720bb55b8b4567"` | string ([Location Details Table](/modding/references/quest-values#location-details)) |
| name | Yes | `"68423056128053531e5a5bf6 name"` | string |
| note | No | `"68423056128053531e5a5bf6 note"` | string |
| progressSource | No | `"eft"` | string |
| rankingModes | No | `[]` | array |
| restartable | Yes | `false` | boolean |
| rewards | No | | object ([Rewards](/modding/references/quest-values#rewards)) |
| secretQuest | No | `false` | boolean |
| side | Yes | `"Pmc"` | string |
| startedMessageText | No | `"68423056128053531e5a5bf6 name"` | string |
| successMessageText | No | `"68423056128053531e5a5bf6 name"` | string |
| traderId | Yes | `"54cb50c76803fa8b248b4571"` | string ([Trader ID Table](/modding/references/quest-values#trader-ids)) |
| type | Yes | `"Skill"` | string ([Quest Type Table](/modding/references/quest-values#quest-types)) |

### Quest Structure
Below is an example quest that was created by BSG.

The following information can be found while reading through the quest structure. There is plenty more information that can be found, and I will not list all details here. You can read through the actual quest data yourself below and see what you can find!

- The Quest Name is "Debut"
- The quest ID is 5936d90786f7742b1420ba5b.
	- As you can see, this ID is also used in the various locale strings, such as "**acceptPlayerMessage**".
- The quest will show in-game notifications when a subtask is completed, as indicated by the "**canShowNotificationsInGame**" being true.
- The quest is an "**Elimination**" quest, so the player task list will have a skull and be branded "Elimination"
- The kills are required to be any non-PMC
	- Bosses & Scavs are classified as "**Savage**" and the role is not defined, so any non-PMC is a valid target.
	- The number of kills required is 5.
- The item being required to hand over is the "MP-133 12ga pump-action shotgun" as indicated by the target "**54491c4f4bdc2db1078b4568**".
	- These shotguns are not required to be FIR as indicated by "**onlyFoundInRaid**" being false.
- This quest unlocks at level 1, but the player must also have completed the quest ID "**657315df034d76585f032e01**"
	- The quest ID that is required is the quest named "Shooting Cans"
- This quest rewards experience, trader standing, items (including built weapons), and a trader assort unlock for Prapor.


```json
{
  "5936d90786f7742b1420ba5b": {
    "QuestName": "Debut",
    "_id": "5936d90786f7742b1420ba5b",
    "acceptPlayerMessage": "5936d90786f7742b1420ba5b acceptPlayerMessage",
    "acceptanceAndFinishingSource": "eft",
    "arenaLocations": [],
    "canShowNotificationsInGame": true,
    "changeQuestMessageText": "5936d90786f7742b1420ba5b changeQuestMessageText",
    "completePlayerMessage": "5936d90786f7742b1420ba5b completePlayerMessage",
    "conditions": {
      "AvailableForFinish": [
        {
          "completeInSeconds": 0,
          "conditionType": "CounterCreator",
          "counter": {
            "conditions": [
              {
                "bodyPart": [],
                "compareMethod": ">=",
                "conditionType": "Kills",
                "daytime": {
                  "from": 0,
                  "to": 0
                },
                "distance": {
                  "compareMethod": ">=",
                  "value": 0
                },
                "dynamicLocale": false,
                "enemyEquipmentExclusive": [],
                "enemyEquipmentInclusive": [],
                "enemyHealthEffects": [],
                "id": "5967379786f774620e763ea8",
                "resetOnSessionEnd": false,
                "savageRole": [],
                "target": "Savage",
                "value": 1,
                "weapon": [],
                "weaponCaliber": [],
                "weaponModsExclusive": [],
                "weaponModsInclusive": []
              }
            ],
            "id": "5967379186f77463860dadd5"
          },
          "doNotResetIfCounterCompleted": false,
          "dynamicLocale": false,
          "globalQuestCounterId": "",
          "id": "5967379186f77463860dadd6",
          "index": 0,
          "isNecessary": false,
          "isResetOnConditionFailed": false,
          "oneSessionOnly": false,
          "parentId": "",
          "type": "Elimination",
          "value": 5,
          "visibilityConditions": []
        },
        {
          "conditionType": "HandoverItem",
          "dogtagLevel": 0,
          "dynamicLocale": false,
          "globalQuestCounterId": "",
          "id": "596737cb86f77463a8115efd",
          "index": 3,
          "isEncoded": false,
          "maxDurability": 100,
          "minDurability": 0,
          "onlyFoundInRaid": false,
          "parentId": "",
          "target": [
            "54491c4f4bdc2db1078b4568"
          ],
          "value": 2,
          "visibilityConditions": []
        }
      ],
      "AvailableForStart": [
        {
          "compareMethod": ">=",
          "conditionType": "Level",
          "dynamicLocale": false,
          "globalQuestCounterId": "",
          "id": "658471a72957dfa0e01552d1",
          "index": 0,
          "parentId": "",
          "value": 1,
          "visibilityConditions": []
        },
        {
          "availableAfter": 0,
          "conditionType": "Quest",
          "dispersion": 0,
          "dynamicLocale": false,
          "globalQuestCounterId": "",
          "id": "658471a35740d10d154dac8f",
          "index": 1,
          "parentId": "",
          "status": [
            4,
            5
          ],
          "target": "657315df034d76585f032e01",
          "visibilityConditions": []
        }
      ],
      "Fail": []
    },
    "declinePlayerMessage": "5936d90786f7742b1420ba5b declinePlayerMessage",
    "description": "5936d90786f7742b1420ba5b description",
    "failMessageText": "5936d90786f7742b1420ba5b failMessageText",
    "gameModes": [],
    "image": "/files/quest/icon/596b465486f77457ca186188.jpg",
    "instantComplete": false,
    "isKey": false,
    "location": "any",
    "name": "5936d90786f7742b1420ba5b name",
    "note": "5936d90786f7742b1420ba5b note",
    "progressSource": "eft",
    "rankingModes": [],
    "restartable": false,
    "rewards": {
      "Fail": [],
      "Started": [],
      "Success": [
        {
          "availableInGameEditions": [],
          "id": "5fe305df8a67d12f5f24c8aa",
          "index": 0,
          "type": "Experience",
          "unknown": false,
          "value": 1700
        },
        {
          "availableInGameEditions": [],
          "id": "60c89c0c80b2027f403dd992",
          "index": 0,
          "target": "54cb50c76803fa8b248b4571",
          "type": "TraderStanding",
          "unknown": false,
          "value": 0.02
        },
        {
          "availableInGameEditions": [],
          "findInRaid": false,
          "id": "5fe305d9c646836c3b6fc562",
          "index": 0,
          "items": [
            {
              "_id": "67d82e6e4f4b5340e611a2d7",
              "_tpl": "5449016a4bdc2d6f028b456f",
              "upd": {
                "StackObjectsCount": 15000
              }
            }
          ],
          "target": "67d82e6e4f4b5340e611a2d7",
          "type": "Item",
          "unknown": false,
          "value": 15000
        },
        {
          "availableInGameEditions": [],
          "findInRaid": true,
          "id": "60cb4643f09d61072d6cf21a",
          "index": 0,
          "items": [
            {
              "_id": "67d82e6e4f4b5340e611a2d8",
              "_tpl": "57d14d2524597714373db789",
              "upd": {
                "StackObjectsCount": 1
              }
            },
            {
              "_id": "67d82e6e4f4b5340e611a2d9",
              "_tpl": "57d152ec245977144076ccdf",
              "parentId": "67d82e6e4f4b5340e611a2d8",
              "slotId": "mod_pistol_grip"
            },
            {
              "_id": "67d82e6e4f4b5340e611a2da",
              "_tpl": "57d1519e24597714373db79d",
              "parentId": "67d82e6e4f4b5340e611a2d8",
              "slotId": "mod_magazine"
            }
          ],
          "target": "67d82e6e4f4b5340e611a2d8",
          "type": "Item",
          "unknown": false,
          "value": 1
        },
        {
          "availableInGameEditions": [],
          "findInRaid": true,
          "id": "60cb467f7c496e588343a193",
          "index": 0,
          "items": [
            {
              "_id": "67d82e6e4f4b5340e611a2dd",
              "_tpl": "65702606cfc010a0f5006a3e",
              "upd": {
                "SpawnedInSession": true,
                "StackObjectsCount": 1
              }
            },
            {
              "_id": "67d82e6e4f4b5340e611a2de",
              "_tpl": "573718ba2459775a75491131",
              "parentId": "67d82e6e4f4b5340e611a2dd",
              "slotId": "cartridges",
              "upd": {
                "SpawnedInSession": true,
                "StackObjectsCount": 50
              }
            },
            {
              "_id": "67d82e6e4f4b5340e611a2df",
              "_tpl": "65702606cfc010a0f5006a3e",
              "upd": {
                "SpawnedInSession": true,
                "StackObjectsCount": 1
              }
            },
            {
              "_id": "67d82e6e4f4b5340e611a2e0",
              "_tpl": "573718ba2459775a75491131",
              "parentId": "67d82e6e4f4b5340e611a2df",
              "slotId": "cartridges",
              "upd": {
                "SpawnedInSession": true,
                "StackObjectsCount": 50
              }
            }
          ],
          "target": "67d82e6e4f4b5340e611a2df",
          "type": "Item",
          "unknown": false,
          "value": 2
        },
        {
          "availableInGameEditions": [],
          "id": "5ac64f3786f774056634a1cb",
          "index": 0,
          "items": [
            {
              "_id": "67d82e6e4f4b5340e611a2e1",
              "_tpl": "5839a40f24597726f856b511",
              "upd": {
                "FireMode": {
                  "FireMode": "single"
                },
                "Foldable": {
                  "Folded": false
                }
              }
            },
            {
              "_id": "67d82e6e4f4b5340e611a2e2",
              "_tpl": "5649ad3f4bdc2df8348b4585",
              "parentId": "67d82e6e4f4b5340e611a2e1",
              "slotId": "mod_pistol_grip"
            },
            {
              "_id": "67d82e6e4f4b5340e611a2e3",
              "_tpl": "57dc347d245977596754e7a1",
              "parentId": "67d82e6e4f4b5340e611a2e1",
              "slotId": "mod_stock"
            },
            {
              "_id": "67d82e6e4f4b5340e611a2e4",
              "_tpl": "564ca99c4bdc2d16268b4589",
              "parentId": "67d82e6e4f4b5340e611a2e1",
              "slotId": "mod_magazine"
            },
            {
              "_id": "67d82e6e4f4b5340e611a2e5",
              "_tpl": "57ffb0e42459777d047111c5",
              "parentId": "67d82e6e4f4b5340e611a2e1",
              "slotId": "mod_muzzle"
            },
            {
              "_id": "67d82e6e4f4b5340e611a2e6",
              "_tpl": "5839a7742459773cf9693481",
              "parentId": "67d82e6e4f4b5340e611a2e1",
              "slotId": "mod_reciever"
            },
            {
              "_id": "67d82e6e4f4b5340e611a2e7",
              "_tpl": "59d36a0086f7747e673f3946",
              "parentId": "67d82e6e4f4b5340e611a2e1",
              "slotId": "mod_gas_block"
            },
            {
              "_id": "67d82e6e4f4b5340e611a2e8",
              "_tpl": "57dc32dc245977596d4ef3d3",
              "parentId": "67d82e6e4f4b5340e611a2e7",
              "slotId": "mod_handguard"
            }
          ],
          "loyaltyLevel": 1,
          "target": "67d82e6e4f4b5340e611a2e1",
          "traderId": "54cb50c76803fa8b248b4571",
          "type": "AssortmentUnlock",
          "unknown": false
        },
        {
          "availableInGameEditions": [],
          "id": "629f016390948017ee17bb3b",
          "index": 0,
          "target": "5c0647fdd443bc2504c2d371",
          "type": "TraderStanding",
          "unknown": false,
          "value": 0.01
        }
      ]
    },
    "secretQuest": false,
    "side": "Pmc",
    "startedMessageText": "5936d90786f7742b1420ba5b startedMessageText",
    "status": 0,
    "successMessageText": "5936d90786f7742b1420ba5b successMessageText",
    "traderId": "54cb50c76803fa8b248b4571",
    "type": "Elimination"
  }
```
## Visibility Conditions
Visibility Conditions are an advanced feature available in creating quests for SPT. Most mod authors do not utilize these values, but they are extremely useful.

The use case for Visibility Conditions is if you have tasks in a quest that you may not want the player to see until they complete the relevant condition first. You can use these to "surprise" a player with additional tasks that do not appear in the task list until they are ready to be engaged with.

>
> Conditions "hiding" in a Visibility Condition do not track or count any values until they are visible to a player.
>

An example of this will be the "Background Check" quest from BSG.

This quest has 2 **FindItem** conditions and a **HandoverItem** condition. We don't actually care about one of the **FindItem** conditions, so that will not be included in the example.
The **HandoverItem** does not appear in the players task list until they complete the condition for finding the "Bronze pocket watch on a chain"

As you can see in the below example, the **HandoverItem** condition has a **visibilityCondition**. This condition requires the "conditionType" of **"CompleteCondition"** which means the _target_ must be completed before the **HandoverItem** condition becomes visible to player.

The _conditionType_ must be "CompleteCondition"
The _id_ must be a unique ID for the visibility array entry itself.
The _target_ is the condition ID that you are requiring to be completed before the condition itself becomes visible.

>
> You can have multiple requirements for a task to become visible, this example only has 1 condition that must be completed for the HandoverItem to be visible. If you would like an example of a quest that has multiple requirements for a condition, see "The Blood of War - Part 3" in the Vanilla Quests Data -> [Useful Links](/modding/references/quest-values#useful-links)
>
```json
{
  "conditionType": "FindItem",
  "countInRaid": false,
  "dogtagLevel": 0,
  "dynamicLocale": false,
  "globalQuestCounterId": "",
  "id": "5968ec9986f7741ddd6c1012",
  "index": 0,
  "isEncoded": false,
  "maxDurability": 100,
  "minDurability": 0,
  "onlyFoundInRaid": false,
  "parentId": "",
  "target": [
    "5937fd0086f7742bf33fc198"
  ],
  "value": 1,
  "visibilityConditions": []
},
{
  "conditionType": "HandoverItem",
  "dogtagLevel": 0,
  "dynamicLocale": false,
  "globalQuestCounterId": "",
  "id": "5967920f86f77468d219d632",
  "index": 1,
  "isEncoded": false,
  "maxDurability": 100,
  "minDurability": 0,
  "onlyFoundInRaid": false,
  "parentId": "",
  "target": [
    "5937fd0086f7742bf33fc198"
  ],
  "value": 1,
  "visibilityConditions": [
    {
      "conditionType": "CompleteCondition",
      "id": "5a5778c986f7740ad83cd652",
      "target": "5968ec9986f7741ddd6c1012"
    }
  ]
}
```


## Available For Finish Conditions
### Handover Item
>
> As with all properties in quests - you should use all available properties regardless of if you need them or not.
> BSG Quests uses all properties regardless of whether or not they are related to the item being handed over.
>

| Property Name | Example Value | Type | Notes |
| :--- | :--- | :--- | :--- |
| conditionType | `"HandoverItem"` | string | HandoverItem condition |
| dogtagLevel | `0` | int | Required if handing over DogTag |
| dynamicLocale | `false` | boolean | Currently unused |
| globalQuestCounterId | `""` | string | Currently unused |
| id | `"5a3fbdb086f7745a554f0c31"` | MongoID string | Unique ID for the condition |
| index | `0` | int | Currently unused (suspected added via BSG Tooling to build quests) |
| inEncoded | `false` | boolean | Required if requiring DSP Transmitter handover |
| maxDurability | `100` | int | Required for medical items, weapons, armour, etc |
| minDurability | `0` | int | Required for medical items, weapons, armour, etc |
| onlyFoundInRaid | `false` | boolean | If item is required to be FIR or not |
| parentId | `""` | MongoID string | Used to create optional sub-tasks for a task - see `"Bad Rep Evidence"` in the Vanilla Quests Data -> [Useful Links](/modding/references/quest-values#useful-links) --- Leave this as an empty string if not needed. |
| target | `["54491c4f4bdc2db1078b4568"]` | MongoID string array | ItemID that is to be handed over, you can have multiple items in the array for multiple choice. If wanting a dogtag handed over, it will only be the specified ID - if you want all of them to be accepted you will need to populate the array for every ID for dogtags. |
| value | `2` | int | Amount of items in target that are required to be handed over to complete subtask |
| visibilityConditions | `[]` | array | see [Visibility Conditions](/modding/references/quest-values#visibility-conditions) for example usage |

Example:
```json
				{
          "conditionType": "HandoverItem",
          "dogtagLevel": 0,
          "dynamicLocale": false,
          "globalQuestCounterId": "",
          "id": "596737cb86f77463a8115efd",
          "index": 3,
          "isEncoded": false,
          "maxDurability": 100,
          "minDurability": 0,
          "onlyFoundInRaid": false,
          "parentId": "",
          "target": [
            "54491c4f4bdc2db1078b4568"
          ],
          "value": 2,
          "visibilityConditions": []
        }
```

### Find Item
>
> As with all properties in quests - you should use all available properties regardless of if you need them or not.
> BSG Quests uses all properties regardless of whether or not they are related to the item being handed over.
>

| Property Name | Example Value | Type | Notes |
| :--- | :--- | :--- | :--- |
| conditionType | `"FindItem"` | string | HandoverItem condition |
| countInRaid | `false` | boolean | Currently unused, should always be false |
| dogtagLevel | `0` | int | Required if finding DogTag of specific level |
| dynamicLocale | `false` | boolean | Currently unused |
| globalQuestCounterId | `""` | string | Currently unused |
| id | `"5a3fbdb086f7745a554f0c31"` | MongoID string | Unique ID for the condition |
| index | `0` | int | Currently unused (suspected added via BSG Tooling to build quests) |
| inEncoded | `false` | boolean | Required if requiring DSP Transmitter handover |
| maxDurability | `100` | int | Required for medical items, weapons, armour, etc |
| minDurability | `0` | int | Required for medical items, weapons, armour, etc |
| onlyFoundInRaid | `false` | boolean | If item is required to be FIR or not |
| parentId | `""` | MongoID string | Used to create optional sub-tasks for a task - see `"Bad Rep Evidence"` in the Vanilla Quests Data -> [Useful Links](/modding/references/quest-values#useful-links) --- Leave this as an empty string if not needed. |
| target | `["54491c4f4bdc2db1078b4568"]` | MongoID string array | ItemID that is to be found, you can have multiple items in the array for multiple choice. If wanting a dogtag handed over, it will only count the specified IDs - if you want all of them to be accepted you will need to populate the array for every ID for dogtags. |
| value | `2` | int | Amount of items in target that are required to be found to complete subtask |
| visibilityConditions | `[]` | array | see [Visibility Conditions](/modding/references/quest-values#visibility-conditions) for example usage |

Example:
```json
{
  "conditionType": "FindItem",
  "countInRaid": false,
  "dogtagLevel": 0,
  "dynamicLocale": false,
  "globalQuestCounterId": "",
  "id": "5ac502a786f7740bde1b000c",
  "index": 0,
  "isEncoded": false,
  "maxDurability": 100,
  "minDurability": 0,
  "onlyFoundInRaid": true,
  "parentId": "",
  "target": [
    "59e36c6f86f774176c10a2a7"
  ],
  "value": 2,
  "visibilityConditions": []
}
```
### Skill Requirement
>
> As with all properties in quests - you should use all available properties regardless of if you need them or not.
> BSG Quests uses all properties regardless of whether or not they are related to the item being handed over.
>

| Property Name | Example Value | Type | Notes |
| :--- | :--- | :--- | :--- |
| compareMethod | `">="` | string | Method to compare player skill to required skill (example shows player must have higher than or equal to the example value) |
| conditionType | `"Skill"` | string | HandoverItem condition |
| dynamicLocale | `false` | boolean | Currently unused |
| globalQuestCounterId | `""` | string | Currently unused |
| id | `"5a3fbdb086f7745a554f0c31"` | MongoID string | Unique ID for the condition |
| index | `0` | int | Currently unused (suspected added via BSG Tooling to build quests) |
| parentId | `""` | MongoID string | Used to create optional sub-tasks for a task - see `"Bad Rep Evidence"` in the Vanilla Quests Data -> [Useful Links](/modding/references/quest-values#useful-links) --- Leave this as an empty string if not needed. |
| target | `"Charisma"` | string | Skill name that the condition targets - see [Skill Table](/modding/references/quest-values#skill-names) |
| value | `10` | int | Amount of items in target that are required to be found to complete subtask |
| visibilityConditions | `[]` | array | see [Visibility Conditions](/modding/references/quest-values#visibility-conditions) for example usage |

Example:
```json
{
  "compareMethod": ">=",
  "conditionType": "Skill",
  "dynamicLocale": false,
  "globalQuestCounterId": "",
  "id": "5ae9c29386f77427153c7fb0",
  "index": 0,
  "parentId": "",
  "target": "Charisma",
  "value": 10,
  "visibilityConditions": []
}
```
### Leave Item At Location
>
> As with all properties in quests - you should use all available properties regardless of if you need them or not.
> BSG Quests uses all properties regardless of whether or not they are related to the item being handed over.
>

>
> This quest type is NOT the same as PlaceBeacon. They have different in game behaviours. Beacon is persistent and can be removed/destroyed and will impact the players progress. LeaveItemAtLocation is completed and the item disappears as soon as it's placed.
>

| Property Name | Example Value | Type | Notes |
| :--- | :--- | :--- | :--- |
| conditionType | `"LeaveItemAtLocation"` | string | LeaveItemAtLocation condition |
| dogtagLevel | `0` | int | Required if finding DogTag of specific level |
| dynamicLocale | `false` | boolean | Currently unused |
| globalQuestCounterId | `""` | string | Currently unused |
| id | `"5a3fbdb086f7745a554f0c31"` | MongoID string | Unique ID for the condition |
| index | `0` | int | Currently unused (suspected added via BSG Tooling to build quests) |
| inEncoded | `false` | boolean | Required if requiring DSP Transmitter handover |
| maxDurability | `100` | int | Required for medical items, weapons, armour, etc |
| minDurability | `0` | int | Required for medical items, weapons, armour, etc |
| onlyFoundInRaid | `false` | boolean | If item to be placed is required to be FIR or not |
| parentId | `""` | MongoID string | Used to create optional sub-tasks for a task - see `"Bad Rep Evidence"` in the Vanilla Quests Data -> [Useful Links](/modding/references/quest-values#useful-links) --- Leave this as an empty string if not needed. |
| plantTime | `30` | int | Time in seconds that it takes the player to "place" the item |
| target | `["54491c4f4bdc2db1078b4568"]` | MongoID string array | ItemID that is to be placed, you can have multiple items in the array for multiple choice. If wanting a dogtag to be placed, it will only count the specified IDs - if you want all of them to be acceptable you will need to populate the array for every ID for dogtags. |
| value | `2` | int | Amount of items in target that are required to be found to complete subtask |
| visibilityConditions | `[]` | array | see [Visibility Conditions](/modding/references/quest-values#visibility-conditions) for example usage |
| zoneId | `"ter_017_area_1"` | string | This value is required and must match the `placeitem` zone that you have created (or use a vanilla zone ID). This zone indicates where the item must be placed. For zone creation, you may consider using the mod VCQL by Virtual. |

Example:
```json
{
  "conditionType": "LeaveItemAtLocation",
  "dogtagLevel": 0,
  "dynamicLocale": false,
  "globalQuestCounterId": "",
  "id": "5a687a1c86f7745f2152168c",
  "index": 2,
  "isEncoded": false,
  "maxDurability": 100,
  "minDurability": 0,
  "onlyFoundInRaid": false,
  "parentId": "",
  "plantTime": 30,
  "target": [
    "590c5a7286f7747884343aea"
  ],
  "value": 3,
  "visibilityConditions": [],
  "zoneId": "ter_017_area_1"
}
```
### Place Beacon

>
> As with all properties in quests - you should use all available properties regardless of if you need them or not.
> BSG Quests uses all properties regardless of whether or not they are related to the item being handed over.
>

>
> This quest type is NOT the same as LeaveItemAtLocation. They have different in game behaviours. Beacon is persistent and can be removed/destroyed and will impact the players progress. LeaveItemAtLocation is completed and the item disappears as soon as it's placed.
>

| Property Name | Example Value | Type | Notes |
| :--- | :--- | :--- | :--- |
| conditionType | `"PlaceBeacon"` | string | PlaceBeacon condition |
| dynamicLocale | `false` | boolean | Currently unused |
| globalQuestCounterId | `""` | string | Currently unused |
| id | `"5a3fbdb086f7745a554f0c31"` | MongoID string | Unique ID for the condition |
| index | `0` | int | Currently unused (suspected added via BSG Tooling to build quests) |
| parentId | `""` | MongoID string | Used to create optional sub-tasks for a task - see `"Bad Rep Evidence"` in the Vanilla Quests Data -> [Useful Links](/modding/references/quest-values#useful-links) --- Leave this as an empty string if not needed. |
| plantTime | `30` | int | Time in seconds that it takes the player to "place" the item |
| target | `["5991b51486f77447b112d44f"]` | MongoID string array | You should **only use** the ID for the MS2000 Marker (`5991b51486f77447b112d44f`) or the Radio Repeater (`63a0b2eabea67a6d93009e52`). Since the item persists after placing, I believe these two IDs are the only ones currently used for this quest type.|
| value | `1` | int | Amount of beacons that must be placed to complete the task. |
| visibilityConditions | `[]` | array | see [Visibility Conditions](/modding/references/quest-values#visibility-conditions) for example usage |
| zoneId | `"gazel"` | string | This value is required and must match the `placeitem` zone that you have created (or use a vanilla zone ID). This zone indicates where the item must be placed. For zone creation, you may consider using the mod VCQL by Virtual. |

Example:
```json
{
  "conditionType": "PlaceBeacon",
  "dynamicLocale": false,
  "globalQuestCounterId": "",
  "id": "5998366886f77455853b2d9f",
  "index": 1,
  "parentId": "",
  "plantTime": 30,
  "target": [
    "5991b51486f77447b112d44f"
  ],
  "value": 1,
  "visibilityConditions": [],
  "zoneId": "gazel"
}
```

### Visit Place

>
> As with all properties in quests - you should use all available properties regardless of if you need them or not.
> BSG Quests uses all properties regardless of whether or not they are related to the item being handed over.
>

>
> Notice that the quest structure for this type is actually inside a "CounterCreator" condition.
> "CounterCreator" conditions hold various condition types, and must be used for this condition type.
{.is-info}

| Property Name | Example Value | Type | Notes |
| :--- | :--- | :--- | :--- |
| conditionType | `"VisitPlace"` | string | VisitPlace condition |
| dynamicLocale | `false` | boolean | Currently unused |
| globalQuestCounterId | `""` | string | Currently unused |
| id | `"5a3fbdb086f7745a554f0c31"` | MongoID string | Unique ID for the condition |
| target | `"place_peacemaker_001"` | string | This value is required and must match the `visit` zone that you have created (or use a vanilla zone ID). This zone indicates where the player must visit. For zone creation, you may consider using the mod VCQL by Virtual. |
| value | `1` | int | This is always 1. The actual value of how many times you must complete the "VisitPlace" condition is the `value` property on the `CounterCreator` itself, and not the one within the `VisitPlace` condition. |

Example:
```json
{
  "completeInSeconds": 0,
  "conditionType": "CounterCreator",
  "counter": {
    "conditions": [
      {
        "conditionType": "VisitPlace",
        "dynamicLocale": false,
        "id": "5a3ba1c286f7742c9d4f5d49",
        "target": "place_peacemaker_001",
        "value": 1
      }
    ],
    "id": "5a3ba11786f7742c9d4f5d28"
  },
  "doNotResetIfCounterCompleted": false,
  "dynamicLocale": false,
  "globalQuestCounterId": "",
  "id": "5a3ba11786f7742c9d4f5d29",
  "index": 1,
  "isNecessary": false,
  "isResetOnConditionFailed": false,
  "oneSessionOnly": false,
  "parentId": "",
  "type": "Exploration",
  "value": 1,
  "visibilityConditions": []
}
```

### Weapon Assembly
>
> As with all properties in quests - you should use all available properties regardless of if you need them or not.
> BSG Quests uses all properties regardless of whether or not they are related to the item being handed over.
>

>
> These types of quest conditions are personally the hardest to get correct. It is very easy to mess up a compare method or use an invalid value.
> Double, triple, and quadruple check these quests as you build them. Test. Them.
{.is-warning}

| Property Name | Example Value | Type | Child Property Name | Child Example Value | Child Type | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| conditionType | `"WeaponAssembly"` | string | | | | WeaponAssembly condition |
| id | `"5accd5e386f77463027e9397"` | MongoID string | | | | Unique ID for the condition |
| index | `0` | int | | | | Currently unused (suspected added via BSG Tooling to build quests) |
| dynamicLocale | `""` | string | | | | Currently unused |
| globalQuestCounterId | `""` | string | | | | Currently unused |
| containsItems | `["5aa66be6e5b5b0214e506e97"]` | string array | | | | List of ItemIDs in an array that the weapon must have attached |
| parentId | `""` | MongoID string | | | | Used to create optional sub-tasks for a task - see `"Bad Rep Evidence"` in the Vanilla Quests Data -> [Useful Links](/modding/references/quest-values#useful-links) --- Leave this as an empty string if not needed. |
| baseAccuracy | - | object | compareMethod | >= | string | Weapon MOA Requirements |
| | | | value | 0 | int | |
| durability | - | object | compareMethod | >= | string | Current durability requirements |
| | | | value | 60 | int | |
| effectiveDistance | - | object | compareMethod | >= | string | Sighting Range requirements |
| | | | value | 60 | int | |
| emptyTacticalSlot | - | object | compareMethod | >= | string | How many empty tactical slots are required |
| | | | value | 60 | int | |
| ergonomics | - | object | compareMethod | >= | string | Ergonomics requirements |
| | | | value | 60 | int | |
| hasItemFromCategory | `["55818b164bdc2ddc698b456c"]` | string array | | | | List of Item Category IDs that the weapon must have attached |
| height | - | object | compareMethod | <= | string | Number of vertical grid cells the weapon must have in the stash |
| | | | value | 2 | int | |
| magazineCapacity | - | object | compareMethod | <= | string | Requirements for size of the attached magazine |
| | | | value | 50 | int | |
| muzzleVelocity | - | object | compareMethod | >= | string | Velocity Requirements (Velocity * SpeedFactor) |
| | | | value | 0 | int | |
| recoil | - | object | compareMethod | <= | string | Sum of Horizontal & Vertical recoil is the value to compare |
| | | | value | 300 | int | |
| target | `["5bfea6e90db834001b7347f3"]` | string array |  |  |  | The ItemID of the weapon to be built |
| value | `1` | int |  |  |  | The number of weapons that must be built and handed over that match the requirements (untested over 1) |
| visibilityConditions | `[]` | array | | | | see [Visibility Conditions](/modding/references/quest-values#visibility-conditions) for example usage |
| weight | - | object | compareMethod | <= | string | Weapon must match the comparison of the value to be valid |
| | | | value | 4.5 | float | |
| width | - | object | compareMethod | <= | string | Number of horizontal grid cells the weapon must have in the stash |
| | | | value | 8 | int | |

Example:
```json
{
  "baseAccuracy": {
    "compareMethod": ">=",
    "value": 0
  },
  "conditionType": "WeaponAssembly",
  "containsItems": [],
  "durability": {
    "compareMethod": ">=",
    "value": 60
  },
  "dynamicLocale": false,
  "effectiveDistance": {
    "compareMethod": ">=",
    "value": 0
  },
  "emptyTacticalSlot": {
    "compareMethod": ">=",
    "value": 0
  },
  "ergonomics": {
    "compareMethod": ">=",
    "value": 47
  },
  "globalQuestCounterId": "",
  "hasItemFromCategory": [
    "55818b164bdc2ddc698b456c"
  ],
  "height": {
    "compareMethod": "<=",
    "value": 1
  },
  "id": "5accd5e386f77463027e9397",
  "index": 0,
  "magazineCapacity": {
    "compareMethod": ">=",
    "value": 5
  },
  "muzzleVelocity": {
    "compareMethod": ">=",
    "value": 0
  },
  "parentId": "",
  "recoil": {
    "compareMethod": "<=",
    "value": 850
  },
  "target": [
    "54491c4f4bdc2db1078b4568"
  ],
  "value": 1,
  "visibilityConditions": [],
  "weight": {
    "compareMethod": ">=",
    "value": 0
  },
  "width": {
    "compareMethod": "<=",
    "value": 4
  }
}
```

### Kills

>
> As with all properties in quests - you should use all available properties regardless of if you need them or not.
> BSG Quests uses all properties regardless of whether or not they are related to the item being handed over.
>

>
> Notice that the quest structure for this type is actually inside a "CounterCreator" condition.
> "CounterCreator" conditions hold various condition types, and must be used for this condition type.
> See [CounterCreator]()
{.is-info}

| Property Name | Example Value | Type | Notes |
| :--- | :--- | :--- | :--- |
| bodyPart | `["Head"]` | string array | If populated, requires specific kill shots to count. See [Body Part Values]() |
| compareMethod | `">="` | string | Compare method, there's really no reason to use anything other than `">="`
| conditionType | `"Kills"` | string | Kills condition |
| daytime | see example below | object | In game hour requirement, not required - if either value is not 0 then it is enforced for the kill to count (typically used for night raids). Leave `from` & `to` both at `0` to not have a time requirement |
| distance | see example below | object | Distance requirement, not required - if either value is not 0 then it is enforced for the kill to count (typically used for night raids). Set `compareMethod` to `">="` & `value` to `0` to not have a distance requirement. Value is distance in meters. |
| dynamicLocale | `false` | boolean | Currently unused |
| enemyEquipmentExclusive | `[]` | boolean | If populated, requires specific equipment to not be worn by enemy when killed (Not Used by BSG, untested) |
| enemyEquipmentInclusive | `[]` | boolean | If populated, requires specific equipment to be worn by enemy when killed (Not Used by BSG, untested) |
| enemyHealthEffects | `[]` | boolean | If populated, requires specific health ailments to be active on enemy when killed (Not Used by BSG, untested) |
| id | `"5a3fbdb086f7745a554f0c31"` | MongoID string | Unique ID for the condition |
| resetOnSessionEnd | `false` | boolean | Whether the condition resets to 0 if not completed by session end (Exfil/death/etc) - In otherwords, the kill condition must be completed in 1 raid or it resets if `true` |
| savageRole | `[]` | string array | If specified, then the kill will only count if the player kills that specific bot type. See [Bot Type & Name Reference Sheet](/modding/references/bot-types) |
| target | `"AnyPmc"` | string | Must be `"AnyPmc"`, `"Savage"`, or `"Any"`. See [Bot Type & Name Reference Sheet](/modding/references/bot-types) for clarification on what is a Savage or Pmc. Specifying `"Any"` will count any kill no matter what. |
| value | `1` | int | This is always 1. The actual value of how many kills you must achieve to complete the condition is the `value` property on the `CounterCreator` itself, and not the one within the `Kills` condition. |
| weapon | `[]` | string array | Array of weapons that must make the killing blow to count towards the condition. Can be empty.|
| weaponCaliber | `[]` | string array | Unused |
| weaponModsExclusive | `[]` | string array | Array of weapon attachments - if the killing weapon has any of these attachments then the kill will not count. |
| weaponModsInclusive | `[]` | string array | Array of weapon attachments - the killing weapon must have these attachments to be counted. |

Example:
```json
{
  "completeInSeconds": 0,
  "conditionType": "CounterCreator",
  "counter": {
    "conditions": [
      {
        "bodyPart": [],
        "compareMethod": ">=",
        "conditionType": "Kills",
        "daytime": {
          "from": 22,
          "to": 7
        },
        "distance": {
          "compareMethod": ">=",
          "value": 20
        },
        "dynamicLocale": false,
        "enemyEquipmentExclusive": [],
        "enemyEquipmentInclusive": [],
        "enemyHealthEffects": [],
        "id": "5edab65ececc0069284c0ec3",
        "resetOnSessionEnd": false,
        "savageRole": [
          "bossSanitar"
        ],
        "target": "Savage",
        "value": 1,
        "weapon": [],
        "weaponCaliber": [],
        "weaponModsExclusive": [],
        "weaponModsInclusive": []
      }
    ],
    "id": "5edab5a6cecc0069284c0ec1"
  },
  "doNotResetIfCounterCompleted": false,
  "dynamicLocale": false,
  "globalQuestCounterId": "",
  "id": "5edab5a6cecc0069284c0ec2",
  "index": 0,
  "isNecessary": false,
  "isResetOnConditionFailed": false,
  "oneSessionOnly": false,
  "parentId": "",
  "type": "Elimination",
  "value": 1,
  "visibilityConditions": []
}
```
### Exit Status
>
> As with all properties in quests - you should use all available properties regardless of if you need them or not.
> BSG Quests uses all properties regardless of whether or not they are related to the item being handed over.
>

>
> Notice that the quest structure for this type is actually inside a "CounterCreator" condition.
> "CounterCreator" conditions hold various condition types, and must be used for this condition type.
{.is-info}

>
> Exit Status conditions can be paired with Exit Name conditions within a "CounterCreator" to also require a specific exfil to have been taken by the player to count. See the example.
{.is-info}

| Property Name | Example Value | Type | Notes |
| :--- | :--- | :--- | :--- |
| conditionType | `"ExitStatus"` | string | ExitStatus condition |
| dynamicLocale | `false` | boolean | Currently unused |
| id | `"5a3fbdb086f7745a554f0c31"` | MongoID string | Unique ID for the condition |
| status | `["Survived", "Transit", "Runner"]` | string array | Depending on what you populate in the array, those are the available exfil statuses that can complete the condition. If you specify the example to the left and the player is killed, the counter remains at 0, because you did not specify "Killed" as a status. If they Transit, they will complete this condition. For valid statuses, see below table. |


| Status Name | Requirements |
| :--- | :--- |
| "Survived" | Player earned 200+ XP or spent at least 7 minutes in raid, and successfully exfilled - not transit. |
| "Killed" | Player dies in raid. |
| "Left" | Player left raid. (Does not apply in SPT) |
| "Runner" | Player exfilled before 7 minutes in raid and did not earn at least 200 XP. |
| "MissingInAction" | Player did not exfil or transit prior to raid time expiring. |
| "Transit" | Player activated a transit and moved to another map. |

Example:
```json
{
  "completeInSeconds": 0,
  "conditionType": "CounterCreator",
  "counter": {
    "conditions": [
      {
        "conditionType": "ExitStatus",
        "dynamicLocale": false,
        "id": "669fb170617a3971bb525b2a",
        "status": [
          "Survived",
          "Transit"
        ]
      },
      {
        "conditionType": "ExitName",
        "dynamicLocale": false,
        "exitName": "Gate_o",
        "id": "66c0a86de55c52cd17921935"
      }
    ],
    "id": "669fb12ec1fbcb64b49837ab"
  },
  "doNotResetIfCounterCompleted": false,
  "dynamicLocale": false,
  "globalQuestCounterId": "",
  "id": "669fb12eb01ceef19a5b4ebc",
  "index": 0,
  "isNecessary": false,
  "isResetOnConditionFailed": false,
  "oneSessionOnly": false,
  "parentId": "",
  "type": "Completion",
  "value": 1,
  "visibilityConditions": []
}
```
### Exit Name
>
> As with all properties in quests - you should use all available properties regardless of if you need them or not.
> BSG Quests uses all properties regardless of whether or not they are related to the item being handed over.
>

>
> Notice that the quest structure for this type is actually inside a "CounterCreator" condition.
> "CounterCreator" conditions hold various condition types, and must be used for this condition type.
{.is-info}

>
> Exit Name conditions can be paired with Exit Status conditions within a "CounterCreator" to also require a specific exfiltration status by the player to count. See the example.
{.is-info}

| Property Name | Example Value | Type | Notes |
| :--- | :--- | :--- | :--- |
| conditionType | `"ExitName"` | string | ExitStatus condition |
| dynamicLocale | `false` | boolean | Currently unused |
| id | `"5a3fbdb086f7745a554f0c31"` | MongoID string | Unique ID for the condition |
| exitName | `"EXFIL_Train"` | string | Name of the exfil that the player must take to complete the condition. For valid exfil names, see [SPT Location Data](https://github.com/sp-tarkov/server/tree/master/project/assets/database/locations) on the GitHub, and view the `allExtracts.json` for the location you are interested in requiring players to exfil from. |

Example:
```json
{
  "completeInSeconds": 0,
  "conditionType": "CounterCreator",
  "counter": {
    "conditions": [
      {
        "conditionType": "ExitStatus",
        "dynamicLocale": false,
        "id": "669fb170617a3971bb525b2a",
        "status": [
          "Survived",
          "Runner",
          "Transit"
        ]
      },
      {
        "conditionType": "ExitName",
        "dynamicLocale": false,
        "exitName": "Gate_o",
        "id": "66c0a86de55c52cd17921935"
      }
    ],
    "id": "669fb12ec1fbcb64b49837ab"
  },
  "doNotResetIfCounterCompleted": false,
  "dynamicLocale": false,
  "globalQuestCounterId": "",
  "id": "669fb12eb01ceef19a5b4ebc",
  "index": 0,
  "isNecessary": false,
  "isResetOnConditionFailed": false,
  "oneSessionOnly": false,
  "parentId": "",
  "type": "Completion",
  "value": 1,
  "visibilityConditions": []
}
```
### Trader Loyalty
>
> As with all properties in quests - you should use all available properties regardless of if you need them or not.
> BSG Quests uses all properties regardless of whether or not they are related to the item being handed over.
>

| Property Name | Example Value | Type | Notes |
| :--- | :--- | :--- | :--- |
| compareMethod | `">="` | string | Compare method, no reason to really change this unless you want to require them to be lower loyalty levels, which may cause the player to be unable to complete this |
| conditionType | `"TraderLoyalty"` | string | TraderLoyalty condition |
| dynamicLocale | `false` | boolean | Currently unused |
| globalQuestCounterId | `""` | string | Currently unused |
| id | `"5a3fbdb086f7745a554f0c31"` | MongoID string | Unique ID for the condition |
| index | `0` | int | Currently unused (suspected added via BSG Tooling to build quests) |
| target | `"54cb50c76803fa8b248b4571"` | string | Trader ID for the value requirement of the loyalty level. See [TraderIDs](/modding/references/quest-values#trader-ids) |
| value | `3` | float | Loyalty Level required for the player to compare against using the `compareMethod` |
| visibilityConditions | `[]` | array | see [Visibility Conditions](/modding/references/quest-values#visibility-conditions) for example usage |

Example:
```json
{
  "compareMethod": ">=",
  "conditionType": "TraderLoyalty",
  "dynamicLocale": false,
  "globalQuestCounterId": "",
  "id": "5dbadfd186f77449467d1482",
  "index": 0,
  "parentId": "",
  "target": "54cb50c76803fa8b248b4571",
  "value": 3,
  "visibilityConditions": []
}
```
### Counter Creator
>
> As with all properties in quests - you should use all available properties regardless of if you need them or not.
> BSG Quests uses all properties regardless of whether or not they are related to the item being handed over.
>

Counter Creator's are used to combine multiple conditions together within a single task of a quest, or even by itself with a single condition because it is required. It is highly advised to have read the relevant documentation for the type of condition you are trying to create.

Do not be afraid to mess around the multiple conditions inside a count creator to understand how it functions and how you can utilize it to create unique quests that others (including BSG!) may not have thought to do.

>
> Many quest conditions are nested inside a Counter Creator. For their specific behaviour within a counter creator, please read the relevant sections for that condition type.
{.is-info}

| Property Name | Example Value | Type | Notes |
| :--- | :--- | :--- | :--- |
| completeInSeconds | `0` | int | Currently unused |
| conditionType | `"CounterCreator"` | string | CounterCreator condition |
| counter | | object | See relevant condition documentation |
| doNotResetIfCounterCompleted | `false` | boolean | Works in tandem with `isResetOnConditionFailed` and on its own. If true, and `value` is less than condition value, can set the condition value to 0. In some scenarios, it will check the `isResetOnConditionFailed` property first. Largely unused. See the quest `"Chemistry Closet"` in the Vanilla Quests Data -> [Useful Links](/modding/references/quest-values#useful-links) for usage. |
| dynamicLocale | `false` | boolean | Currently unused |
| globalQuestCounterId | `""` | string | Currently unused |
| id | `"5a3fbdb086f7745a554f0c31"` | MongoID string | Unique ID for the condition |
| index | `0` | int | Currently unused (suspected added via BSG Tooling to build quests) |
| isNecessary | `false` | boolean | Used in tandem with parentId. If true, and parentId used for optional condition, requires it instead of being optional. Largely unused. |
| isResetOnConditionFailed | `false` | boolean | Used in tandem with `doNotResetIfCounterCompleted`. If true, and `doNotResetIfCounterCompleted` is true - Will reset the value of the counter to 0 if any conditions are not met when starting a raid. This has never been used, untested if works properly. |
| oneSessionOnly | `false` | boolean | Currently unused |
| parentId | `""` | MongoID string | Used to create optional sub-tasks for a task - see `"Bad Rep Evidence"` in the Vanilla Quests Data -> [Useful Links](/modding/references/quest-values#useful-links) --- Leave this as an empty string if not needed. |
| type | `"Elimination"` | string | Type of condition for the counter creator. |
| value | `5` | int | Number of nested condition counts required to count the `CounterCreator` condition as completed. (Ie, 5 kills, 5 visits, etc) |
| visibilityConditions | `[]` | array | see [Visibility Conditions](/modding/references/quest-values#visibility-conditions) for example usage |

## Available For Start Requirements

## Fail Conditions

## Rewards
### Experience
### Item
### Trader Standing
### Skill
### Stash Rows
### Achievement