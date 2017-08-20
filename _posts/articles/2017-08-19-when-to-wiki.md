---
layout: post
title: What about wikis? Content management and change management
excerpt: "Anne Gentle, the original wiki aficionado from the mid-2000s, discusses their relevance today."
modified: Sat Aug 19 20:07:50 CDT 2017
categories: articles
author: anne_gentle
tags: [documentation, docs, wiki, open source]
image:
  feature: spacewalk-nasa2explore.jpg
  credit: NASA Johnson
  creditlink: https://flic.kr/p/iKTgKf
comments: true
share: true
---

While I was writing _Docs Like Code_, I went back and forth in my mind, arguing with myself on whether the timing was quite right. I didn't know for certain if we had reached a tipping point as an industry, or if I was simply seeing a trend relevant only to the open source, developer-centric world I was embedded in.

And then, I heard from Gene in an email.

> "Whenever I start considering retirement, again, I read one of your articles
> and get inspired to keep going.  Thank you for your interesting ideas and
> willingness to share them."

And he kept me going, and asking more questions as I went, and feeling energized once again to answer his question about wikis and writing closer to the code.

Gene goes on to share his background, which resonates with both software developers and technical writers who were once some other profession.

> "The Docs Like Code theme resonates with me as a former software developer
> and having always been embedded with developers as a tech writer.  I think
> it's easier for a developer-writer to buy into the concept than the
> traditional tech writer can because the tools and methodology are already
> familiar.  Myself, I mostly converted because the critical mass behind
> Markdown became too great to continue battling against it.  My ideas of a
> better way gave way to being open to using GitHub and
> Markdown/reStructuredText, and looking for opportunities to make that
> workflow better."

Gene positively nails the place many of us find ourselves today. Converted or converting, migrating from one familiar toolset to another, less familiar one, and taking the best from one workflow to another workflow to streamline the tasks at hand.

We are living through change management in our content management.

He goes on to ask, with double-spaces after periods, which I find absolutely endearing,

> "I still have companies asking about using a wiki for documentation when
> considering jettisoning their legacy documentation tools, which aren't
> working.  I'm able to dissuade them by saying the proliferation of content
> soon becomes unmanageable, and they accept that because they assume I know
> what I'm talking about and they don't when it comes to documentation.  Many
> of the arguments for using a wiki are the same you give in the Docs Like Code
> articles; primarily, collaboration and ease of use."

> "What are your thoughts on the differences between using a wiki and using
> Git/Markdown, that I might be able to give them more substantive arguments?"

This is a good question. I love the phrasing of this question because it does not pre-suppose a value judgement on either method.

If I were in his shoes, I'd be curious and asking questions about the reasons for jettisoning -- is it because of licensing, authoring, or deliverables they can get from legacy? Or maybe there is a combination of reasons I can't come up with? That's interesting, and of course informs your requirements list and considerations.

## Consider the workflow - sit in another environment

For me, when moving towards a docs as code workflow, my eyes were opened when a developer told me he'd never want to leave his Terminal window to write docs. Think about the context switch from coding to opening a wiki page. Many developers do not see a need to open a browser window simply to log in and edit a page that they have to take time to find in the first place. You can avoid that context switching by placing the docs right in the code or in the same repository as the code. This context switch was a powerful push for me, even when pushing away from my familiar XML territory.

## Authentication and privacy needs

Sometimes wikis are seen as internal-only documentation sites, which is a good use case because the wiki can be accessible only behind a firewall, for example. GitHub Pages from Github.com are publicly available when published, even when publishing from a private repository.

You can implement an authentication workflow on a site uploaded to GitHub Pages, but you then need to have the web development resources to maintain the login requirement. You could use GitHub Enterprise Pages with GitHub Enterprise requiring a VPN connection to view pages. Security and openness decisions may preclude one solution or another.

## Who's reading? Who's writing?

Does the wiki give you statistics you can use to figure out who knows more about a certain topic? GitHub can enable you to see which contributors are working on a particular part of the software project which can help with documentation needs. Wikis can do this too, a reader was quick to point out, but my sense is that those wikis are truly CMSes and not "quick editors."

## Automation, the game-changer for docs-as-code workflows

Automated builds for review purposes are a huge gain with GitHub for documentation. While wikis have a simple save button per page, for some there is way to write scripts to automate translations or glossary re-use. Now, the more advanced and integrated wikis are certainly moving in this direction, and may sway you away from your static site generator towards a content management wiki. Wikis can be very box-like and rigid, while treating docs like code lets you automate more tasks than simply "render and publish HTML." These statements are not meant to provide final judgement on either platform.

## Information architecture, can you get what you want and release?

Wikis are quite page-oriented, and in order to do releases, you might need to publish a page twice, using namespaces for example, if information affects two releases. With GitHub, you can backport a change from one release to another using branches and a similar pull request and review workflow.

## Reviews

Wikis often have add-ons for review workflows, but when the heart of a wiki is quick editing, people will not easily switch to a review workflow within a wiki while in GitHub it's expected to let others review your changes before merging, or publishing in the case of a document.

Sprawl can be a problem with both solutions, but the organized nature of code near documentation seems to keep the two in lock-step when the docs and code share systems such as version control and review workflows.

## Design and experiences

When publishing an entire site using static sites, you get more flexibility in choosing web designs and navigation than many heavily-opinionated wiki frameworks. That said, if your web development resources know a particular wiki framework really well, they may create a nicer end-user experience in a wiki  than in a highly-flexible web framework like Sphinx or Jekyll.

Wikis may have a reputation built up over time with a lack of discipline in editing a page instead of starting a new page, and in gaining trusted information that can be found easily.

## Bringing it home

Even as I wrote back to Gene to answer his questions, and even as I incorporated the answers into the _Docs Like Code_ book, I continue to be challenged with my answers and to reconsider some of them. Tools come and go, and our ability as professional writers remains and shines: provide the best critical analysis of the content management tools, and then write and manage the heck out of the content and the talent that creates and maintains it.

{% include sign-up.html %}
