---
layout: post
title: Quality Tracking with GitHub for Docs
excerpt: "What do you do when people say, 'The Docs Suck.'?"
last_modified_at: Fri Sep 23 21:03:14 CDT 2016
categories: articles
tags: [developers, github, git, improvement, quality, testing, writers]
image:
  path: /images/stacked-logs-mtischendorf.jpg
  caption: "[Flickr mtischendorf](https://flic.kr/p/aAb4s8)"
comments: false
share: true
---

A definitive aspect of a docs-like-code philosophy is attention to quality and accuracy. You want the docs to get better and better. You want to know if the docs are out of date compared to tightly-coupled code. You want people to report issues when they see something that needs fixing. The vision is that more readers mean more testers, and those readers and testers should report problems right there on the page.

## What do you do when people say, "The Docs Suck."?

It's a pretty simple request:

1. Tell me which page.
1. Tell me your expectations for that page.
1. Tell me how to fix it.

You can then pre-fill with additional information to help you or other collaborators fix the bug, such as the source file and when it was merged into the repository.

All these concerns can be addressed with a great [Issues template](https://github.com/blog/2111-issue-and-pull-request-templates). To make an Issue template for a GitHub docs repository, save a file named ISSUE_TEMPLATE in the root directory that contains the information you need in Markdown format. Add headings, links, @-mentions, and task lists to your Issue template.

In OpenStack, we use [JavaScript](https://github.com/openstack/openstackdocstheme/blob/master/openstackdocstheme/theme/openstackdocs/static/js/docs.js#L119) to pre-fill the bug form with the page title, URL, a link to the source file itself, and any tags to add to the logged doc bug. I'm sure you could adopt something similar in your static site generator as well.

Users click here: ![Figure: Report a docs bug]({{base_url}}/images/report-a-bug.png)

Next, users go through a bug reporting workflow with a pre-filled template:
![Figure: Pre-filled docs bug template]({{base_url}}/images/pre-filled-bug-template.png)

To take it a step further, you can also add a link to edit the source doc file in GitHub's web editor workflow to have the person fix the bug themselves.

## From no reviews to many

In traditional enterprise doc systems, writers can go weeks without getting reviews or input. Even when asking and nagging multiple times, sometimes the documentation systems are so separate from code systems that technical reviews are through email. GASP. Put those days behind you and go where the technically knowledgeable people are.

Working in the same collaboration tools as technical people gives better reviews. We can merge as many as 50 patches per day, though in reality it's about a dozen a day. We are running up to four automated doc tests per patch and requiring two humans to check the patch and click in order to publish. Each reviewer who can publish must adhere to our review rules, and people follow the rules really well.


{% include sign-up.html %}
