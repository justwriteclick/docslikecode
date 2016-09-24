---
layout: post
title: Quality Tracking with GitHub for Docs
excerpt: "What do you do when people say, 'The Docs Suck.'?"
modified: Fri Sep 23 21:03:14 CDT 2016
categories: articles
tags: [developers, github, git, improvement, quality, testing, writers]
image:
  feature: stacked-logs-mtischendorf.jpg
  credit: Flickr mtischendorf
  creditlink: https://flic.kr/p/aAb4s8
comments: false
share: true
---

A definitive aspect of a docs-like-code philosophy is attention to quality and accuracy. You want the docs to get better and better. You want to know if the docs are out of date compared to tightly-coupled code. You want people to report issues when they see something that needs fixing. The vision is that more readers mean more testers, and those readers and testers should report problems right there on the page.

## What do you do when people say, "The Docs Suck."?

It's a pretty simple ask:

1. Tell me which page.
1. Tell me your expectations for that page.
1. Tell me how to fix it.

You can then pre-fill with additional information to help you or other collaborators fix the bug, such as the source file and when it was merged into the repository.

All these concerns can be addressed with a great [Issues template](https://github.com/blog/2111-issue-and-pull-request-templates). To make an Issue template for a GitHub docs repository, save a file named ISSUE_TEMPLATE in the root directory that contains the information you need in Markdown format. Add headings, links, @-mentions, and task lists to your Issue template.

In OpenStack, we use [JavaScript](https://github.com/openstack/openstackdocstheme/blob/master/openstackdocstheme/theme/openstackdocs/static/js/docs.js#L119) to pre-fill the bug form with the page title, URL, a link to the source file itself, and any tags to add to the logged doc bug. I'm sure you could adopt something similar in your static site generator as well.

Users click here: ![Figure: Report a docs bug]({{base_url}}/images/report-a-bug.png)

And go through a bug reporting workflow with some pre-filled information from the web page they clicked through:
![Figure: Pre-filled docs bug template]({{base_url}}/images/pre-filled-bug-template.png)

To take it a step further, you can also add a link to edit the source doc file in GitHub's web editor workflow to have the person fix the bug themselves.

## From no reviews to many

In traditional enterprise doc systems, writers can go weeks without getting reviews or input. Even when asking and nagging multiple times, sometimes the documentation systems are so separate from code systems that technical reviews are through email. GASP. Put those days behind you and go where the technically knowledgeable people are.

Working in the same collaboration tools as technical people gives better reviews. We can merge as many as 50 patches per day, though in reality it's about a dozen a day. We are running up to four automated doc tests per patch and requiring two humans to check the patch and click in order to publish. Each reviewer who can publish must adhere to our review rules, and people follow the rules really well.


<!-- Begin MailChimp Signup Form -->
<link href="//cdn-images.mailchimp.com/embedcode/slim-10_7.css" rel="stylesheet" type="text/css">
<style type="text/css">
	#mc_embed_signup{background:#fff; clear:left; font:14px Helvetica,Arial,sans-serif; }
	/* Add your own MailChimp form style overrides in your site stylesheet or in this style block.
	   We recommend moving this block and the preceding CSS link to the HEAD of your HTML file. */
</style>
<div id="mc_embed_signup">
<form action="//justwriteclick.us1.list-manage.com/subscribe/post?u=3828f8d87d82289b96ff8fd19&amp;id=cc1d483d59" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
    <div id="mc_embed_signup_scroll">
	<label for="mce-EMAIL">Enter your email address to learn about docs like code together</label>
	<input type="email" value="" name="EMAIL" class="email" id="mce-EMAIL" placeholder="email address" required>
    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_3828f8d87d82289b96ff8fd19_cc1d483d59" tabindex="-1" value=""></div>
    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="btn"></div>
    </div>
</form>
</div>

<!--End mc_embed_signup-->
