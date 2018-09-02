---
title: "Templating and data-based layouts"
image:
  path: /images/so-simple-sample-image-4.jpg
  thumbnail: /images/site-logo.png
---

Templates within static site generators enable you to use variables or metadata values from other files in the source files that create HTML. Maybe you want to keep the product version value in a metadata file. Or you want to access the domain name the site is built upon, reliably and repeatedly. Template engines integrated with the underlying programming language give access to loops, variables, or functions so that you can enhance your website output.

* Jekyll uses the [Liquid templating engine](https://shopify.github.io/liquid/), originally built by Shopify, written in Ruby.
* Hugo has a packaged templating engine similar to liquid, but Go-based. Read more in [Introduction to Hugo Templating](https://gohugo.io/templates/introduction/).
* Sphinx uses Python for any extensibility you need. I find it helpful to browse through the [Read the Docs Theme](https://github.com/rtfd/sphinx_rtd_theme) to find examples of templating.

When using a templating engine like Liquid in Jekyll, you can access the version value from a data file. Read more in the Liquid documentation about [Iteration](https://shopify.github.io/liquid/tags/iteration/).

The Read the Docs theme for Sphinx uses Python variables to indicate the version, using values from the `conf.py` file for the project and a definition list rather than an unordered list.

## Additional resources

[Learning Liquid](https://www.shopify.com/partners/blog/topics/learning-liquid)
