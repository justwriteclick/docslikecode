---
title: "Evaluating Static Site Generator themes"
layout: learn
image:
  path: /images/learn/ssg-themes.png
  thumbnail: /images/learn/ssg-themes400x225.png
---

Themes for static site generators often provide the advanced user experience features such as navigation, search, and responsive designs for mobile consumption. You also analyze the theme to make decisions on the authoring side, such as a table format for large data tables.

When researching and selecting a theme, analyze the possibilities for printed outputs, such as PDF or EPUB. Perhaps you need version control for both the output and the source files. The size of your site may mean you need to consider performance gains you can make with the build. Themes are one part of this analysis.

Here's a short list of questions you may want to ask about the theme you use for a static site generator.

## Admonitions or notes
Are there designs for output of levels of admonition, such as warning, information, and note?

Advanced admonitions can enable substituting custom text instead of "Note" or "Warning," or custom icons. You can also configure the admonitions in some themes to expand or contract in-page. For example, look at the variations for Markdown source with the [Mkdocs Material theme when using the admonition extension](https://squidfunk.github.io/mkdocs-material/extensions/admonition/). Or, when using [RST with the Read the Docs theme, you have lots of directives](https://sphinx-rtd-theme.readthedocs.io/en/latest/demo/demo.html#admonitions) to choose from, including Attention, Hint, Important, Note, Tip, Error, or Danger, or write your own. You should also test if code blocks work within an admonition if that is important in your documentation.

![Note, Tip, Error, oh my](/images/learn/rtd-admonitions.png)

## Code syntax and highlighting
For code examples, can you set the exact highlight you want to use, such as JavaScript or Python or Bash? Does the code snippet have a copy icon for copying only the code and not copying a prompt? What about the behavior of the scroll bar for long lines of code examples? Are there line numbers available? Can you highlight or emphasize certain lines to convey meaning? How about captions on the code block, similar to captions on figures?

## Comments or forums integration
Which comment engines are supported? Do they work with the comment systems other organizations use in your company or group?

## Customization
How straightforward is it to add your logo or a header that's common to multiple web sites? Can you learn how to maintain the theme's customizations yourself or will you need to rely on a web developer for maintenance and any enhancements such as adding a version drop-down list? For example, the Jekyll theme "Minimal Mistakes" is "skinnable," meaning you can [configure various color variations](https://mmistakes.github.io/minimal-mistakes/docs/configuration/) for that theme.

## Images
Are images automatically resized when looking at them on a mobile browser or resized browser window? Are alt tags and captions considered in the design?

## Localization and translation support
When translations are available, are they simple to get to? Does the theme itself have the ability to be localized, such as for the search form or navigation elements, can the labels used in the theme be localized?

## Navigation and configuration possibilities
Does the theme have a sidebar, breadcrumbs, and an in-page table of contents  available? Can you turn on or off each based on the page layout or page template or whether the person is using a mobile browser or tablet?

Do you want to have Previous and Next buttons on each page, so that someone can go through a series of pages in order?

## Responsive and mobile design
Does the theme use thoughtful navigation and search when on a small screen?

Can your readers get to the Contents fairly easily and expand and contract, even when on a mobile phone or tablet? Check how the search experience works when using a smaller screen. Most of the built-into-the-browser developer tool kits, such as the Chrome Developer Tool, lets you preview the site experience on a simulated smaller screen.

![](/images/learn/rtd-mobile-nav.png)

## Search
Is the search form in a prominent location and if needed, can you customize the them to place the search form somewhere else on the page? Does the search work on mobile devices with readable results? Can the result list also be styled?

## Social media support
If you want Twitter cards for your documentation pages, are they available through the theme? Which social media sites can you link to from each page?

## Tables
Do tables work on different browsers? If PDF or epub is another output option, do the tables still work on a particular page size or do you need to adjust how tables are made in the source file itself for good results in the output?

## Theme updates
How easy is it to upgrade the theme files? Can you make regular updates through a version-control system and know exactly which theme you have in use?

## Versions
Many themes do not have a version picker by default. You might want a drop-down list or navigation that could include version. The Sphinx Read the Docs theme does have one and it works great. For Jekyll, look at the [versions-jekyll repository](https://github.com/justwriteclick/versions-jekyll) to see a couple of implementation ideas.

## Evaluating other options

* [Evaluating table layouts and formatting](https://www.docslikecode.com/learn/08-evaluating-table-layouts/)
* [Evaluating Static Site Generator search options](https://www.docslikecode.com/learn/09-ssg-search-implementations/)
