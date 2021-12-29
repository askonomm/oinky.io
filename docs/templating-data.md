---
title: Templating data
layout: docs
order: 7
---

No matter if you are inside of a [partial](/docs/partials), a [layout](/docs/layouts) or a [page](/docs/pages), you can make use of templating data that's made ready for you, and that you can also create yourself. 

## Pre-set templating data

Pre-set data is data that is always there, regardless if you create your own data or not. This data is as follows:

- `meta.{key}` - Meta-data for the currently in-scope [content](/docs/content)
- `entry` - HTML entry for the currently in-scope [content](/docs/content) or [page](/docs/pages)
- `slug` - URL slug for the currently in-scope [content](/docs/content) or [page](/docs/pages)
- `path` - full location path for the currently in-scope [content](/docs/content) or [page](/docs/pages)
- `time_to_read` - Time to read (in minutes) for the currently in-scope [content](/docs/content) or [page](/docs/pages)

## Creating custom static templating data

If you want to create your own data tha would be available for you inside any of the Handlebars templates, you can create a `site.json` file in the root directory of your project and put anything you want in there, and that would be then available to you as `site.{key}`. 

For example, given this `site.json` file:

```json
{
    "title": "My awesome website",
    "links": {
        "twitter": "https://twitter.com/askonomm"
    }
}
```

You can access this data in your Handlebars template files as either `{{site.title}}` or `{{site.links.twitter}}`. Do note however that this data will not be available like that from nested structures such as `{{#each}}{{/each}}` loops where you have to prepend `@root` to it to be able to display it from higher up in the hierarchy, meaning you would do `{{@root.site.title}}` instead.

## Generating custom templating data dynamically

You might also want to generate templating data dynamically - from your Markdown content. Since Markdown content can contain meta-data, there is a lot you can come up with. To create templating data from your Markdown content, simply create a `content.json` file in the root directory of your project. 

An example, full usage of the file would look like this:

```json
[
    {
        "name": "blog_posts",
        "from": "posts",
        "order": "desc",
        "sort_by": "meta.date"
    },
    {
        "name": "blog_archive",
        "from": "posts",
        "order": "desc",
        "sort_by": "meta.date",
        "group_by": "meta.date|year",
        "group_by_order": "asc"
    }
]
```

In the above example what happens is that Oinky will create variables named `blog_posts` and `blog_archive`, which you can then access in your [partials](/docs/partials), [layouts](/docs/layouts) and [pages](/docs/pages) as `content.blog_posts` and `content.blog_archive`. Yup, just prepending the word `content` to it with a dot (.) delimiter.

### `name` (required)

The `name` property lets Oinky know what to call this data inside your Handlebars templates, so that you could access it using `content.{name}`. 

### `from` (required)

Specifying `from` is mandatory in order for Oinky to know from which directory to read the data from. For example, let's say you want to get data from `documents/essays/general`, then you would specify `from` as that. Remember that Oinky reads this data recursively, so it will also get any content from any directories from within that directory.

### `order`

You can order data in either ascending (`asc`) or descending (`desc`) order, by specifying that in the `order` property. 

### `sort_by`

You can sort data by either `slug`, `entry`, `path`, `time_to_read` or any meta item you have in your Markdown content via `meta.{key}`. 

### `group_by`

You can group content by either `slug`, `entry`, `path`, `time_to_read` or any meta item you have in your Markdown content via `meta.{key}`. There is a special case for `meta.date`, however. You can pass an additional modifier to group by year, month or day, by doing either `meta.date|year`, `meta.date|month` or `meta.date|day`. 

### `group_by_order`

Now while you can order the contents of each group using the `order` and `sort_by` property explained above, you can also order the groups themselves, using `group_by_order`. This can be either ascending (`asc`) or descending (`desc`).