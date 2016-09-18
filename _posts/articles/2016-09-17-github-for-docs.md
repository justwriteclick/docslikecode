---
layout: post
title: The Vocabulary of GitHub for Documentation
excerpt: "What would happen if we treated docs like code?"
modified: Sat Sep 17 07:11:52 CDT 2016
categories: articles
tags: [github, git, definitions, repository, branch, fork, pull request]
image:
  feature: guarded-lightbulb-rob-sinclair.jpg
  credit: Flickr rob-sinclair
  creditlink: https://flic.kr/p/8J2gDY
comments: false
share: true
---

What if you could use GitHub, static site generators, and Continuous Integration and Deployment (CI/CD) for our documentation? I imagine you can track your backlog and get some metrics on the quality with their nice contributor graphs. I bet you could measure "docs drift" to figure out just how behind the docs have gotten. Hey, let's also get access to the developer playground and fun equipment! Let's play on the slides and swings while we make cool and beautiful documentation, side-by-side as collaborators.

I hope you're wondering, "What would happen if we treated docs like code?"

Believe me, your fellow software builders are wondering, experimenting, or already starting down this road. I've seen this vision come to life and want to share my experiences so more people can learn these techniques.

![git]({{ site.url }}/images/git-logo.png)
{: .pull-right}

I’ve found that the principles inherent to the social web for coding work extremely well for documentation. The social web, leads to social coding, leads to social documentation.

# What is GitHub?

Like many tools, git and GitHub were created by fire — through a pressing need for performant and efficient source control management for theLinux kernel. Read the history in the excellent [Pro Git Book](https://git-scm.com/book/en/v2/Getting-Started-A-Short-History-of-Git).

GitHub is the web interface for `git` the command-line tool, that works well on Linux, Mac, or Windows. To work with others on a project (code or docs), you merge files. This model is the opposite of using  a “lock and checkout” model, where no one else can work on the piece at the same time as you. With GitHub, you can work separately and bring it all together later. Git has a non-linear branching model that can take some learning to get used to. That said, I've found git and GitHub for docs quite practical and even inspirational.

![GitHub]({{ site.url }}/images/github-logo.png)
{: .pull-left}

You can keep docs in a source code repository then the developers will review all your changes prior to merging them in. Unlike traditional source code management, branches are not full copies of entire code base so they are “cheap” and “fast.” The more Agile techniques are applied to documentation, the
more treating docs like code makes sense.

# GitHub definitions and parallels for information

I hope I'm talking to people who care a lot about words. Let's start with some vocabulary and definitions to build upon.

* Branch: Indicator of divergence from base without changing the main line (or "trunk" if you like to visualize organic tree-structures to remember this term).
* Commit: Point in time snapshot of repository with changes.
* Fork (noun): Copy of the repository that is entirely yours in your namespace. In GitHub-land, forking does not have a negative connotation that it can in other contexts (such as taking an open source project in a new direction in a huff to get different contributors). Rather, it is a way to contribute openly and publicly with your account attributed.
* Fork (verb): Making a copy of the repository.
* Issue: Defects, tasks, or feature requests.
* Organization: Collection of group-owned repositories.
* Pull Request: Comparison of edits to see if team wants to accept changes.
* Push: Move changes branch-to-branch. The man page says "Update remote refs along with associated objects" but that's more technical than we need here.
* Repository: Collection of stored code or documentation that is written and built like code.
* Review: Do a line-by-line comparison of a change, much like an editor would for documentation, and comment on improvements or changes.

These definitions can give you decision points to make about information architecture, so think about which deliverables you'll make, who should review and collaborate on those deliverables, and how you can automate publishing with the chunks of a repository or an organization as overarching collections.

Take a look at this article on GitHub to get a sense of the "source" for a document. We'll look at the source aspects in a future article. To stay in touch, subscribe to get relevant emails in your inbox.

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