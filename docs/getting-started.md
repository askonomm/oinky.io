---
title: Getting started
layout: docs
order: 1
---

Oinky is a static site generator. Like most static site generators, Oinky utilizes the power of Markdown and a templating language to help you create websites with ease. But, unlike most static site generators, Oinky also allows you to create complex websites by creating data-sets from your Markdown content which you can then use in your templates. Cool, right?

## Install

To get started, simply install Oinky by running the following command in your terminal:

```shell
curl -s -L https://oinky.io/install.sh | bash -s
```

If you want to install Oinky only locally, then run this command instead:

```shell
curl -s -L https://oinky.io/install.sh | bash -s -- -l
```

## Run

Once you've installed Oinky, simply navigate to your project' directory, type `oinky` and press enter. Yup, that's it. If you installed Oinky locally then you have to run oinky as `./oinky` relative to where it is saved. Once running it, it will compile all of the available content in that directory into the `/public` directory which you can then readily host somewhere like [Netlify](https://www.netlify.com) or [Vercel](https://vercel.com). 

### Example directory structure

Oinky is very flexible in most part so you can create your website just how you'd like it. An example directory structure for an Oinky site is as follows:

- **_partials/**
    - header.hbs
    - footer.hbs
    - sidebar.hbs
- **_layouts/**
    - default.hbs
    - post.hbs
- **blog/**
    - hello-world.md
- index.html.hbs

In the above example you have special folders that start with an underscore (_) where Oinky keeps special files, such as [partials](/docs/partials) and [layouts](/docs/layouts). Everything else is entirely up to you. For example, the `blog/hello-world.md` file will be compiled into `/public/blog/hello-world/index.html` file. And the `index.html.hbs` file you see? That would be compiled into `/public/index.html`. 

So, Markdown files (.md) would get their own directory and an `index.html` file within that directory, whereas Handlebars files (.hbs) would be compiled into the same directory they are, and would keep the file name they have, with the `.hbs` suffix removed, thus allowing you to create whatever type of file you'd like, such as RSS feeds, sitemaps, and so on!

You can read more about [Markdown content here](/docs/content), and [Handlebars pages here](/docs/pages).

## Watch

When developing a website it might get annoying having to constantly run Oinky again, for that reason Oinky comes built-in with a watcher that will re-compile your website whenever it detects a change. 

To run Oinky with a watcher, call it as `oinky watch`.