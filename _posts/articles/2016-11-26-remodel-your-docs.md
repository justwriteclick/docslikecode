---
layout: post
title: Remodeling documentation
excerpt: "Make sure you have a punch list."
modified: Sat Nov 26 16:23:13 CST 2016
categories: articles
tags: [issues, bugs, technical debt, github, git, backlog]
image:
  feature: mtischendorf-logpile.jpg
  credit: Flickr mtischendorf
  creditlink: https://flic.kr/p/aAb4s8
comments: false
share: true
---

A few years ago we went house-hunting in Austin, Texas. One house was so popular during the first showing, there were six back-to-back appointments. We waited in the driveway while another couple toured it. Once they left, we could quickly go through it while another prospective buyer waited on the front walkway.

This house was awful. Every single surface was ugly, out-dated, and circa 1973. There was a giant hole in dirt by the front porch, likely dug by an animal. But you know what? I loved it. I wanted to bring it back to a vibrant family home, taking it back from the rogue porch-dwelling raccoons &mdash; or was it dirt-digging armadillos? We may never know.

![Raccoon visiting](../../images/trikersticks-raccoon.jpg "Raccoon visiting")

Let’s look at your code base and your doc base as a great house with a good layout and foundational “bones.” You still need that “punch list” to hand to your contractor. When you move towards more docs like code techniques, make sure you treat your doc base like a code base, and track defects. Get that “punch list” done.

With a code base, you know how much remodeling you need to do. The same thinking can work well for docs. How dated have your docs become? How accurate are the docs compared to the rest of the code base? How can you make the site livable and vibrant again? 

Let’s give your readers the chance to do those quality checks for you as easily as possible: by reporting the bug on the page where they found it.

This technique works well when:

* You have more readers than contributors. (I generally hope this always happens.)
* Your readers are super busy. Still, they do want to make the docs better and help others.
* You want to know how far your docs have “drifted” from the truth.
* You want your docs to be more trustworthy by chipping away at a bug backlog.
* You have a private GitHub repo for documentation, but you want to enable public bug reports with tracking back to your docs repo.

Your quick win is to look at your current docs site, any given page. Is there a way to report a bug publicly, to add to the “punch list?” 

1. Bare minimum starter level would be an email address link from every page. 
1. Level up by adding a link to your GitHub source repo Issues page so readers can report bugs. 
1. Better yet, write a quick bit of code to embed on every output doc page so that the issue is pre-filled with relevant information. 

Here are some resources to get your first punch in that punch list:

* Using Python Sphinx? The OpenStack docs theme has some Javascript you could re-use to pre-populate an Issue template so the reporter sends the page URL, the source URL, the git SHA of the commit for that version of the page, and the release version value. See this [docs.js snippet](https://github.com/openstack/openstackdocstheme/blob/master/openstackdocstheme/theme/openstackdocs/static/js/docs.js#L119).
* Using a private repo for docs, but want to track bugs publically? Use [Issues-only Access Permissions](https://help.github.com/articles/issues-only-access-permissions/).
* Want to add a bit of code to pre-create Issues to use as comments on every page? Free yourself from Disqus comments. Try this [set of tips and sample code in a blog post](http://zpbappi.com/jekyll-with-tags-archive-and-comments-in-github-pages/).


{% include sign-up.html %}
