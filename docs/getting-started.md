---
title: Getting started
layout: docs
order: 1
---

Oinky is a static site generator. Like most static site generators, Oinky utilizes the power of Markdown and a templating language to help you create websites with ease. But, unlike most static site generators, Oinky also allows you to create complex websites by creating data-sets from your Markdown content using a built-in DSL. Sounds cool, right?

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

Once you've installed Oinky, simply navigate to your project' directory and run `oinky`. Yup, that's it. If you installed Oinky locally then you have to run oinky as `./oinky` relative to where it is saved. Once running it, it will compile all of the available content in that directory into the `/public` directory which you can then readily host somewhere like [Netlify]() or [Vercel](). 

## Watch

When developing a website it might get annoying having to constantly run Oinky again, for that reason Oinky comes built-in with a watcher that will re-compile your website whenever it detects a change. 

To run Oinky with a watcher, call it as `oinky watch`.