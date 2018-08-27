---
title: "Advanced topics"
image:
  path: /images/so-simple-sample-image-4.jpg
  thumbnail: /images/site-logo.png
---

Themes for static site generators often provide the advanced user experience features such as search. You also analyze the theme to make decisions on the authoring side, such as a table format for large data tables. What about printed outputs, such as PDF? Or versions for the output and the source? Any performance gains you can make with the builds themselves? Themes are one part of this analysis.

These advanced topics may have different underlying implementations with dependencies on parts of the entire system. Some requirements depend on the static site generator, some depend on the theme, some depend on the source format itself. For each topic, let's look at considerations and options for each tool.

Examining themes
Search options
Performance considerations
Print or PDF output
Table layout and formatting
Templating and data-based layouts and lists


## Search options on web site output

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

## Performance considerations

When you start building large documentation sites, or gluing together multiple documentation sets, you might look for performance gains in the build time. Having smaller doc sites helps with this, so that you can build with your static site generator systems in parallel, but also look for incremental builds or ways to measure build times to look for areas where the build is slowed down and then find a root cause for the slower performance.

### Sphinx build performance options

Sphinx has a couple of possibilities for decreasing build times and increasing efficiency of builds.

Sphinx is configured by default to rebuild only new and changed files, rather than building the entire site over again. Use the `-a` flag on the `sphinx-build` command to always write all output files. This setting may help you measure benchmark values for build times.

Trying to keep your number of individual RST files to build to hundreds rather than thousands will naturally make the builds take less time. If you do need thousands of documents, then also be careful with the number of `toctree` directives in use as that overhead can slow down builds.

One option for large doc sets is to let Sphinx use multiple processes, adjusting on its own with the `sphinx-build -j auto` setting, available since the 1.7 release. The `auto` value causes Sphinx to use the number of CPUs for the number of parallel builds.

### Jekyll build time improvements

Jekyll can build only changed files with the incremental build feature, but it is considered experimental in the Jekyll 3.0 release. Use the `-I` or `--incremental` flag on your `jekyll build` or `jekyll serve` commands any time you want to re-build only posts and pages with changes.

```
$ jekyll build --incremental
```

For sites with about a hundred pages, there's less need for performance helpers, but when the site grows to 1,000 pages or more, you should consider only building changed files with the `--incremental` flag.

### Hugo build performance metrics

For Hugo, often the build is so fast you don't have to worry about building incremental changes. That said, Hugo does provide ways to benchmark the site build and to look for metrics for the templates themselves, because it is possible to slow down the build with inefficient template executions. When you run a `hugo` command, you can also use these flags to learn more about build performance:
    * `--stepAnalysis` - Display memory and timing of different steps of the program.
    * `--templateMetrics` - Display metrics about template executions.
    * `--templateMetricsHints` - Calculate some improvement hints when combined with --templateMetrics.

There's also the benchmark command, documented on the [gohugo.io site](https://gohugo.io/commands/hugo_benchmark/). The command builds the site multiple times with various flags set, and analyzes the running process to provide a benchmark for comparison either over time or with various flags set, such as including expired content.

## Print or PDF output

How difficult or straightforward is it to create a print or PDF format? You may want to investigate and test solutions beyond this article, as requirements and print tolerances can vary widely.

### Jekyll PDF options

In the Jekyll Documentation Theme site, Tom Johnson suggests buying a license for Prince XML ($500) in order to create print-ready PDF files with the Jekyll Documentation Theme. The PDF layout and styles are set using CSS. Considering that the only gem solution, [jekyll-pdf](https://github.com/abeMedia/jekyll-pdf), makes PDF files of single pages rather than a collection, the third-party solution is probably the way to go.

### Sphinx PDF output

When you use Read the Docs builds for deployment, you automatically get versioned documentation based on releases, as well as PDF output for the entire site. The PDF formatting is based on [LaTex](https://www.latex-project.org/), an open source typesetting system. It has page numbering, linking, and footnotes.

### Hugo PDF output

Hugo supports many [custom output formats through templates](https://gohugo.io/templates/output-formats/), but as of right now no one has written a series of templates for PDF, based on the discussions in various Issues. ([#1360 Generate concatenated document for Kindle/PDF generation](https://github.com/gohugoio/hugo/issues/1360)) ([#3530 Add alternative rendering format for LaTeX](https://github.com/gohugoio/hugo/issues/3530)). You could also use Prince XML as a solution here, similar to Jekyll.

## Table layout and formatting

One of the most helpful tools when creating tables for Markdown or RST is the Tables Generator at https://www.tablesgenerator.com/markdown_tables. You can draw tables or paste table data and then render the ASCII-based output for pasting into your document source file.

For example, here is an empty five-column table in Markdown, ready for you to insert cell data and spaces.

```
|  |  |  |  |  |
|:-|:-|:-|:-|:-|
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
```

When using Markdown for tables, you do not have access to block-level formatting. If you need a second paragraph, you can use `<br>` inside of a Markdown table. For more complex tables, many people use HTML inside of Markdown files.

For RST, there are several options for table markup that is super simple while still allowing for nice table output.

Simple tables can be made with dashes and plus signs and pipe symbols. Use spaces to indicate the size of cells. However these can be difficult to hand-type and maintain with changes over time.

The [RST documentation](https://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html#tables) has several table syntax examples, but over time I have found that the most useful way to maintain table data in columns and rows is the `csv-table` directive. Indicate header rows and labels in the cells, along with the widths of each column. Then enter the data in a CSV-like stye. Here's an example:

```
.. csv-table:: a title
   :header: "name", "firstname", "age"
   :widths: 20, 20, 10

   "Smith", "John", 40
   "Smith", "John, Junior", 20
```

If you also output PDF using LaTeX with Sphinx, be aware that there's a column specification for tabular data. Then you can use centimeters for width like so:

```
.. tabularcolumns:: |l|c|p{5cm}|
+--------------+---+-----------+
|  simple text | 2 | 3         |
+--------------+---+-----------+
```

## Templating and data-based layouts and lists

Jekyll uses the [Liquid templating engine](https://shopify.github.io/liquid/), originally built by Shopify, written in Ruby.

Hugo has a packaged templating engine similar to liquid, but Go-based.

Sphinx uses Python for any extensibility you may need.

When using a templating engine like Liquid in Jekyll, you can access the version value from a data file such as in the `_data` folder in a `navigation.yml` file. For example, when the URLs for versions are built to static folders with the version value, you can then put the version values into a data format along with the URls:

```
versions:
  - title: "Latest (1.8)"
    url: http://docs.example.com/latest/
  - title: "Version 1.8"
    url: http://docs.example.com/1.8/
  - title: "Version 1.7"
    url: http://docs.example.com/1.7/
```

Then, to create a drop-down menu for versions with an unordered list, use a `for` loop.

The Read the Docs theme for Sphinx does something similar to indicate the version, using values from the `conf.py` file for the project and a definition list rather than an unordered list:

## Translations

## Alternative CI/CD options for deploying and hosting docs sites

You can also deploy Jekyll gem-based sites using free hosting options as alternatives to GitHub Pages.

* GitLab also offers GitLab Pages, read more [about how to set it up to learn how](https://about.gitlab.com/2016/04/07/gitlab-pages-setup/).

*  [Netlify](https://www.netlify.com/blog/2015/10/28/a-step-by-step-guide-jekyll-3.0-on-netlify/) provides the same capability as GitHub and GitLab with the Ruby gem configuration described in this tutorial and in the [Minimal Mistakes theme documentation](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#ruby-gem-method).
