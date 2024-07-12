---
layout: post
title: Ten tips for maintaining a long-term relationship with docs like code
excerpt: "Learn about one team's journey to keep a long-term relationship with their docs-like-code system, TechDocs, which is open source and available to all."
last_modified_at: Fri Nov  6 20:47:45 CST 2020
categories: articles
author: gary_niemen
tags: [cicd, backstage, spotify, GitHub, git, portal, internal, documentation, developer, docs]
image:
  path: /images/spotify/soundboard-han.ailes.jpg
  caption: "[Flickr han.ailes](https://flic.kr/p/oVPTVm)"
comments: false
share: true
---

I remember about two years ago sitting here watching a Write the Docs video. Well, not precisely “here” because we sat in offices in those days and in 2020 I'm in my home office. I was watching, wide-eyed and a bit confused, a video of [Riona MacNamara’s talk from Write the Docs 2015](https://youtu.be/EnB8GtPuauw). In the talk, Riona described how she and another technical writer used a docs-like-code approach to change Google engineering culture around technical documentation.

I remember seeing this adoption curve and saying to myself: We need to do this. I want that curve.

![running total: projects & authors from Documentation, Disrupted ](/images/spotify/adoption1.png)

And just a few months later, we had built and released TechDocs, Spotify’s docs-like-code solution for internal technical documentation. And a few months after that, we had the curve that I had longed for. Nice gradient, eh?

![Adoption Stats](/images/spotify/adoption2.png)

 If you haven't heard of it, Spotify is a digital music, podcast, and video streaming service providing access to content from artists around the world. We were fortunate in that there were several synchronous moments that helped us, but overall, we moved fast because we were able to make use of preexisting infrastructure, such as [Backstage](https://backstage.io/) (our homegrown and now open sourced developer portal) and Tingle, Spotify’s CI/CD tool. We also made use of the open source static site generator, [MkDocs](https://www.mkdocs.org/).

In just two short years, writing docs in Markdown in our enterprise version of GitHub has become standard practice. We have over 3,000 doc sites from across the organisation, all showing up and searchable in Backstage. And most of the feedback we get from engineers is positive with the odd request for a small tweak or improvement.

![TechDocs Documentation screenshot](/images/spotify/techdocs.png)

Time to put our feet up, right?

Not quite. We have outlasted the honeymoon period, moved past the one-year anniversary, and now suddenly find ourselves in the territory of a long-term relationship. Now is definitely not the time to take anything for granted.

So, with that in mind: here are 10 tips for keeping your long-term relationship with docs like code thriving:

## 1. Keep fiercely optimizing for engineers

One of the keys to our success has been our commitment to fiercely optimize for engineers by creating a documentation infrastructure fully aligned with the existing engineering workflow. Well, that’s what docs like code is all about, right? But one can easily be swayed.

Can we use Jira instead of GitHub to report issues? Can we use a Google Doc and embed it into TechDocs? Can we use Lucid Charts for diagrams instead of PlantUML? Is it possible to have our source in Markdown in GitHub and get it to show up in Confluence?

Some of these requests were from non-engineers and some from engineers. Whatever the case, our stance is always the same: Continue to optimize for engineers and the engineering workflow.

## 2. Sanctify the frictionless experience

Another key factor for us was making sure that the workflow from authoring in Markdown to a nice-looking website in Backstage is a frictionless experience. Everything just works.

We have had requests to add metadata to .yaml files, break the build if doc sites fail, and a bunch of other workflow-breaking extras — but each time we have resisted and prioritized the frictionless experience.

We have even pushed the frictionless experience further by including docs setup when software components are created in Backstage and removing various MkDocs configuration requirements.

## 3. Have an opinionated position, and hold onto it

Very early on, we boldly said to Spotify’s tech community: *TechDocs is now the one way to produce documentation, and Backstage is now the one place to find and consume it*. Then we ducked. But no missiles came our way, and we got it through. I think the organisation was ripe for this standardisation, having become totally fed up with documentation being distributed across so many places, such as Confluence, Google Docs, README files, GitHub Pages, and various websites.

What I would say is this: Hold onto the opinionated position. It’s one of the keys to success and should be a kind of guiding light as you move forward with your docs-like-code solution.

## 4. Beware of second-order effects

