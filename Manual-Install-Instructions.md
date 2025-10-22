---
title: Manual Install Instructions
description: 
published: true
date: 2025-10-22T00:51:55.951Z
tags: 
editor: markdown
dateCreated: 2025-10-21T23:42:29.093Z
---

You should really [use the installer](https://hub.sp-tarkov.com/files/file/672-spt-installer/), but if you insist...

1. Download Escape from Tarkov from: https://www.escapefromtarkov.com
2. After installing EFT, **copy** the Tarkov installation folder to another location
3. Rename the folder to something like `SPTxxx` (`xxx` being the version you are installing, for example `SPT401`)
    - Do NOT copy to a protected location, e.g. `Desktop` or `Program Files`
    - Do NOT delete the original Tarkov installation to save space, it must remain in the original install location for SPT to function
4. **If necessary**, download and run a downgrade patcher:
    - If the SPT version you are installing matches live, **DO NOT** run the downgrade patcher. 
    - Each version of SPT needs a specific version of EFT, this version is noted on the Release page of the SPT version.
    - **If necessary**, download the corresponding patcher for your version of Tarkov: [Download patchers here](https://spt-mirror.refringe.com/patchers/).
    - Make sure to use the tool [7Zip](https://www.7-zip.org/) to extract this archive, the built-in Windows tool will not work correctly.
5. Download the SPT release archive under the `Direct Download` section of the latest [release page](https://github.com/sp-tarkov/build/releases/latest).
6. Extract the contents of the SPT release archive into your `SPTxxx` folder.
7. Open your `SPTxxx` folder, then the nested `SPT` folder inside of it
8. Run `SPT.Server.exe` and wait for it to start. `Server has started` in green will appear when it has finished loading.
9. Start `SPT.Launcher.exe`
    - You can create shortcuts for these two programs and move the shortcuts to the parent `SPTxxx` directory to make future launching easier
10. Enter any username into the username box (NOT the same details as your live account)
11. Click `Login` and choose the edition you want (EoD, Standard, Easy Start, etc...)
12. Click `Start Game`