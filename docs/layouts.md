---
title: Layouts
layout: docs
order: 3
---

While you can create as much [content](/docs/content) as you want without specifying a layout for the content items, and you can use that content in all of your [pages](/docs/pages), [partials](/docs/partials) and layouts using [data creation](/docs/creating-data), if your goal is to create Markdown content that would end up as individual web pages then you want to attach a layout to that Markdown content.

## What is a layout?

A layout is a Handlebars template file that determines how your Markdown content should be displayed, and allows you to design your content however you see fit using [partials](/docs/partials) and [helpers](/docs/helpers). Layouts live inside the special `_layouts/` directory.

## Creating a layout

For example, say you wanted all of your blog posts to have the `post` layout, then you'd create your blog post' Markdown file looking something like this:

```markdown
---
title: Hello, World
date: 2021-12-26
layout: post
---

Hi there, world!
```

You see that meta-data item called `layout`? It's a reserved meta-data item that Oinky will read in order to know what Handlebars layout to render your Markdown content with.

Now let's go ahead and create a `post.hbs` file inside of the special `_layouts/` directory, and let's make it look something like this:

```handlebars
{{>header}}

<h1>{{meta.title}}</h1>

{{format_date meta.date "%Y-%d-%m}}

{{{entry}}}

{{>footer}}
```

There's a lot of things happening in that Handlebars layout file, so let's break it down. Firstly, you notice words wrapped within curly brackets, two of them on each side - those signify rendering things in Handlebars. For more precice info on Handlebars, I recommend you go read the [Handlebars website](https://handlebarsjs.com/guide/). But for now all you need to know is that anything that starts with a right arrow, like `{{>header}}` is a [partial](/docs/partials), which allows you to include other Handlebars files inside your Handlebars files, thus making components reusable and easier to maintain.

Secondly, you notice we have things like `{{format_date}}` which takes two arguments - the date, and a format. What it does it self-explanatory in that it formats the given date with the given format, but we call these things [helpers](/docs/helpers), and we have a few of them.

Thirdly, you see use of `meta.*` and `entry` and so on - where do these things come from and what exactly they are? Well, if you go back to reading about [content](/docs/content), you'll quickly realize that all of those `meta.*` things are actually just your Markdown meta-data, and the `entry` is the Markdown content. The reason why we use 3 curly brackets on each side for Markdown is so that it would render the HTML instead of displaying it.