---
title: How to Contribute
description: Learn how to contribute to the SPT Wiki.
published: true
date: 2025-10-14T01:37:55.434Z
tags: guide
editor: markdown
dateCreated: 2025-10-12T15:47:12.223Z
---

## Wiki.js
[Wiki.js](https://js.wiki/) is the framework the SPT Wiki uses. However, this framework currently does not directly support edit requests.
Trusted community members are given the ability to directly edit the Wiki. You can leave suggestions in the [`#website-wiki`](https://discord.com/channels/875684761291599922/1426941224324960266) channel on our [Discord server](http://discord.sp-tarkov.com/).
If instead you'd like to submit or edit a page, you'd need to make a pull request on the [Wiki's Github page](<https://github.com/sp-tarkov/wiki/>).

## Pull requests
To set up a pull request, first you'll need to create a fork of the Wiki. 
1. On the [Wiki's Github page](<https://github.com/sp-tarkov/wiki/>), simply click the `Fork` button.
2. This will create a fork, or a seperate copy, of the Wiki under your control. You will be able to add or edit pages freely to it.
3. Once you're happy with the changes you made, you'll be able to create a pull request. That is a request to merge the changes you made in your fork to the actual Wiki.
4. On your fork's `Pull requests` page, press the `New pull request` button. Github should automatically select the correct repositories. It will let you know if the pull request is `Able to merge`.
5. Press `Create pull request`. If approved, your changes will be made to the SPT Wiki.

## Markdown
The SPT Wiki can use many different types of formatting. The easiest to use is [Markdown](https://daringfireball.net/projects/markdown/). You can see which Markdown features are supported on the [Wiki.js documentation page](https://docs.requarks.io/editors/markdown). There are many resources online for Markdown, however it's entirely doable in just Notepad or Github's text editor.

**Note**: If you're submitting a new page, the file must have the `.md` file extension, and include this header at its beginning:

```
---
title: title
description: summary
published: true
date: 2025-10-12T12:00:00.000Z
tags: 
editor: markdown
dateCreated: 2025-10-12T12:00:00.000Z
---
```
Only the `title` and `description` fields need to be edited. The `date` and `dateCreated` fields should be updated to the date of your page's creation, but it's not stricly necessary. Already created pages have this header included if you'd like to see examples.

# See also

[Style Guide](/Style_Guide)