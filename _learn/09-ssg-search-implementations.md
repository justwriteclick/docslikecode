---
title: "Evaluating Static Site Generator search options"
layout: page
image:
  path: /images/learn/ssg-search-options.png
  thumbnail: /images/learn/ssg-search-options400x225.png
---

Most static site generators provide a browser-side search capability, where the list of indexed keywords for search are built at the same time as the output. Learn more about considerations for each SSG in the following sections.

### Jekyll implementation for search within the site

For Jekyll and the [Minimal Mistakes theme](https://mmistakes.github.io/minimal-mistakes/), the theme author has implemented Lunr.js as a browser-side search tool. The search works fast, and when a user types in a search term, it pre-fills with suggestions in the search form. The JSON file used for the search terms should be generated each time the site is re-built.

### Sphinx search implementation

For Sphinx, the default search engine creates a `searchindex.js` file that depends on cached doctree files being built each time the site is built. The build implementation goes through each document and pulls out words for search. Then, the theme uses a web form that calls the `searchindex.js` file when a user fills out the form. Currently the system does not have a way to substitute another browser-side search implementation, but the developers are considering it in a future Sphinx release based on [discussion in this GitHub Issue](https://github.com/sphinx-doc/sphinx/issues/3812).

### Hugo search options

For Hugo, the search engine included with the "Learn" theme can be configured for Lunr.js. To configure the theme to use the `lunr.js` [JavaScript search engine](https://lunrjs.com/), add these lines to the `config.toml` file and rebuild.
```
[outputs]
home = [ "HTML", "RSS", "JSON"]
```

You can also configure Algolia, a software-as-a-service (SaaS) search solution, in Hugo, according to this [blog post](https://forestry.io/blog/search-with-algolia-in-hugo/).

## Evaluating other options

* [Evaluating Static Site Generator themes](https://www.docslikecode.com/learn/07-evaluating-ssg-themes/)
* [Evaluating table layouts and formatting](https://www.docslikecode.com/learn/08-evaluating-table-layouts/)
