---
title: Content
layout: docs
order: 2
---

Content in Oinky comes in the form of Markdown files. Both `.md` and `.markdown`  file extensions are supported. An example content file looks like this:

```markdown
---
title: Hello, world
date: 1992-09-17
---

Hi there, **world**.
```

## Meta-data

In the top of the file, between three hyphens (-), sits meta-data. Each meta-data item is separated from other meta-data items by a line break, and within each meta-data item there are two things: keys and values. In the above example a key would be either `title` or `date`, and the value for each would be `Hello, world` and `1992-09-17`, respectively. Keys and values are separated by a colon character (:). You can have as much meta-data as you wish.

This meta-data can then be utilized inside your [partials](/docs/partials), [layouts](/docs/layouts) and [pages](/docs/pages) via [templating data](/docs/templating-data).

## Markdown

Below the meta-data is your Markdown content. The Markdown content follows [CommonMark](https://spec.commonmark.org) and [Github Flavored Markdown](https://github.github.com/gfm/) spec.