---
title: "Evaluating Static Site Generator themes"
image:
  path: /images/so-simple-sample-image-4.jpg
  thumbnail: /images/site-logo.png
---

Themes for static site generators often provide the advanced user experience features such as search. You also analyze the theme to make decisions on the authoring side, such as a table format for large data tables. What about printed outputs, such as PDF? Or versions for the output and the source? Any performance gains you can make with the builds themselves? Themes are one part of this analysis.

Here's a short list of questions you may want to ask about the theme you use for a static site generator.

## Admonitions or notes
Are there designs for output of levels of admonition, such as warning, information, and note?

## Code syntax and highlighting
For code examples, can you set the exact highlight you want to use, such as JavaScript or Python or Bash? Does the code snippet have a copy icon for copying only the code and not copying a prompt?

## Comment engines
Which comment engines are supported and do they work with what other organizations use in your company or group?

## Customization
How straightforward is it to add your logo or a header that's common to multiple web sites? Can you learn how to maintain the theme's customizations yourself or will you need to rely on a web developer for maintenance and any enhancements such as adding a version drop-down list? For example, the Jekyll theme "Minimal Mistakes" is "skinnable," meaning you can [configure various color variations](https://mmistakes.github.io/minimal-mistakes/docs/configuration/) for that theme.

## Images
Are images automatically resized when looking at them on a mobile browser or resized browser window? Are alt tags and captions considered in the design?

## Localization and translation support
When translations are available, are they simple to get to? Does the theme itself have the ability to be localized, such as for the search form or navigation elements, can the labels used in the theme be localized?

## Navigation and configuration possibilities
Does the theme have a sidebar, breadcrumbs, and an in-page table of contents? Can you turn on or off each based on the page layout or page template or whether the person is using a mobile browser or tablet?

## Responsive and mobile design
Does the theme use thoughtful navigation and search when on a small screen?

## Search
Is the search form in a prominent location and if needed, can you move the search form on the page? Does the search work on mobile devices with readable results? Can the result list also be styled?

## Social media support
If you want Twitter cards for your documentation pages, are they available through the theme? Which social media sites can you link to from each documentation page?

## Tables
Do tables work on different browsers? If PDF or epub is another output option, do the tables still work on a particular page size or do you need to adjust how tables are made in the source file itself for good results in the output?

## Theme Updates
How easy is it to upgrade the theme files? Can you make regular updates through a version-control system and know exactly which theme you have in use?

## Versions
Many themes do not have a version picker by default. You might want a drop-down list or navigation that could include version. The Sphinx Read the Docs theme does have one and it works great. For Jekyll, look at the [versions-jekyll repository](https://github.com/justwriteclick/versions-jekyll) to see a couple of implementation ideas.
