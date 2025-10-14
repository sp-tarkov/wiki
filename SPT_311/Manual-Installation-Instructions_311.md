---
title: Manual Installation Instructions for SPT 3.11
description: 
published: true
date: 2025-10-14T01:33:40.518Z
tags: 
editor: markdown
dateCreated: 2025-10-10T18:56:40.239Z
---

> This page applies to SPT version `3.11`
{.is-info}

1. You will need to download a patcher to downgrade your game files. 
  Each version of SPT requires a specific version of EFT. `SPT 3.11.4` requires `EFT 16.1.3.35392`. The following downgrade is currently available:
  [](PATCHER)[16.9.0.40087 to 16.1.3.35392](https://spt-legacy.modd.in/Patcher_16.9.0.40087_to_16.1.3.35392.7z)
2. Download Escape from Tarkov from: https://www.escapefromtarkov.com
3. After installing EFT, **copy** the Tarkov installation folder to another location
4. Rename the folder to something like `SPT311`
    - Do NOT copy to a protected/OneDrive location, e.g. `Desktop` or `Program Files`
    - Do NOT delete the original Tarkov installation to save space, it must remain in the original install location for SPT to function
5. Extract the contents of the downgrade patcher into your `SPT311` folder, and run `patcher.exe`
    - Make sure to use the tool [7Zip](https://www.7-zip.org/) to do this, the built-in Windows tool will not work correctly.
    - If live is newer than the above downgrade patch, **please wait**, a new downgrade patch will be created eventually.
6. Download the `SPT 3.11.4` release archive [from here](https://github.com/sp-tarkov/build/releases/download/3.11.4/SPT-3.11.4-35392-96e5b73.7z)
7. Extract the contents of the SPT release archive into your `SPT311` folder.
8. Open your `SPT311` folder
8. Run `SPT.Server.exe` and wait for it to start. `Server is running` in green will appear when it has finished loading.
9. Start `SPT.Launcher.exe`
10. Enter any username into the username box (NOT the same details as your live account)
11. Click `Login` and choose the edition you want (EoD, Standard, Easy Start, etc...)
12. Click `Start Game`