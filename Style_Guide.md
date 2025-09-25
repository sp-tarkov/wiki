---
title: Style Guide
description: Keep a consistent style across the Wiki.
published: true
date: 2025-09-25T10:36:55.409Z
tags: 
editor: markdown
dateCreated: 2025-08-28T19:25:07.078Z
---

Here's a rudimentary style guide for the Wiki. Nothing here is set in stone or enforced, and it'll see many changes as the Wiki develops.
Its main purpose is to keep the initial set of pages semi-consistent with each other.

## There's no need for initial titles

The Wiki already includes the page's title and short description as part of its page layout. It's unnecessary to add a second title stating the same right underneath it.

## Header sizes

There are 6 different header sizes available. `#` will give you the largest title, while `######` will be the smallest.
Note that using any header will allow for direct linking to that section of a page e.g.: 

https://wiki.sp-tarkov.com/en/Style_Guide#header-sizes

You can copy the direct link to a header by hovering over it, right clicking `¶` and copying the link.

```
# Largest heading
Useful for the "See also" section. If a section on a page could use this header size, consider making it a separate page instead.

## Second largest
The perfect size for section headings. All headings on this page use this size.

### Third largest 
To separate larger lists which might required external linking to. Use instead of ordered/unordered lists.

#### Forth largest 
It's too small to work as a heading. Same applies for the two smaller headings.

##### Fifth largest

###### Sixth largest
```

## Lists and bulletpoints

Ordered lists should be used for a series of steps, while unordered lists should be used in all other cases.
Full stops should be used if a bulletpoint is a longer sentence, however this determination should mostly be made by how it looks on the page.

- Apples
- Bananas are yellow
- Oranges are orange and are the fruit of a tree.

## Images

Images are best handled by using HTML:

`<img src="/image_filename.png" alt="image title" width=400 style="display: block; margin: 0 auto;">`

This will imbed the image in the middle of the screen, with a width of 400 px. Use 600 for images with smaller text.
However, this will put the image directly next to the text with no space in-between. Use the non-breakable space's HTML code of `&nbsp;` to seperate images from non-header text surrounding it. Header text doesn't need it as it already spaces itself from images.

## Text formatting
The most subjective section. Use of bold and italicised text should still be standardised across the wiki.

- **Bold** text should be used either to highlight very important information in the middle of a sentence, or to highlight key words that, for example, are verbatim of what's in-game:
  - "You should always **read the mod pages** of the mods you're installing."
  - "You should disable **V-Sync** in your in-game graphics settings."
- **Italics** are best reserved for key information in a sentence:
  - "If the mod archive has a `BepInEx` or `user` or *both* folders, drag and drop the contents of the archive to the empty space in your SPT folder."
- When you want to differenciate two concepts that share the same name, assign one concept to be **bold** and the other as *italicised*.:
   - "The selected difficulty in the **Pre-Raid Setting** determines which *difficulty classes* are allowed to spawn in your raid:
     - **As in online**: Mix of *Easy*, *Medium*, and *Hard* classes can spawn.
     - **Easy**: Only *Easy* class bots will spawn.
     - **Medium**: Only *Medium* class bots will spawn."
- _Underlines_ should be avoided, as clickable links are also underlined. Bold or italicised text should be used instead.
- `Code blocks` should be used when referring to folder names, file names, values and text strings from config files:
  - "To create a new, empty load order, delete your `user\mods\order.json`."
  - "Set [ALP](https://forge.sp-tarkov.com/mod/1015/alp-algorithmic-level-progression)'s `leveledClothing` to false in `user\mods\AlgorithmicLevelProgression\config\config.json`."
- <kbd>Keyboard keys</kbd> should be used when referring to a keyboard key:
  - "...configure the client-side settings in the <kbd>F12</kbd> menu."