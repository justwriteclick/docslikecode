---
layout: post
title: "Adopting Docs-as-Code: From Hackathon to Production"
excerpt: Sysdig's journey from unstructured to structured, finally to semi-structured authoring and how Sysdig hackathon enabled design their homegrown docs-like-code solution.
last_modified_at: 
categories: articles
author: radhikapc
tags: [cicd, sysdig, docker, docs, Hugo, Go]
image:
  path: /images/sysdig/sysdig-banner.png
  caption: "[Courtesy Sysdig blog](https://sysdig.com/blog/adopting-docs-as-code/)"
comments: false
share: true
---

Originally published in the [Sysdig Blog](https://sysdig.com/blog/adopting-docs-as-code/). 

Thanks to the yearly Hackathons at Sysdig, we’ve recently democratized documentation creation by embracing the docs-as-code philosophy. Similar to our source code practices, product documentation has been version controlled, subjected to the same gatekeeping systems, and auto-delivered by using the same CI/CD pipeline.

![](/images/sysdig/sysdig-process.png)


In this article, you’ll read about the journey of Sysdig documentation. You will also learn how we finally arrived at the current scheme of things, how it enables us to be effective and productive at work, ultimately helping customers win.

## Why Doc-as-Code?

We have witnessed a sudden surge in the number of subject matter experts that are enthusiastic about contributing to documentation while our existing authoring tools failed to meet contributors’ requirements. Because our contributors span from developers to product managers and support teams, we felt it’s advantageous to integrate our authoring system into the developer workflow to enable smooth collaboration.

## The Journey: Unstructured to Structured to Semi-Structured

We have tried a bunch of different ways to handle public documentation over the years before embarking on the GitHub way. All the previous tried-and-tested systems have proved either restricted or ill-fitting for our requirements, be it a structured or unstructured tool.

Sysdig documentation was initialized as a bunch of [Zendesk](https://support.zendesk.com/hc/en-us/articles/4408839258778) articles. As the product suits evolved and the proliferation of content became unmanageable, we required a content management system optimized for collaboration. Because Sysdig uses [Confluence](https://support.atlassian.com/confluence-cloud/docs/create-and-edit-content/) for internal documentation, the next logical step was to switch to Confluence.

Confluence came up with its own challenges. The version we were using missed most of the enterprise features, including topic reuse, version control, and the facility to customize the pages according to Sysdig branding. At the time, both content development and documentation tooling had been managed entirely by the documentation team.

| Confluence Advantages     | Confluence Disadvantages                       |
| ------------------------- | ---------------------------------------------- |
| Cost                      | Limited branding / customization options       |
| Ease of use for authoring | Inability to reuse topics                      |
| Ease of contribution      | Limited  versioning/content management options |

In order to adopt a Sysdig look and feel for the documentation site, we arrived at a decision to jettison it for an Enterprise authoring and content management system with specialized support. And we chose Paligo.

[Paligo](https://paligo.net/product/), an XML-based authoring & content management system, offered most of the functionalities for the Enterprise. However, it missed an integrated-hosting service with version control. We had to build a GitHub- and static site-based workflow for versioning and publishing, which implies we were, in part, already into the Doc-as-Code system. Besides, the XML-based contributor interface became a hurdle to contributors external to the documentation team. And subject matter experts started to build content repositories for experiment features in GitHub and pulling that content into XML-based Paligo became a nightmare. To streamline content creation and allow for broader team contributions, the switch was inevitable.

| Paligo Advantages                    | Paligo Disdvantages                       |
| ------------------------------------ | ----------------------------------------- |
| Topic reuse                          | Collaboration hurdles                     |
| XML-based authoring                  | Unfriendly branching Interface            |
| Localization support                 | Unfriendly reviewer/contributor interface |
| Enterprise-level support from Paligo | No markdown support                       |
| Branching/staging                    | No hosting services                       |
| Enhanced search                      |                                           |
| Content management                   |                                           |

In short, if Zendesk articles worked well for the support organization, it was not fit for complete end-to-end product documentation. If Confluence worked very well for doc contributors, it was way too conventional to retain versions or follow Sysdig branding. No one system ever seemed to satisfy all our requirements.

## Hackathon Effect

A Hackathon is a time-boxed event in which cross-functional teams work on creative ideas. Sysdig conducts a yearly Hackathon fest where employees can propose innovative ideas and collaborate with colleagues who they don’t otherwise get to work closely with.

The impossible becomes possible with the Sysdig Hackathon. Our team proposed the idea of porting the XML content in Paligo to the Doc-as-Code scheme using an innovative in-house tool.

As [Parkinson’s law](https://en.wikipedia.org/wiki/Parkinson's_law) states, “work expands so as to fill the time available for its completion.” Thanks to the Hackathon, the effort concluded with the content having been ported to Github in markdown format and having an aesthetic Hugo-Docsy-based website live.

### Conversion Tooling

Porting DocBook XML content in Paligo to Doc-as-Code-friendly markdown format required some level of automation, and the obvious choice for the conversion was `pandoc`. It is an open-source universal document converter that supports both DocBook and markdown. However, you cannot simply run a `pandoc` command and expect the XML to be converted into a desired form of markdown. Not all DocBook tags are easily convertible to markdown. There are many attributes that XML has and markdown does not, and on top of that, Paligo proprietary identifiers require different treatment.

Therefore, the focus of the Hackathon team was to refine the XML file prior to running the `pandoc` command, and post conversion, cleaning up the tags in the converted markdown files. Patching the XML file included, but was not limited to, replacing attributes with those that `pandoc` can identify. The post-conversion refinement dealt mostly with polishing how content is displayed on the website.

The result was a Python script to solve this problem and make the conversion automated.

### CI/CD Pipeline

We chose [Hugo](https://gohugo.io/) static site generator with [Docsy](https://www.docsy.dev/) theme for building the documentation website for its rich feature set. Hugo is faster, offers a rich feature set for expansion, and has an active community for support. Docsy offers features such as dark theme, RSS feed support, and swagger integration for APIs, which we plan to introduce to the site at some point. [Netlify](https://www.netlify.com/) is faster to launch and easier to integrate with Github repository for hosting preview and production builds. The publishing flow has been designed in such a way that each Pull Request would generate a preview build so reviewers can see the content as it would appear on the website. This mechanism accelerated our documentation publishing pace without sacrificing quality.

### From Docs-as-Code to Docs-from-Code

Our move to the docs-as-code scheme of things has not only enabled us to automate doc publishing, but also equipped us to automate doc development. Gaps in documentation mostly occur when modification of source code and documentation are not in sync. Unfortunately, this is typical when different people contribute to the code under a time crunch in project cycles.

The “doc-from-code” method that we devised tries to solve this case.

A part of our documentation is automated in such a way that content is generated by parsing the source code and configuration files in the projects. We developed a set of templates to parse the source code and render the content in the doc. The template is run periodically or when a new release is published. This process also generates an updated version of the docs and creates an automated pull request ready to be reviewed and published by the docs team. This ensures that documentation is always updated, no matter who contributes to the source code of our applications. Also, parsing code to generate docs saves time and resources, as well as makes our docs coherent in content and formatting.

Finally, one of the latest Hackathon projects iterated over this workflow to handle automating tooltip and documentation creation for the metric dictionary. Automating metric dictionary creation is expected to drive cross-functional teams to collaborate closely on improving metrics definitions and thereby eliminate manual errors and frictions that might otherwise be introduced to the path.

## Conclusion

In the new scheme of things, Sysdig documentation is stored and managed in GitHub alongside source code. The current authoring environment, built by gluing together SaaS products and OSS components, is collaboratively maintained by documentation and development teams. As a result, we decamped a licensed structured authoring tool that presented barriers to easy doc contributions.

| Docs-as-Code Advantages                   | Docs-as-Code Disadvantages                                   |
| ----------------------------------------- | ------------------------------------------------------------ |
| Tighter collaboration with SMEs           | We are still exploring and experimenting and will be back with our learnings! |
| Easy integration with Sysdig repositories |                                                              |
| Easier versioning branching for releases  |                                                              |
| Staging / Preview builds                  |                                                              |
| Enhanced search                           |                                                              |
| Dark mode                                 |                                                              |
| RSS feed                                  |                                                              |
| In-house doc infrastructure               |                                                              |

The switch has witnessed measurable success within a month of rolling out into production: the number of contributors has increased 15 times; the doc deployment time has been reduced to seconds. By eliminating manual review processes and introducing an automated web-based staging environment, doc publishing has been expedited. Docs-as-code also has enabled us to automate repetitive activities associated with documentation development. Above all, we have achieved shared ownership of developing and delivering quality content to help our customers succeed.