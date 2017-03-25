---
layout: post
title: Case Study - Symantec, Jennifer Rondeau
excerpt: "Jennifer Rondeau, Technical Writing Manager at Capital One, talks about her experiences as a Principal Information Developer at Symantec integrating code and documentation tightly."
modified: Sat Mar 25 15:51:58 CDT 2017
categories: articles
author: jennifer_rondeau
tags: [case study, javadoc, doxygen, use case, github, docs, repos, workflows, tools]
image:
  feature: ehktang-yellow-reflection.jpg
  credit: Flickr ehktang
  creditlink: https://flic.kr/p/bpTk6k
comments: true
share: true
---

# Use Case: Symantec

The team I was assigned to as the technical writer was building SOAP web services for remote management of an installed enterprise security server.

Spoiler alert: the story isn't quite about docs AS code &mdash; it's more about docs *from* code, but I hope it's still useful in world where documentation and code are still trying to figure out just what their relationship ought to be.

The docs aren't published to a site; they're built separately and provided as part of the server build. This is true for both the project that I describe here, documenting web services, and for the larger GUI-based admin server docs.

Symantec uses primarily a documentation management system that only the writers have access to. Content is authored in DITA-inflected DocBook XML, using a WYSIGYG editor for topics and a drag-and-drop GUI for single-sourcing multiple deliverables from the same source files. The deliverables are checked into version control (Perforce) and picked up by the product server at build time.

For web services, we needed something that would let the writer (me, in this case) work more closely with the code, and with developers. The project was written in Java, so Javadoc turned out to be the answer. The rest of this story is about how we dealt with the Javadoc, and what it ultimately meant for our whole writing team.

## What we built

We built Javadoc output using doxygen. Doxygen was already the tool of choice for code documentation because the very large codebase was written mostly in Java for the server, and in C and C++ for the client. Doxygen meant that dev could run the doc tool over the entire codebase, instead of different tools for client and server.

When I started on the project, it turned out that dev was unfamiliar with some best practices for Javadoc management. The lead architect had put a basic doxyfile (the doxygen config file) in place and written out a stub main page intended primarily for an audience of internal developers and testers. We needed something suitable for external developers and system administrators. So I took over everything, where "everything" meant:

* maintaining the doxyfile
* writing and editing the Javadoc comments
* creating package-level comment files, and then writing the content for them

We planned to incorporate the doc build into the server build, but for lack of time to set me up completely with a working dev environment, we abandoned that approach. We did use some code and build tools for the doc, however; see below for details.

The Javadoc output was relatively small &mdash; about 50 pages of doc content total (plus the inevitable helper files).

## Why we chose these techniques

First, let me specify what I'm thinking of as a technique:

* Writer primarily responsible for all aspects of creating doc content in the code, getting content reviewed, and building docs &mdash; this happened because I was already so familiar with the Javadoc workflow, and because doxygen has a pretty flat learning curve. Everyone on the team also worked very closely together, so there was a high level of mutual trust from the beginning. We also had a stellar PM who encouraged us all to explore new things.

* Manual doc build: this happened because the time to set up a complete dev environment was at the time so great. I did use all the dev tools, with an otherwise identical-to-dev workflow: Eclipse for editing code comments, Code Collaborator for review, TeamCity to check that my changes to code files weren't breaking the server build, and Perforce for version control. The one thing I did not do was to build the server locally before doing a personal build on TeamCity (this is a build that lets TeamCity pick up your local changes before they're checked into version control).

* Writer use of dev tools and environment for the work: because the doc content was in the code, this only made sense. It's much easier to explore code and figure out what needs to be documented in comments if you've got a good code explorer to work in; it's easier to get reviews done as part of the code review process; TeamCity let me check that my changes wouldn't break the server builds; and version control ... well, the doc content was living in the code, not just with it, so it had to go into version control. All of our doc content, though, was always checked into version control at some point, including all the HTML and PDF deliverables that were generated from our silo'd doc management system. The difference with this project is that the doc source content was actually in the code, and the server picked up the doc build in a separate process.

