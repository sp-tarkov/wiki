---
title: WTT - Item Creation Guides Vol. 1: Intro to Static Objects
description: 
published: true
date: 2025-11-01T08:26:02.663Z
tags: modding
editor: markdown
dateCreated: 2025-11-01T08:26:02.663Z
---

<img src="https://i.ibb.co/nsqLjRn4/AA8i-VLt-JUP9fe-Cgw9f-Tz-We9mpzhf-Zhuk-T05z-Z-1h-Ua-XXVR79o-W1x-HEz-Ch-T9j6-CZ14c-Aiq-HSMx-RCcm-MK72.png" alt="baby" width=600 style="display: block; margin: 0 auto;">

## Prerequisites

- [Blender (v3.0+ recommended)](https://www.blender.org/)
- [Unity Hub (2019.39f)](https://unity.com/)
- [Escape from Tarkov SDK](https://github.com/S3RAPH-1M/EscapeFromTarkov-SDK)
- A 3D Model Sources:
	- [Sketchfab](https://sketchfab.com/) (filter by Low Poly + Free Download)
	- [TurboSquid](https://www.turbosquid.com/) (search for Game Ready models)
	- Create a model, or source it yourself!
- A Server Mod ready for you to add your item and test it in game.

**NOTE: This guide does NOT cover server modding - just item creation.**



## 1. What You’ll Learn

This guide teaches you how to add static objects (loot, quest items, etc) to Escape from Tarkov using Blender and Unity. By the end, you’ll be able to:

- Import and scale 3D models to match Tarkov’s scale.
- Configure Tarkov-specific scripts inside Unity to prepare your item.
- Build a custom asset bundle, ready for use in-game.

Difficulty: Beginner

Time Required: 30 mins - 1 hour


## 2. Source Your Model


What to Do:

1. Have your 3D model ready, create one, or download a low-poly model (.fbx, .obj, or .blend) from Sketchfab/TurboSquid.
	- Try to avoid models over 10k triangles (use Blender’s Statistics panel to check). Exceptions can be made, but try and remain as low-poly as possible.
2. Example Search Terms: “Keycard Low Poly,” “Military Crate Game Ready.”

For this tutorial, we will be using these [Russian GP5 Filters](https://sketchfab.com/3d-models/russian-gp5-filters-695d7745151b4796a46b4e070811a596).
<div style="margin-top: 10px;"></div>
<img src="https://i.ibb.co/hFgB56qh/Screenshot-2025-02-24-064041.png" alt="gas filters" width=800 style="display: block; margin: 0 auto;">

> **Pro Tip**: Always check the model’s licenses.
{.is-info}


## 3. Import into Blender

What to Do:

1. Start with a clean scene: Select all default objects and delete them.
2. Import your custom model:
	- For `.blend` files: `File > Open`
	- For `.fbx/.obj/etc` files: `File > Import`
  
<div style="margin-top: 10px;"></div>
<img src="https://i.ibb.co/NzZ11Km/Screen-Recording-2025-02-24-162322.gif" alt="import" width=800 style="display: block; margin: 0 left;">

3. Import the Tarkov PMC example model for scale reference:
	- You can find this model inside the `Escape From Tarkov SDK/Assets/Examples/Models/ExampleCharacter.fbm/ExampleCharacter.fbx` .
	- In Blender: `File` > `Import` > `FBX` → Select the `ExampleCharacter` file.
  
<div style="margin-top: 10px;"></div>
<img src="https://i.ibb.co/Z6qksNf6/Screen-Recording-2025-02-24-163455.gif" alt="model import" width=800 style="display: block; margin: 0 left;">

4. Scale & Position:
	- Press <kbd>S</kbd> to scale. Use <kbd>S</kbd> + <kbd>X</kbd>/<kbd>Y</kbd>/<kbd>Z</kbd> to adjust individual axes.
	- Press <kbd>G</kbd> to grab your model. Use <kbd>G</kbd> + <kbd>X</kbd>/<kbd>Y</kbd>/<kbd>Z</kbd> to move individual axes.
	- Match your object to the PMC’s scale as closely as you can for your desired object.
  
<div style="margin-top: 10px;"></div>
<img src="https://i.ibb.co/tTDP5hDp/Screen-Recording-2025-02-24-163541.gif" alt="scale" width=800 style="display: block; margin: 0 left;">

5. Apply Transforms:
	- Right-click model → `Set Origin` → `Origin to Geometry`. This will set the objects origin to the center of its geometry.
	- Press <kbd>Ctrl</kbd> + <kbd>A</kbd> → Apply `Rotation & Scale` to finalize object size.
  
<div style="margin-top: 10px;"></div>
<img src="https://i.ibb.co/CKJjrNvF/Screen-Recording-2025-02-24-163615.gif" alt="transform" width=800 style="display: block; margin: 0 left;">

6. Center the Object & Save:
	- Press <kbd>Alt</kbd> + <kbd>G</kbd> to clear all transforms, setting your object back to Blender's World's Origin of `0, 0, 0`.
	- Delete the example character (Armature and Meshes) once you're done.
	- Save your file! You're done with the Blender portion!

<div style="margin-top: 10px;"></div>
<img src="https://i.ibb.co/v4Yj5B0N/Screen-Recording-2025-02-24-164033.gif" alt="transform" width=800 style="display: block; margin: 0 left;">

> **Troubleshooting**: If scaling looks wrong in Unity, re-apply transforms in Blender.
{.is-info}


## 4. Import into Unity

What to Do:

1. Drag your `.blend` file into Unity’s **Assets** folder.

<div style="margin-top: 10px;"></div>
<img src="https://i.ibb.co/gnWBhZh/Screen-Recording-2025-02-24-195229.gif" alt="assets" width=800 style="display: block; margin: 0 left;">

2. Extract material (and textures if there are any) from model:
	- Click the `.blend` file → `Inspector > Materials > Extract Embedded Materials`. You can choose a folder to extract them to, or just hit okay and they'll extract to the same location as the `.blend` file.
  
<div style="margin-top: 10px;"></div>
<img src="https://i.ibb.co/7tMwn4Nw/Screen-Recording-2025-02-24-195310.gif" alt="extract" width=800 style="display: block; margin: 0 left;">

3. Assign Tarkov shaders:
	- Select material → `Shader > Bumped Specular Smap` (Tarkov's most used shader).
	- If you don't have textures assigned, now would be the time to drag them onto the material. Diffuse(Specular), Normal, and Gloss if you have one. Tarkov uses a specular shader, meaning the specularness is baked into the actual diffuse texture.
	- Every texture is going to differ, especially if you have an actual proper texture with a baked specular. However, for a baseline on items that *DON'T* have proper textures (Like our example GP5 Model) I usually start with:

|-|-|
| Main Color 				|	White |
| Specularness 			|	`0.35` |
| Glossness 				|	`1` |
| Reflection Color	|	Black (or almost) |
| Specular Vals 		|	`1 1 0 0` |
| Defuse Vals				|	`1 1 0 0` |

- From here, you need to adjust the values per-material in order to get it to look the way you want.
- Once you have your shader setup and textures applied, it should automatically apply to your imported model. If it doesn't, just drag the material onto your model during the next steps.

<div style="margin-top: 10px;"></div>
<img src="https://i.ibb.co/yFMfBx81/Screen-Recording-2025-02-24-195347.gif" alt="shader" width=800 style="display: block; margin: 0 left;">

> **Important Note**: Install Blender on your system first. Unity requires it to process `.blend` files natively!
{.is-warning}


## 5. Setting Up the GameObject

What to Do:

1. Drag your `.blend` file into the scene heirarchy (top left window), right-click it and `Unpack Prefab Completely`.

<div style="margin-top: 10px;"></div>
<img src="https://i.ibb.co/7tDY3Z8b/Screen-Recording-2025-02-25-072543.gif" alt="unpack" width=800 style="display: block; margin: 0 left;">

2. Setup your GameObject heirarchy exactly like this:
	- Create an empty gameobject: Right-click `Hierarchy` → `Create Empty` → Rename to your desired GameObject Name.
	- Position at `0, 0, 0`.
	- Drag your model into the empty GameObject.

<div style="margin-top: 10px;"></div>
<img src="https://i.ibb.co/cSmw4x2L/Screen-Recording-2025-02-25-072733.gif" alt="gameobject" width=800 style="display: block; margin: 0 left;">

3. Setup your GameObject scripts exactly like this:
	- Select the `child mesh (your model) → Add Component → Mesh Collider → Check the Convex option to simplify the collider` .
	- Attach the `PreviewPivot` script to your Main Empty Gameobject.
	- Configure the preview pivot:
		- Open the SDK's `Preview Pivot Editor` (Window > Item Preview).
		- Drag the empty gameobject with the preview pivot component into the top entry of the Item Preview Window.
		- Drag the object around to move its rotation.
		- Once you're satisfied with the position, hit `Save current rotation to PreviewPivot` and `Render Icon`.

<div style="margin-top: 10px;"></div>
<img src="https://i.imgur.com/v4iVF5P.gif" alt="pivot" width=800 style="display: block; margin: 0 left;">


> **Pro Tips**:
	- Use a consistent naming scheme (e.g.: `Item_Quest_[Name]`) to avoid confusion.
	- If your preview window doesn't show the item, try adjusting the window size and checking to make sure your object's origin is centered.
	- You can adjust the size of the object and icon in the Item Preview Window
	- You may need to close and re-open the preview pivot window to see your changes applied.
{.is-info}

## 6. Build the Asset Bundle

What to Do:

1. Create a prefab:
	- Drag your GameObject into the `Assets` folder.
2. Assign labels:
	- Select `prefab` → `Inspector` → `Asset Label` → Add "your prefab name" and the bundle extension.
3. Build the bundle:
	- Open `Window → Asset Bundle Browser`.
	- Open the `Build` tab → Click `Build`.

<div style="margin-top: 10px;"></div>
<img src="https://i.imgur.com/AvkTqXk.gif" alt="build" width=800 style="display: block; margin: 0 left;">



> **Critical**:
Ensure you wait until Unity becomes FULLY RESPONSIVE after the build process, or your shaders might not appear in game.
If the AssetBundle Label entry doesn't let you type, either click off of it and then try again OR hold down your left mouse button on the entry as you type. I know, it's the worst...
{.is-danger}

## 7. Test in Tarkov

What to Do:

1. Debug issues:
	- **Purple Model?** Reassign textures shaders in Unity.
	- **Preview Pivot off-center?** Adjust your origins in blender, or manually move the coordinates in the preview pivot component.
	-	**Item Falls through the Ground?** You might have forgot to add a mesh collider to your model, or put it on the wrong GameObject.

<div style="margin-top: 10px;"></div>
<img src="https://i.ibb.co/mr6bQVWm/Screenshot-2025-02-25-091314.png" alt="build" width=800 style="display: block; margin: 0 left;">

# See also

[Tutorial: How to SDK Creating Custom Weapon](https://docs.google.com/document/d/1miWuhu9Jgr-P_HKsAaYMxiz3i4wbq7hn1FSDGEJzo1A/)
[WTT Discord server](https://discord.gg/Nz6VX78xRa)


