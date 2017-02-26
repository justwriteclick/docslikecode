# Always Be Publishing: Continuous Integration for Docs

Let's face it. Writing documentation can be downright boring sometimes. It is as exacting as the code itself. There are syntax errors and unwanted whitespace that you can introduce. Sometimes your ideas simply stop flowing, but you still need to fill in the blanks to make sure your docs are complete.

By writing documentation collaboratively as close to the code as possible, you can automate documentation tests, builds, and deployments. This approach provides many benefits: tested doc builds, continuous publishing, reviews of the docs and the code together, multiple outputs including tested code examples, release management, and prevents code from merging unless it has adequate documentation.

## Introduction to Docs CI/CD

Many programming languages have a documentation framework that integrates well. Typically these are static site generators, such as Jekyll for Ruby, and Sphinx for Python. The source files for the docs are Markdown or reStructured Text (RST). With these static site generators, you can make beautiful documentation sites. In fact, there's a <a href="https://github.com/PharkMillups/beautiful-docs">collection of links to beautiful docs on GitHub</a>.

For REST API documentation, three frameworks also provide documentation output in the form of web pages, many of them interactive. These are OpenAPI, RESTful API Modeling Language (RAML), and API Blueprint. OpenAPI, previously known as Swagger, is based on JSON, and because YAML is a superset of JSON, you can interchange the source file. RAML is a YAML-based language to describe REST APIs. API Blueprint uses Markdown and can also adhere to <a href="https://help.github.com/categories/writing-on-github/">GitHub Flavored Markdown syntax</a>.

Because these doc source files can be transformed using scripts, you can continuously build the documentation with the same build jobs as the code. For example, when building a Jekyll web site like <a href="http://http://docslikecode.com">docslikecode.com</a>, the Travis CI job is simple:

```
#!/usr/bin/env bash
set -e # halt script on error

bundle exec jekyll build
bundle exec htmlproofer ./_site
```

Jekyll sites are deployed by copying flat files from a static directory, so you can store a script to build the site in the code repo with other build files. You can also have a simple link checker to test for any broken links before deploying the site. The `htmlproofer` is a Ruby library written to do just that.

The deployment mechanism provided by GitHub is called GitHub Pages. You have some options for triggering a docs deployment. You can automate builds from a `gh-pages` branch, from the `master` branch, or always deploy docs from a `/docs` directory on the `master` branch. Your GitHub repo has these options on the Settings page. While you can deploy to a custom domain name, one limitation for GitHub Pages currently is that you <a href="https://github.com/isaacs/github/issues/156">cannot serve directly through HTTPS</a>, but as a free service it's a good starting point. For production web sites, you can deploy from GitHub to a cloud server or VPS that has the security requirements you need. More or less, you are creating your own hosted web site.

## Why and when to treat docs like code




## REST API documentation written collaboratively


## Tests for reviewing docs


