---
title: Client Modding Quick Guide
description: A basic guide on getting started with Client mods.
published: true
date: 2025-12-16T16:27:35.797Z
tags: modding
editor: markdown
dateCreated: 2025-10-14T00:46:02.669Z
---

> This page applies to any SPT version
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
2. Install .NET runtime (miniumum version: 6.0, latest should work fine) [downloads](https://dotnet.microsoft.com/en-us/download/dotnet).
3. Install [dnSpy](https://github.com/dnSpyEx/dnSpy/releases/latest).
	- Scroll to the bottom of that release to the `Assets` section, and select either `dn-spy-net-win32.zip` or `dn-spy-net-win64.zip` depending on your system.
	- Create a `C:\dnSpy` folder, then drag the contents of the zip you downloaded into that folder.
	- Optionally, right click `dnSpy.exe` and create a shortcut, then place it on your desktop.

## Step 1: SPT development install setup

1. Create a fresh SPT install to use for development.
2. Create a Development folder to hold your mod projects in the root directory of your new SPT install e.g.: `[spt install folder]/Development` .
	- Doing this is nice because when it is time to update your mod to a new SPT version, you can just paste the whole Development folder into that install and get to work without needing to update reference paths, etc. (thank Drakia for the idea!).
3. Download the `Mono` version of `BIE 5.X` of [Unity Explorer](https://github.com/sinai-dev/UnityExplorer/releases/latest). Install it like any other client mod.
4. Navigate to `[spt install folder]/BepInEx/config` and open `BepInEx.cfg`, set `LogChannels = all` and `Enabled = true` under the [Logging.Console] section. This will cause the BepInEx console to launch when you launch SPT. All logging done in your mod will appear in this console.
5. Make sure to run your dev install once, all the way to the main menu and then quit. This deobfuscates the assembly.

## Step 2: Export Assembly-CSharp.dll file to view Tarkov’s decompiled source

We do this so we can study the Tarkov source code to see what we may want to change, as well as where to change it. I suggest creating a Visual Studio project to contain the decompiled source. Fortunately, dnSpy has the ability to do this for us!


1. Create a folder to store your decompiled source. I suggest naming it after the SPT version the source is for, to differentiate it from future assemblies you decompile when SPT updates to a new EFT client version e.g.: `SPT400_assembly` .
2. Open dnSpy.
3. Go to `File > Open` and navigate to this path: `[game folder]/EscapeFromTarkov_Data/Managed`, select the `Assembly-CSharp.dll` file and click `Open`.
4. Once the `Assembly-CSharp.dll` file is open, you should see it in dnSpy. You can look through the code inside dnSpy if you prefer, but I suggest creating a Visual Studio project to hold it. You can do so by going to `File > Export to Project…` then selecting the folder we created in step 1.
5. Open the project! Run `Assembly-CSharp.sln` in the project folder dnSpy created to do so.

You can use <kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>F</kbd> to search the entire solution for code. Go ahead and try and search for something like “Jump” or “Door” to see what you can dig up!

## Step 3: Mod project setup

0. Set up and log in to a GitHub account (https://github.com/), then head to [the example repo](https://github.com/Jehree/SPTClientModExamples).
1. Click the green `Use this template > Create a new repository` button at the top right of the example repo's GitHub page.
2. Use something like GitBash to clone your new repo into a folder on your computer (https://git-scm.com/downloads) or download it manually with `Code > Download ZIP`.
   * Make sure you are cloning **YOUR** new repo, not the example repo itself.
3. Rename the following files from `SPTClientModExamples` to your new mod name:
    * Folder the project is in
    * **.csproj** file
    * **.sln** file
4. Open the **.sln** file with a text editor, <kbd>CTRL</kbd> + <kbd>F</kbd> for `SPTClientModExamples` and replace ll with your new mod name.
5. Open the **.csproj** file with a text editor, <kbd>CTRL</kbd> + <kbd>F</kbd> for `SPTClientModExamples` and replace all with your new mod name.
6. Open your solution by double clicking your **.sln** file, double click **Plugin.cs**.
7. Press <kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>F</kbd>, click Replace in Files:
    * make sure `Look in` is set to `Entire solution`
    * in `Find` field, enter: `SPTClientModExamples`
    * in `Replace` field, enter your new mod name
    * click `Replace All` in bottom right, click yes if prompted 

## Step 4: Start coding!

1. Play around with the examples from [the example repo](https://github.com/Jehree/SPTClientModExamples) to get your hands dirty!
2. Once you’re ready to test, go to `Build > Build Solution` or press <kbd>F6</kbd> to build your mod. If your project solution is correctly placed in `YourSPTInstall/Development`, the compiled plugin should be automatically copied into `BepInEx/plugins`, so all you should have to do is build and launch the game to test.
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
[Modding Resources](/modding/Modding_Resources)