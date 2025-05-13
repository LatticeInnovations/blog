---
description: Soura Bhattacharyya | May 13, 2025
cover: ../.gitbook/assets/arun-sharma-rTAdnqmYS40-unsplash.jpg
coverY: 0
layout:
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# If you want to type, then retype

It is ironic that I am publishing this post on a site hosted via GitBook. Because it is about their direct competitor, [Retype](https://retype.com/).

I spent several weeks exploring different tools for publishing static sites. My criteria were as follows:

1. Inexpensive
2. Easy for me to understand and operate, i.e. designed primarily for a writer, not a coder
3. Easy to manage content via GitHub, where all of our documentation sits

I had already used GitBook to set up my personal blog and a product website ([www.neoport.org](https://www.neoport.org/)). The free plan worked great for a site updated by a single contributor, but the paid tiers that enabled collaboration were expensive.

Chanced across Retype thanks to a Reddit post. Used it for our open-source platform, [Agni](https://agni.thelattice.in). Loved it. Here is why.

### Git all the way—with you in control&#x20;

Retype takes markdown content as-is, and builds a `.retype` html directory within your repository. It then creates a separate branch that is published. You have full control over content at all times.

If you already follow pull-request discipline, then garnering contributions from the entire team is simple. And if you use a paid plan, then save the license as a repo secrect. No need to share passwords.

### Build and run locally

This is a huge bonus over GitBook. Retype can be built and run locally—a great way to review changes before publishing them, especially during major overhauls. Once changes are merged to the `main` branch, GitHub actions rebuilds and publishes the website.

The local build feature is so useful that I am considering adding Retype to internal projects, just to have a better way to read through docs. &#x20;

### Generous free-tier and pocket-friendly pricing

* Websites up to 100 pages are free.&#x20;
* All the essential features, including css customization,  are free. The paid tier gives you ability to control visibility of pages and sections.&#x20;
* You can test drive the paid plan locally, to see if it right for you.
* Pricing is based on projects, not users. Yup, you read that correctly.
* A single license, mapped to a sub-domain, is free for lifetime. Updates are limited to three years.

### Attention to detail

Some of these configurations are paid. All of these configurations are examples of design done right:

* You can set different dark and light logos for your site. Check out [Agni](https://agni.thelattice.in); pay attention to the top-left icon as you switch between dark and light mode.
* You can set different heading depths on the right-side navbar. The default (available with the free plan) is H2 to H4.
* Octicons available as a default library to spruce up buttons and side navigation.
* Granular control over side nav—sequence of items, grouping. open/ closed state, visibility (on paid plans).
* Simple extensions to standard markdown syntax, to provide features like accordions and tabs.

So, if you type, try [Retype](https://retype.com/).



_Photo credit:_ [_Arun Sharma_](https://unsplash.com/@arunwithideas?utm_content=creditCopyText\&utm_medium=referral\&utm_source=unsplash) _on_ [_Unsplash_](https://unsplash.com/photos/black-typewriter-rTAdnqmYS40?utm_content=creditCopyText\&utm_medium=referral\&utm_source=unsplash)
