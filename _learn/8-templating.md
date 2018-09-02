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

Then, to create a drop-down menu for versions with an unordered list, use a `for` loop. You can see an example of this in the `versions-jekyll` repository at https://github.com/justwriteclick/versions-jekyll.

The Read the Docs theme for Sphinx does something similar to indicate the version, using values from the `conf.py` file for the project and a definition list rather than an unordered list:

```
      <dl>
        <dt>{{ _('Versions') }}</dt>
        {% for slug, url in versions %}
          <dd><a href="{{ url }}">{{ slug }}</a></dd>
        {% endfor %}
      </dl>
```


## Additional resources

[Learning Liquid](https://www.shopify.com/partners/blog/topics/learning-liquid)
