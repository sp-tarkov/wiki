---
title: Style Guide
description: Keep a consistent style across the Wiki.
published: true
date: 2025-08-28T19:47:10.949Z
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
# Largest title
Is usually too big for any use. If a section on a page is so separate from the others, consider making it a separate page instead.

## Second largest
The perfect size for section headings

### Third largest 
To separate larger lists which might required external linking to. Use instead of ordered/unordered lists.

#### Forth largest 
It's too small to work as a heading. Same applies for all the other titles.

##### Fifth largest
###### Sixth largest
```

## Lists and bulletpoints

Ordered lists should be used for series of steps, while unordered lists should be used in all other cases.
Full stops should be used if a bulletpoint is a longer sentence, however this determination is mostly made by how it looks on the page.

- Apples
- Bananas are yellow
- Oranges are orange and are the fruit of a tree.

## Images

Images are best handled by using HTML:

`<img src="/image_filename.png" alt="image title" width=400 style="display: block; margin: 0 auto;">`

This will imbed the image in the middle of the screen, with a width of 400 px. Use 600 for images with smaller text.
However, this will have the unfortunate effect of putting the image directly under the text with no space in-between. Use the non-breakable space's HTML code of `&nbsp;` to seperate images from non-header text surrounding it. Header text doesn't need its inclusion as it already seperates itself from images.

## Bold, italics, underlines and codeblocks
The most subjective section, use of bold and italicised text should be standarised across the wiki.
- **Bold** text should be used either to highlight very important information in the middle of a sentence, or to highlight key words that, for example, are verbatum of what's in-game:
  - You should always **read the mod pages** of the mods you're installing.
  - You should disable **V-Sync** in your in-game graphics settings.
- **Italics** are best reserved for key information in a sentence