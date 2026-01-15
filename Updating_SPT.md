---
title: Updating SPT
description: Learn how to update your SPT installation.
published: true
date: 2026-01-15T18:58:18.778Z
tags: guide
editor: markdown
dateCreated: 2025-08-09T12:01:16.553Z
---

> This page applies to any SPT version
{.is-info}

## Version numbers
SPT follows the [Semantic Versioning](https://semver.org/) schema for its version numbers, which works as follows:

`SPT Version X.Y.Z`

`X` = Major update
- A large refactor of SPT or EFT
- Requires reinstalling SPT anew
- Old mods **won't work**
- Unmodded old profiles *might* work

`Y` = Minor update
- A new version of EFT is being used
- Requires reinstalling SPT anew
- Old mods **won't work**
- Unmodded old profiles *might* work

`Z` = Patch/Hotfix
- Bug fixes for the previous Minor version
- Generally doesn't require a reinstall
- Generally works with mods made for the previous hotfix version
- Old profiles **will work**
- **Can be used to update your SPT if it's on the same Minor version**

You can always check if a hotfix patch will be compatible with your installed mods on the [Release page](<https://github.com/sp-tarkov/build/releases>):
&nbsp;
<img src="/patch_compat.png" alt="Direct Download" width=400 style="display: block; margin: 0 auto;">
<div style="margin-top: 10px;"></div>
<div style='text-align: center;'>
Example of the compatibility section for SPT 3.11.3.
</div>

## Updating to a new hotfix patch

> This method can only be used to update to a new hotfix patch. An update from ex. `3.11.4 > 4.0.0` requires a new install of SPT.
{.is-warning}


1. Download the SPT files from the Direct Download section at the **bottom** of the [Release page](https://github.com/sp-tarkov/build/releases) (requires [7zip](https://www.7-zip.org/)).
<div style="margin-top: 10px;"></div>
<img src="/direct_download.png" alt="Direct Download" width=400 style="display: block; margin: 0 auto;">

2. Close your game, launcher, and server.
3. Copy contents of the 7z file into your **existing** folder, **overwrite all files**.
4. **Update all of your mods to their latest release versions**.
 - Mods made for previous hotfix versions should work on the latest version. Those that don't might have received an update to address that.
  - You can use a tool like [Check Mods](<https://forge.sp-tarkov.com/mod/2471/check-mods>) to see which of your mods require updating.
> This will only overwrite base SPT files. It will __not__ overwrite or remove your profile(s), mods or mod configs.
{.is-info}

# See also
[New to SPT? Start here!](/Beginners_Guide)
[Installing SPT](/Uninstalling_Mods)