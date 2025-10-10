---
title: FAQs 4.0
description: Answers to frequently asked questions about SPT 4.0
published: false
date: 2025-10-10T12:35:08.107Z
tags: 
editor: markdown
dateCreated: 2025-10-10T12:23:08.957Z
---

# SPT 4.0
### Why are there so many files in the new `\SPT` folder?
To allow modders to use method patching, all the DLLs need to be 'loose' and not stored inside the server executable.

### What version of Tarkov is SPT running?
Version `0.16.9.0.40087`, released 2 October 2025.

### Is (insert content here) in SPT now?
Refer to the previous question. If you're curious about something specific, please see the official [Tarkov changelog](<https://escapefromtarkov.fandom.com/wiki/Changelog>).

### Is Labyrinth in SPT?
Yes.

### Is the Softcore wipe in SPT?
No. The Softcore wipe only made changes to the PVP mode. SPT is based off the PVE mode. You can easily recreate it using mods.

### Will 4.0 be updated to include the latest EFT patches?
No. EFT patches made after the release of SPT 4.0 will only be available in SPT 4.1.

### Can I use my profile and mods from 3.11?
***If*** the `3.11` profile was ***un-modded***, yes. Otherwise A new profile will be required. None of your `3.11` mods are compatible.
See the guide on [Updating SPT](/Updating_SPT) for more details.

### I miss 3.11, can I re-download it?
Yes. SPT 3.11 is in Long Term Distribution. However, you will need to manually install it and we offer no support for it.
See [this guide](https://github.com/sp-tarkov/build/wiki/3.11-Manual-Installation-Instructions) for instructions.

### When is (insert mod here) going to update to 4.0?
Nobody knows when certain mods are going to update, not even the authors themselves. Do not pester mod authors about updates to their mods.

# Troubleshooting tips
- Do not install mods until you've launched SPT at least once. Verify your SPT install works, then install mods.
- Do not install out of date mods.
- Do not install multiple mods at once (unless they're dependencies). Install mods one at a time or in small batches. That way when something goes wrong, you'll know exactly what mod is responsible.
- Read mod pages. Not only is it just common courtesy to read the mod page __before__ asking for help, chances are the mod page has exactly the information you need. What the mod does, how to install it, how to use it, and known issues or incompatibility with other mods.

##### "I'm still having issues and it wasn't the last mod I installed, what do I do?" 
Start removing mods one at a time, or if you have a lot of mods, follow the [50/50 Method](<https://wiki.sp-tarkov.com/en/5050-method>).
If none of that helps, then it's time to create a support ticket. Join our [Discord Server](http://discord.sp-tarkov.com/) and read through the [#support-guidelines](https://discord.com/channels/875684761291599922/1172733248317694022) for instructions.

# Old versions of SPT
We do not host old versions of SPT because each SPT version is specifically designed to work with a particular version of EFT. Since EFT is a live service game that receives frequent updates, every SPT version requires a dedicated patcher to downgrade your local EFT installation to the compatible version. Maintaining multiple older SPT versions would necessitate actively maintaining multiple downgrade patchers, which includes updating these patchers after each and every EFT update. Our team simply does not have the time to dedicate to this level of ongoing maintenance.

This decision is firm and will not be changed by further requests or complaints. Repeatedly asking or arguing about this will unfortunately result in administrative action.

**HOWEVER**, we are pleased to announce that the SPT 3.11 release has been designated as a Long-Term Support (LTS) version. This means it will be maintained and available for download (along with its corresponding downgrade patcher) for an extended period.

# See also
[Known EFT Issues](/Known_EFT_Issues)