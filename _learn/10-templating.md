---
title: "Templating and data-based layouts"
layout: learn
image:
  path: /images/learn/web-templates.png
  thumbnail: /images/learn/web-templates400x225.png
---

Templates can have a couple of different definitions for content, depending on the size. You can make a template for an entire document or for a page. When talking about repositories you can also have a template for a repository. 

Template engines within static site generators enable you to use variables or metadata values from other files in the source files that create HTML. Maybe you want to keep the product version value in a metadata file. Or you want to access the domain name the site is built upon, reliably and repeatedly. Template engines integrated with the underlying programming language give access to loops, variables, or functions so that you can enhance your website output.

* Jekyll uses the [Liquid templating engine](https://shopify.github.io/liquid/), originally built by Shopify, written in Ruby. The template language is also called Liquid. 
* Hugo has a packaged templating engine similar to Liquid, but Go-based. Read more in [Introduction to Hugo Templating](https://gohugo.io/templates/introduction/).
* Sphinx uses Python for any extensibility you need. I find it helpful to browse through the [Read the Docs Theme](https://github.com/rtfd/sphinx_rtd_theme) to find examples of templating.

## Version values as a use case for templates

For web templates, the data can be substituted at the smallest level possible, the word or character level. A templating engine uses certain characters to indicate that you want to start substituting in other information from a data source. For example, a double curly bracket can show the start of the template insertion point.

When using a templating language like Liquid in Jekyll, you can access the version value from a data file or from a database. Read more in the Liquid documentation about [Iteration](https://shopify.github.io/liquid/tags/iteration/).

The Read the Docs theme for Sphinx uses Python variables to indicate the version, using values from the `conf.py` file for the project and a definition list rather than an unordered list.

A practical example for storing a value for version would be in the `_config.yml` file in a Jekyll project. In this case, you want to output the older versions of the docs site to different base URLs, and there was a product name change from one version to the next.

`_config.yml`

```
baseurl                  : /versions-jekyll/latest
productname              : Oppogrid
```

`_config.4.2.yml`

```
baseurl                  : /versions-jekyll/4.2
productname              : Oppogrid
```

`_config.4.1.yml`

```
baseurl                  : /versions-jekyll/4.1
productname              : Opposcale
```

Any place that your source files contain these template indicators, you can rely on substitution to fill in the values. 

Example snippet from a Markdown file with substitutions:

See the &#91; &#123;&#123; site.productname &#125;&#125; User Guide&#93;&#40;&#123;&#123; site.baseurl &#125;&#125;user-guide&#41; for more information.

With the first `_config.yml` file, the output would be:
"See the [Oppogrid User Guide](https://annegentle.io) for more information." and the internal cross link would go to the correct version for that site. 

## Additional resources

[Learning Liquid](https://www.shopify.com/partners/blog/topics/learning-liquid)

[Sphinx Readthedocs theme documentation](https://sphinx-rtd-theme.readthedocs.io/)