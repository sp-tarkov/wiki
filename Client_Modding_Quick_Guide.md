---
title: Client Modding Quick Guide
description: A basic guide on getting started with Client mods.
published: true
date: 2025-10-14T01:01:09.758Z
tags: guide, mods
editor: markdown
dateCreated: 2025-10-14T00:46:02.669Z
---

> This page applies to SPT versions: Any
{.is-info}

In order to write client mods for SPT (or any other Unity game with BepInEx) you will need to know how to program in C#. See the resources section to get started if you are new to programming.

## Resources:
- [C# Learning resource](https://dotnet.microsoft.com/en-us/learn/csharp)
- [BepInEx docs](https://docs.bepinex.dev/)
- [Harmony 2 docs](https://harmony.pardeike.net/articles/intro.html)
- [Client mod examples repo](https://github.com/Jehree/SPTClientModExamples)

## Step 0: Installing needed programs

1. Install [Visual Studio](https://visualstudio.microsoft.com/)
	- Click `Download Visual Studio`.
	- Once the installer is downloaded, run it. Click `Available` at the top, then click `Install under Visual Studio Community 2022`.
	- Scroll down under the `Workloads` tab until you see `Game development with Unity`. Check the box next to that workload, and click `Install` in the bottom right.
2. Install [.NET 4.7.1 Framework (runtime version)](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net471).
3. Install [dnSpy](https://github.com/dnSpyEx/dnSpy/releases/latest).
	- Scroll to the bottom of that release to the `Assets` section, and select either `dn-spy-net-win32.zip` or `dn-spy-net-win64.zip` depending on your system.
	- Create a `C:\dnSpy` folder, then drag the contents of the zip you downloaded into that folder.
	- Optionally, right click `dnSpy.exe` and create a shortcut, then place it on your desktop.

## Step 1: SPT development install setup

1. Create a fresh SPT install to use for development.
2. Create a Development folder to hold your mod projects in the root directory of your new SPT install e.g.: `[game folder]/Development` .
	- Doing this is nice because when it is time to update your mod to a new SPT version, you can just paste the whole Development folder into that install and get to work without needing to update reference paths, etc. (thank Drakia for the idea!).
3. Download the `Mono` version of `BIE 5.X` of [Unity Explorer](https://github.com/sinai-dev/UnityExplorer/releases/latest). Install it like any other client mod.
4. Navigate to `[game folder]/BepInEx/config` and open `BepInEx.cfg`, set `LogChannels = all` and `Enabled = true`. This will cause the BepInEx console to launch when you launch SPT. All logging done in your mod will appear in this console.
5. Make sure to run your dev install once, all the way to the main menu and then quit. This deobfuscates the assembly.

## Step 2: Export Assembly-CSharp.dll file to view Tarkov’s decompiled source

We do this so we can study the Tarkov source code to see what we may want to change, as well as where to change it. I suggest creating a Visual Studio project to contain the decompiled source. Fortunately, dnSpy has the ability to do this for us!


1. Create a folder to store your decompiled source. I suggest naming it after the SPT version the source is for, to differentiate it from future assemblies you decompile when SPT updates to a new EFT client version e.g.: `SPT400_assembly` .
2. Open dnSpy.
3. Go to `File > Open` and navigate to this path: `[game folder]/EscapeFromTarkov_Data/Managed`, select the `Assembly-CSharp.dll` file and click `Open`.
4. Once the `Assembly-CSharp.dll` file is open, you should see it in dnSpy. You can look through the code inside dnSpy if you prefer, but I suggest creating a Visual Studio project to hold it. You can do so by going to `File > Export to Project…` then selecting the folder we created in step 1.
5. Open the project! Run `Assembly-CSharp.sln` in the project folder dnSpy created to do so.

You can use <kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>F</kbd> to search the entire solution for code. Go ahead and try and search for something like “Jump” or “Door” to see what you can dig up!

## Step 3: Visual Studio mod project setup

Note: If you would prefer to copy the SPTClientModExamples project and rename it instead of making a new one from scratch, skip step 3 and 3.1 and follow the steps in the README in the repo instead: https://github.com/Jehree/SPTClientModExamples

1. Open Visual Studio, head to `File > New > Project`.
2. Select `Class Library`. Make sure it is the one for `C#` development.
3. Set the Project name to the name of your mod (this can be a little annoying to change later, FYI).
4. Set the Location to the path to the Development folder you just created.
5. Check the Place solution and project in same directory box.
6. Set the Framework to `.NET Standard 2.1`, click `Create` in the bottom right.
7. Rename the single `.cs` file in your project to `Plugin.cs`, and create a `Patches` folder.
8. Double click `Properties` on the left in the `Solution Explorer` area, and click on `Build Events`.
9. Paste the command below into the `Post-build event command line` box, and set `Run the post build event` to `Always`.
	- Command: copy `"$(TargetPath)" "$(ProjectDir)\..\..\BepInEx\plugins\$(TargetFileName)"`
	- Why do this?: This will automatically copy your mod’s .dll file into `BepInEx/plugins` when you build it with `Build > Build Solution`, so you don’t have to manually place it there.
	- NOTE: If you build your mod without making any changes to the code, the copy will not happen. If you want to force it to copy, manually delete your mod’s `.dll` file from `BepInEx/plugins`, make a small change to your code like adding a comment, then build it.

&nbsp;
<img src="/cmqg/post_build_command_line.png" alt="post build command line" width=600 style="display: block; margin: 0 auto;">

## Step 3.1: Adding references to `.csproj` file

We need to add some references so that classes in the EFT source code as well as some helper SPT classes can be referenced in your mod. Drakia has a convenient list of starting references, so we are going to add those. Do note that these are not all the refs that you can use. You can reference any `.dll` file in `EscapeFromTarkov_Data/Managed`, so feel free to add more if needed!

1. Make sure your mod project is closed.
2. Navigate to `[game folder]/Development/[your mod name]`, and open the `.csproj` file with a text editor (Notepad is fine).
3. Scroll to the bottom of the file.
4. Replace the `</ItemGroup>` tag and contents as shown below in the screenshot with [Drakia’s refs](https://github.com/Jehree/SPTClientModExamples/blob/main/StarterRefPaste.txt).

&nbsp;
<img src="/cmqg/drakia_refs.png" alt="drakia refs" width=600 style="display: block; margin: 0 auto;">

## Step 4: Start coding!

1. Head to [this repo](https://github.com/Jehree/SPTClientModExamples) and use the examples there to get your hands dirty!
2. Once you’re ready to test, go to `Build > Build Solution` or press <kbd>F6</kbd> to build your mod. It should be automatically copied into `BepInEx/plugins`, so all you should have to do is build and launch the game to test.
3. Have fun!



## Credit to the cool peeps:

To those who have helped me learn all this shiz and gave me feedback on this doc, you guys ROCK. Thank you so much!

DrakiaXYZ
Cj
Arys
Kiki
mpstark
Tyfon

# See also
[Modding Resources](/Modding_Resources)