## Audience considerations

We needed a writer to own these docs because the audience was not quite like the developers who were writing the code. Good projects also recognize that someone who makes a thing isn't necessarily the best person to explain the thing.

As the writer, however, I was unusually involved with potential customers for the web services we were building. These customers write remote monitoring and management applications for providers of small business solutions. The applications integrate with provisioning, development, and security solutions, including Symantec's Endpoint Protection. I went on one offsite customer visit with the program manager and product manager, and I listened in on long calls with other customers. I learned the third-party management tools that were looking to integrate with our web services, so as to understand better just what our audience of developers and system administrators really needed to do with our product. (As it turned out, our primary customers, system and security administrators of larger enterprises, were also interested in our web services to let them write custom management solutions.)

But I also had an internal audience, namely the developers who were writing the code. During the second iteration of the project &mdash; an extension of the original set of web services &mdash; we were more tightly organized into an agile scrum team. I attended standups, helped plan sprints, and sometimes wrote comments ahead of the code, based on discussions with the rest of the team and on my familiarity with the basic server functionality that we were exposing with the web services.

Our readers did not typically write with us, but for this project there was a lot of interaction between key customers/audience and the entire product team including the writer.

We also didn't really have a review queue: we updated the docs on a rolling basis during development, building as needed for review before integration into the server, and publishing as part of the server release (typically twice a year). No CI/CD.

## Reviews

We did doc reviews as part of the code review process. Whenever dev touched the web services code or the comments, I was automatically added to the required code review. Whenever I touched comments (or occasionally code, for naming or for error messages), I spun up a code review in Code Collaborator.

We had review checklists that had to be completed before reviewers could sign off. We also integrated code reviews and version control, so that noone could check code files in without a review first. And since the doc was literally part of the code, it also had to be reviewed before it could be checked in.

## Publishing

The complete doc set (we called it an SDK) included the following items:

* The Javadoc build, which I did manually (as noted above).
* An integration guide, which I wrote and published separately using our documentation management system.
* Sample PowerShell code for all the web services plus OAuth, which I wrote based on test scripts. The code samples were also heavily annotated, since that's the most common place any dev starts with integrating a service or library. They were reviewed separately, but using the same process as above.
* Static WSDL files, which were generated automatically during server build (third-party developers could also generate them from their own server installs).

The server picked up the first three items were picked up from the SDK folder in version control at build time, and added the WSDL files automatically.

## Automation

All the writer contributions to the doc/SDK were built manually, but pickup was automated.

## Version control and workflow

The overall workflow looked like this, after environment setup:

* Get latest code files from version control (Perforce)
* Edit or create Javadoc comments, package-info files
* Edit main page content as necessary (for example, when we added new services)
* Check out changed files as needed
* Submit changes for code review
* Respond to any code review comments/edit
* Build with writer changes on TeamCity
* Check Javadoc build out of version control (this could happen earlier or later, too, but obviously before checking new build back in)
* After TeamCity build passed, manually build Javadoc
* Check Javadoc build for obvious errors, fix, rebuild
* Check code files and doc build back into version control, merging diffs as needed

Version control was "optimistic," with multiple people working on the same files at the same time (see preceding list). This could occasionally produce gnarly merges, especially because writers are used to working on content over a period of time. But generally it wasn't a big problem. I would keep the Javadoc main page checked out for a while because I was the only person working on it, but generally I'd try to work on (and therefore check out) a small set of code files that I could manage through to checkin before anyone else needed to work on them.

## Benefits

There were two different kinds of benefit, as I see it:

* Having a writer work on code documentation meant that the docs were better focused on the needs of an external audience. Our entire doc team worked on different aspects of the product as primary user advocate &mdash; code docs were no exception.

