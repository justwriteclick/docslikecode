---
layout: post
title: Building Docs Like Code
excerpt: "Let's look at a live example."
modified: Sun Sep 25 15:35:08 CDT 2016
categories: articles
tags: [developers, github, git, improvement, quality, testing, writers]
image:
  feature: threeblackdots-playground.jpg
  credit: Flickr threeblackdots
  creditlink: https://flic.kr/p/8tQAGQ
youtube: YUbl_ucNPuA
comments: false
share: true
---

Let's take a look at what docs like code looks like in practice.

The basic steps on a Mac are:

1. Make sure you have all the pre-requisites set up for Ruby, Jekyll, and Bundler. [Set up GitHub Pages locally](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/) as instructed in the excellent GitHub documentation.
1. Clone a repository that contains a Jekyll theme that you like. We're using the [so-simple theme](https://mmistakes.github.io/so-simple-theme/) here.
1. Switch to the cloned git directory.
1. Run `bundle install` to install the required gems.
1. Run `bundle exec jekyll serve` to serve the content from a local web server.
1. Copy and paste the `http://127.0.0.1:4000/` URL into your web browser.

This video shows you how to clone a GitHub repo with an existing Jekyll theme, and build it locally.

### How it's made

<iframe width="560" height="315" src="https://www.youtube.com/embed/{{ include.id }}" frameborder="0" allowfullscreen></iframe>

