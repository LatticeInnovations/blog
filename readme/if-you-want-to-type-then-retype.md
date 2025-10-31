---
description: Soura Bhattacharyya | May 13, 2025
cover: ../.gitbook/assets/arun-sharma-rTAdnqmYS40-unsplash.jpg
coverY: 0
---

# If you want to type, then retype

It is ironic that I am publishing this post on a site hosted via GitBook. Because it is about their direct competitor, [Retype](https://retype.com/).

I have used GitBook to set up my [personal blog](https://soura.org), this site, and a product website ([neoport.org](https://www.neoport.org/)). The free plan works great for a single-contributor site, but paid tiers for collaboration were beyond my budget. Or beyond my faux middle-class sensibilities.

So, when faced with the prospect of publishing a large project, I spent several weeks exploring alternatives for publishing static sites. My criteria were—in no particular order:

1. Inexpensive
2. Easy for me to understand and operate, i.e. designed primarily for a writer, not a coder
3. Ability to hide some pages, and password-protect others.
4. Easy to manage content via GitHub, where all of our documentation sits

I chanced across Retype thanks to a Reddit post. Used it for our open-source platform, [Agni](https://agni.thelattice.in). Loved it. Here is why.

### Git all the way—with you in control&#x20;

Retype takes markdown content as-is, and builds a `.retype` html directory within your repository. It then creates a separate branch, which you publish via GitHub pages. You have full control over content at all times.

If you already follow pull-request discipline, then garnering contributions from the entire team is simple. If you use a paid plan, then you save the license key as a repo secret. No need to share passwords.

### Build and run locally

This is a huge bonus over GitBook. Retype can be built and run locally—a great way to review changes before publishing them, especially during major overhauls. Once changes are merged to the `main` branch, GitHub actions rebuilds and publishes the website.

The local build feature is so useful that I we are adding Retype to a [complex internal project](https://www.thelattice.in/projects/ai-platform), just to have a better way to read through docs. &#x20;

### Generous free-tier and pocket-friendly pricing

* Websites up to 100 pages are free.&#x20;
* All the essential features, including css customization, are free. The paid tier gives you ability to control visibility of pages and sections.&#x20;
* You can test drive the paid plan locally, to see if it right for you.
* Pricing is based on projects, not users. Yup, you read that correctly.
* A single license, mapped to a sub-domain, is free for lifetime. Updates are limited to three years.

### Attention to detail

Some of these configurations are paid. All of these configurations are examples of design done right:

* Switch between different logos for dark versus light mode. On the [Agni](https://agni.thelattice.in) site, check out the top-left icon as you switch between dark and light mode.
* Vary heading depths on the right-side navbar. The free plan is limited to the default of H2 to H4.
* Specify language to beautify code snippets, show or hide line numbers, and add line-level highlights.
* Use Octicons to spruce up buttons and side navigation.
* Exercise granular control over the left side nav—sequence of items, grouping, open/ closed state.
* Use markdown-like syntax to pull in UI elements like accordions and tabs.
* If you need cards—something that GitBook provides by default—then create a one-time, customized CSS container.

So, if you type, try [Retype](https://retype.com/).



_Photo credit:_ [_Arun Sharma_](https://unsplash.com/@arunwithideas?utm_content=creditCopyText\&utm_medium=referral\&utm_source=unsplash) _on_ [_Unsplash_](https://unsplash.com/photos/black-typewriter-rTAdnqmYS40?utm_content=creditCopyText\&utm_medium=referral\&utm_source=unsplash)
