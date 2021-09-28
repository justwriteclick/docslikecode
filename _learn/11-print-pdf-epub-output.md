---
title: "Evaluating print, PDF, or epub output"
layout: learn
image:
  path: /images/learn/print-pdf-epub.png
  thumbnail: /images/learn/print-pdf-epub400x225.png
---

How difficult or straightforward is it to create a print or PDF format? You may want to investigate and test solutions beyond this article, as requirements and print tolerances can vary widely.

### Jekyll options

In the Jekyll Documentation Theme site, Tom Johnson suggests buying a license for Prince XML ($500) in order to create print-ready PDF files with the [Jekyll Documentation Theme](https://idratherbewriting.com/documentation-theme-jekyll/). The PDF layout and styles are set using CSS. Considering that the only gem solution, [jekyll-pdf](https://github.com/abeMedia/jekyll-pdf), makes PDF files of single pages rather than a collection, the third-party solution is probably the way to go. You could look into the [Open-Publisher](https://github.com/chrisanthropic/Open-Publisher) project, which is using Jekyll to create outputs that can be used as Pandoc inputs. [Pandoc](https://pandoc.org/) is a super handy conversion tool that can convert many formats to other formats, and has templating capabilities that can help.

### Sphinx options

When you use Read the Docs builds for deployment, you automatically get versioned documentation based on releases, as well as PDF output for the entire site. The PDF formatting is based on [LaTex](https://www.latex-project.org/), an open source typesetting system. It has page numbering, linking, and footnotes.

You also notice you get an Epub output when you use [Read the Docs](https://readthedocs.org/). Sphinx does have advantages over other static site generators for book-like output options since the Read the Docs theme is so thorough.

### Hugo options

Hugo supports many [custom output formats through templates](https://gohugo.io/templates/output-formats/), but as of right now no one has written a series of templates for PDF, based on the discussions in various Issues, such as [#1360 Generate concatenated document for Kindle/PDF generation](https://github.com/gohugoio/hugo/issues/1360) and [#3530 Add alternative rendering format for LaTeX](https://github.com/gohugoio/hugo/issues/3530). You could also use Prince XML as a solution here, similar to Jekyll.

## Other options?

For the _Docs Like Code_ book, I have written an article about how I created print-ready PDF and Amazon-supported ebook files such as the MOBI format. Read more in [Practical Advice On Publishing A Technical Book using GitHub and GitBook](https://www.docslikecode.com/articles/practical-advice/). GitBook has since changed their overall pricing and support plan, but is certainly worth investigating.
