---
layout: post
title: Yes You Can Use GitHub Pages with Python Sphinx
excerpt: "Learn some pro tips to build Python Sphinx developer docs to both GitHub Pages and your local system."
last_modified_at: Sat Apr 20 09:43:00 CDT 2019
categories: articles
tags: [github, git, python, sphinx, documentation, developer, docs]
image:
  path: /images/keyboard-mleung311.jpg
  caption: "[Flickr mleung311](https://flic.kr/p/fqJJbW)"
comments: false
share: true
---

If you prefer to write in ReStructured Text instead of Markdown for your technical documentation, you're in good company. There are quite a few benefits to using Sphinx, Python, RST, and Sphinx extensions because these tools are custom-built with developer documentation in mind.

Another great offering is GitHub Pages, with automatic publishing when a known branch, such as the `master` or `gh-pages` branch is updated.

So, how about the best of both? Let's dive into the key configurations that enable you to publish Python Sphinx pages to GitHub Pages.

## Naming the GitHub repository can affect the resulting URL

If you want a URL like `<username>.github.io` or ``<orgname>.github.io`, name the repo `<username>.github.io` or `<orgname>.github.io`. Then, by default, GitHub Pages publishes to the URL matching the repo name.

## Enable GitHub Pages for the GitHub repository

> Note: You must have admin privileges on the repository to see the **Settings** tab.

1. Go to the repository on the GitHub website and make sure you are logged in.
1. Add a `/docs` directory to the `master` branch. Otherwise you do not get the **master branch /docs folder** for the Source option in the drop-down list.
1. Click the **Settings** tab. You first go to the Options section.
1. Scroll down to the **GitHub Pages** section and choose the drop-down list under Source.
   > Note: Your choices will differ based on whether you're in a User repo or an Org repo. [Read all about the differences in the GitHub docs](https://help.github.com/en/articles/user-organization-and-project-pages).

1. To keep source and output HTML separate, choose **master branch /docs folder** for Source.

Next, you set up the `.nojekyll` file to indicate you aren't using Jekyll as your static site generator in this repository.

## Add a .nojekyll file in the /docs directory

When GitHub sees a `.nojekyll` file, it serves the root `index.html` file. Read more in the [original blog post about this feature](https://github.blog/2009-12-29-bypassing-jekyll-on-github-pages/).

> Note: I'd recommend using the `/docs` directory on the `master` branch, so that you are sure to keep source and output HTML separate. You could also use a `_build` directory in the root of your repo as the served HTML.

1. Create a new branch locally, named `docs-config` in this example, based on `master`:
   ```
   $ git checkout -b docs-config
   ```
1. Create an empty dot file, named `.nojekyll` within the `/docs` folder of your repo. A dot file has a period prefix and may not be visible in all text editors or your Finder windows, so be aware and don't panic if you can't "see" it later.
1. Use the add command to make sure Git starts tracking the file:
   ```
   $ git add docs/.nojekyll
   ```
1. Commit the change with the `-a` option to add new files to the commit, and the `-m` option for a message:
   ```
   $ git commit -a -m "Adds a .nojekyll file for docs builds"
   ```
1. Push the change to the remote, in this case named "origin", so you can compare the change to `master`.
   ```
   $ git push origin docs-config
   ```
1. On the GitHub website, go to your repository and create a Pull Request.
1. Merge the Pull Request to add the `.nojekyll` file to the `master` branch.

## Create a "docsource" or "docsrc" folder for the source files

Now, in the root of your repository, you can create a source folder for your doc builds:

  - If you're working with code and docs in the same repo, you can name the folder `docsource` or `docsrc`.
  - If your repo is for only documentation, you can name the folder `source`.

Next, make sure that your `conf.py` file has been set up with these source and destination directories. The Sphinx documentation has a good [Configuration section](http://www.sphinx-doc.org/en/master/usage/configuration.html).

## Make sure you can still build Sphinx locally for reviews

Here's another pro tip I found while browsing [Issues in the Sphinx repository itself](https://github.com/sphinx-doc/sphinx/issues/3382#issuecomment-470772316). Since you want to keep the source and output separate, but still be able to both publish on GitHub Pages and preview builds locally, you can add an option to your `Makefile` to do both.

```
  github:
      @make html
      @cp -a _build/html/. ../docs
```

Now you can run `make github` from the doc source directory to generate a local preview and move the docs where GitHub wants to serve them from.

> Note: Realize that there's a `conf.py` setting for both where the `make` command is run and where files are built to. Read up in the [Configuration section](http://www.sphinx-doc.org/en/master/usage/configuration.html) of the Sphinx docs for all the details.

## Pull it all together

I've been working on a talk titled, "Make an Instant Web Site with Webhooks" for DevNet Create. In it, I show how to publish and host on GitHub Pages, which is built to use Jekyll by default, using Python Sphinx instead. I've got a GitHub repository set up at [annegentle/create-demo](https://github.com/annegentle/create-demo) as a demonstration. I'll post the slides when it's done. In the meantime, we'd love to see you next week! Visit the [DevNet Create site](https://developer.cisco.com/devnetcreate/2019) for more information.

{% include sign-up.html %}
