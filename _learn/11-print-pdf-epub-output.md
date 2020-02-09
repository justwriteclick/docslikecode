---
title: "Evaluating print, PDF, or epub output"
image:
  path: /images/learn/print-pdf-epub.png
  thumbnail: /images/learn/print-pdf-epub400x225.png
---

How difficult or straightforward is it to create a print or PDF format? You may want to investigate and test solutions beyond this article, as requirements and print tolerances can vary widely.

### Jekyll PDF options

In the Jekyll Documentation Theme site, Tom Johnson suggests buying a license for Prince XML ($500) in order to create print-ready PDF files with the Jekyll Documentation Theme. The PDF layout and styles are set using CSS. Considering that the only gem solution, [jekyll-pdf](https://github.com/abeMedia/jekyll-pdf), makes PDF files of single pages rather than a collection, the third-party solution is probably the way to go.

### Sphinx PDF output

When you use Read the Docs builds for deployment, you automatically get versioned documentation based on releases, as well as PDF output for the entire site. The PDF formatting is based on [LaTex](https://www.latex-project.org/), an open source typesetting system. It has page numbering, linking, and footnotes.

### Hugo PDF output

Hugo supports many [custom output formats through templates](https://gohugo.io/templates/output-formats/), but as of right now no one has written a series of templates for PDF, based on the discussions in various Issues. ([#1360 Generate concatenated document for Kindle/PDF generation](https://github.com/gohugoio/hugo/issues/1360)) ([#3530 Add alternative rendering format for LaTeX](https://github.com/gohugoio/hugo/issues/3530)). You could also use Prince XML as a solution here, similar to Jekyll.