I have been thinking about second-order effects a lot recently. We make what we think is a good decision and then hey-ho, a few days or a week later, negative consequences of that decision start to emerge. What do we do? Do we reverse the decision? Do we tweak it? Do we try to address the new negative consequences? Or do we carry on regardless? Working with product — as in life — it’s important to consider second-, third-, and nth-order effects. Here is a [great piece on the topic](https://fs.blog/2016/04/second-order-thinking/). (Aside: I wonder to myself sometimes if the whole history of humankind is not an nth-order effect.)

We’ve fallen victim to second-order effects a number of times. Here’s one:

We adjusted the reading width in Backstage to fall in line with accessibility guidelines. What could go wrong there? Plenty, it turns out. The reading width becomes too narrow when the font is small. Wide tables need a scroll bar, and that makes them less readable. And the narrower reading frame looks weird on a large computer screen. Support questions rolled in and…rolled in — taking up a great chunk of our engineers’ time. From peace, we had created chaos.

Beware of second-order effects.

## 5. TechDocs is great, but please fix search

The first big argument after the honeymoon period was about finding stuff. To paraphrase two and a half pages of feedback: “TechDocs is great, but please fix search.”

I get this. It is all very well and good having all of your technical documentation in one place, but if you can’t find it — well, what’s the use? The opposite is also true, by the way. If you have a great search engine but what you find is out of date or of low quality, then again — what’s the use? So, we listened to our users and are now working to improve search success.

## 6. Don’t rely on vanity metrics; establish actionable metrics and watch them instead

In the early days, we were all about adoption. “Hey Gary, we are up to 200 sites.” “Hey Emma, it’s 500 sites now.” “We are up to 1,000 sites, let’s celebrate!” We just wanted that nice upward slope. But as time went on, we started to see that really, the number of doc sites was little more than a vanity metric. So we started to think more deeply about which metrics would be more useful to track. This is still a work in progress, but our top metrics at the moment are:

* Total visits
* Number of actual doc updates
* Issues and open PRs around docs
* Successful searches

We also send out a short survey every six months to gauge if TechDocs is helping engineers get unstuck faster, check whether we are moving people away from other documentation platforms, and fish for general feedback.  

## 7. Use the feedback loop to maintain doc quality

Before we introduced our docs-like-code solution TechDocs, an often-heard complaint from engineers was: *I don’t know where to find information, and if I do find it, I don’t know if it is up to date*. With the introduction of TechDocs, this complaint vanished. There was now one place to find information. Plus, teams migrated their existing content onto the platform and started creating new content on it, so there was a sense that now, not only was everything in one place, but everything was up to date as well. Nirvana.

But (yes, of course, there is a but), as time went on, the “I don’t know if it is up to date,” complaint began to reemerge. And, to be honest, we kind of knew this was going to happen. We don’t have technical writers watching over the documentation; that simply doesn’t scale. So we knew we needed some other way to keep the doc quality up.

The way we do this is to try and nurture a thriving community of technical documentation producers, contributors, and consumers. And we do this by building up a free-flowing feedback loop. In other words, we make it easy for consumers of documentation to contribute or give feedback. We then make sure that the contributions or feedback gets to the right teams and that those teams are, in some way, incentivized to make the suggested updates. Then, to complete the loop, the ones who gave the feedback are notified that it has been addressed.

## 8. Give teams data on their doc sites

Just as it is important that teams know what software they own, it is equally important that they know what documentation they own. Giving our teams this functionality was a key factor in making the long-term relationship work (kind of a one-year anniversary gift). On a nice-looking dashboard, teams can see which doc sites they own or part own, when they were last updated, and number of GitHub Issues per doc site. We have heaps of ideas for more data we could add — just to keep the relationship fresh, of course.

## 9. Productify your tech-writer knowledge and experience

Early on, we made the bold decision to move our tech writers up the stack. In other words: build a team of tech writers and engineers, and build a tool to scale and solve technical documentation at Spotify. The tech writers would instill their knowledge and experience into the product. But they wouldn’t do any actual technical writing. And that’s basically what we have done.

We rely on crowdsourcing and the feedback loop (as described above) to keep overall doc quality high. Our tech writers don’t review technical documentation.

However, engineering teams do get word that we have tech writers stashed away on our team, and so we do get asked to help out with plenty of technical writing assignments. It is hard to say no sometimes, but overall we have managed to stick to our initial strategy:

What we do offer is:

* A one-hour introduction to technical writing at Spotify.
* A one-hour “consultancy” meeting with the team.
* A support channel for smaller questions.
* Document templates.
* A technical writing handbook that includes a style guide.

We believe for a company the size of Spotify, this approach is the only way to scale quality technical documentation.

## 10. Commit to docs like code and keep committing

At Spotify, we have this key onboarding documentation called Golden Path tutorials. You can read about them here: [How we use Golden Paths to solve fragmentation in our software ecosystem](https://engineering.atspotify.com/2020/08/17/how-we-use-golden-paths-to-solve-fragmentation-in-our-software-ecosystem/). They present a great challenge to a docs-like-code solution because they are large, owned by multiple teams, and have many dependencies. In addition, we have one tutorial for each engineering discipline (for example, backend, data, web, etc.) and it’s crucial that the various tutorials play well together.

These tutorials used to be in Google Docs and people used to very much appreciate this format in particular the strong commenting features. We could have easily opted to keep the Golden Path tutorials in Google Docs, but we had committed to docs like code and we wanted to go all in. I remember our product manager at the time saying something like: If we can make this work for the Golden Path tutorials, it will help us solve for all other technical documentation at Spotify.

So we implemented the tutorials in TechDocs, use the [CODEOWNERS](https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/about-code-owners) file to keep track of ownership, and set up a special GitHub bot to handle notifications when GitHub Issues are raised. We are also starting to take it even further by exploring ways that we can use tooling to help teams keep track of the documentation dependencies found in the tutorials.

---

So that’s about it. There’s your long-term relationship advice. Not bad for a bunch of techies eh?

One last note to let you know that **we have now open sourced TechDocs**. Let’s take TechDocs to the next level together. Everything you need to know, you’ll find in the blog post [Announcing TechDocs: Spotify’s docs-like-code plugin for Backstage](https://backstage.io/blog/2020/09/08/announcing-tech-docs).

### Resources

* [TechDocs Documentation](https://backstage.io/docs/features/techdocs/techdocs-overview)
* [Frontend code for TechDocs](https://github.com/backstage/backstage/tree/master/plugins/techdocs)
* [Backend code for TechDocs](https://github.com/backstage/backstage/tree/master/plugins/techdocs-backend)
* Tools for TechDocs: [techdocs-cli](https://github.com/backstage/techdocs-cli) and [techdocs-container](https://github.com/backstage/techdocs-container)
* [MkDocs](https://www.mkdocs.org/), a static site generator
* [Markdown Guide](https://www.markdownguide.org/)
* [Backstage](https://backstage.io), an open platform for building developer portals
* [github.com/backstage](https://github.com/backstage/backstage)
* [DevRelCon London, December 2019: Gary Niemen, The Hero’s Journey: How we are solving internal technical documentation at Spotify](https://www.linkedin.com/posts/garyniemen_how-we-are-solving-internal-technical-documentation-activity-6646078605594030080-4L31)