* Having the web services docs tightly integrated into the code as part of the comments meant that they always got the attention of the entire product team.

The biggest overall win, though, came from the communication between dev and doc that sharing a workflow created. There simply couldn't be such a thing as an undocumented feature. And in some cases writer questions about what was going on with an error message, for example, produced better error handling generally. I was also able to catch some potential security issues, for example when a set of enums was initially called from the implementation code, potentially exposing black box functionality. The enums had to be documented for the web services, and so the team reluctantly realized that we'd have to violate DRY principles to expose the enums appropriately.

## Cautionary tales

Doc management was continually concerned that putting a writer into the code &mdash; writing code comments and code samples &mdash; would set inappropriate expectations of the writers. In other words, dev would come to rely too heavily on writers for work that devs should be responsible for. I never found this to be the case in practice &mdash; I was a member of a team and we all contributed and learned from each other in much the same way as when we worked together on GUI-based design and doc. If an API was hard to document, I'd ask about it just as I'd ask about difficult UI text or workflow, and the team would discuss possible alternatives to make the design work better. The same kind of thing happened with test scripts and the sample code that I wrote &mdash; if I had trouble parsing a series of API calls, I'd ask whether that was the best way to test them, and we'd have a conversation about the issue.

The web services project was pretty well contained, too &mdash; I continued to work on other aspects of the server docs &mdash; and in fact there was quite a lot of code savvy on our docs team as a whole that management had previously been unaware of. So there were other writers who could contribute to developer docs in much the same way that I did, although "replacing" me was a lesser concern.

The biggest difficulty came when we moved from SOAP to REST. Code comments don't work so well as source content for REST web services documentation, and it took us a while to figure out what to use instead. The tooling that we eventually settled on, spring-restdocs, required even tighter integration of dev and doc effort because the main doc files are written by hand, but the example requests and responses are generated from a documentation method that's added to the mock tests. So dev has to write the test method, either dev or the writer creates the main source files that include the examples, and then any reference information must be maintained manually outside the code, but within the code framework. These issues were still being addressed when I left the company.

Generally the kind of approach that we took is at least initially writer-intensive, and therefore not extensible without careful planning and attention to the nuances of load balancing. For the first set of web services that we shipped, I worked on the project full-time. For updates the following year, we had enough of a system in place that I could work on the updates about half time. But juggling a developer workflow and a separate documentation workflow was quite a challenge, especially when I came back to the developer workflow after nearly a year of work in the separate doc flow. Developer tools and configurations had changed, and I had to learn them all over again. I don't necessarily recommend an all-or-nothing approach (all developer tools all the time or else none), but it's important for everyone &mdash; doc teams and dev teams &mdash; to understand the difficulties of jumping into and out of different workflows and toolchains. 

## What you wish you knew

The biggest thing we didn't do was integrate the Javadoc build completely into the server build. Doing so would have required an investment of time and effort up front plus ongoing time and work to build the entire server locally, so we decided that it wasn't worth the large up-front effort to integrate and have the writer working completely in the dev workflow. That said, automated builds would not only have saved writer time and effort, they would also have saved the occasional server build break (when the built docs caused the break, because they weren't part of the server tests), and they would also have guaranteed up-to-date Javadocs.

On the other hand, because other doc components besides the Javadoc could only be built manually, more automation could have solved only part of the problem of keeping content up-to-date on the server. Ultimately, the decision not to automate the Javadoc made sense &mdash; there are always pain points on either side of a decision like this.

We also didn't realize initially that we'd have to coordinate our doxygen build, which ran over only a small subset of the code, with multiple other doxygen builds over other parts of the code tree. I wound up working with lead devs on other coding projects to coordinate main page markup and config values so that we could all get the doc builds that we needed. This work was a bit fiddly, and produced an extra round of review with every Javadoc build to make sure that the right components were all properly included. 

{% include sign-up.html %}

