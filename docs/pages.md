---
title: Pages
layout: docs
order: 4
---

By now we already know that you can create website pages using [content](/docs/content) and [layouts](/docs/layouts) together and utilizing all the power of Markdown and meta-data to do so, but what if you wanted more power? What if you wanted to create custom files entirely such as HTML pages? RSS feeds? Sitemap XML feeds? Anything, really? Well, then you're in the right place, because Pages allow you to do just that.

You see, you can create a Handlebars files outside of the special `_partials/` (reserved for [partials](/docs/partials)) and `_layouts/` (reserved for [layouts](/docs/layouts)) directories as well, and you can do some pretty cool stuff with that. 

## Creating a index page

By default Oinky has no home page created for you, leaving that part entirely up to you. And you can create a home page, or what is more correctly called an "index" page, using Handlebars templates. In this case you will simply create a `index.html.hbs` file in the root directory of your project, fill it with anything you want - such as [partials](/docs/partials) or [templating data](/docs/templating-data) - and then run Oinky, and this file will end up saved to `public/index.html`.

You see? All Oinky does is just remove the `.hbs` extension from the file, and save the rest as is, in the directory that the Handlebars file is in - so if it's in a root directory like in this example, it will be compiled into the root directory of the created site - the `/public` directory, and you will have your home page!