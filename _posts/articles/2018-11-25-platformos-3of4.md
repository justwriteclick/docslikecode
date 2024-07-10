---
layout: post
title: "Building Our Documentation Site on platformOS — Part 3: Community"
excerpt: Welcome to part 3 of our article series where we explore how we collaborate with our community.
last_modified_at: Thu Nov 25 22:01:44 CDT 2018
categories: articles
author: diana_lakatos
tags: [developer documentation, contributor experience, community, style guide, templates, editorial workflow, docs, documentation]
image:
  path: /images/platformos/platformos_part3/part3_cover.jpg
  caption: "[Courtesy platformOS Blog](https://www.platformos.com/blog/post/building-our-documentation-site-on-platformos-part-3-community)"
comments: false
share: true
---

In this [article series](/articles/platformos-1of4) we describe the process of building the [platformOS documentation site](https://documentation.platformos.com/) from discovery to development, with in-depth insights into our approach, decisions, plans, and technical implementation. Welcome to part 3, where we explore how we collaborate with our community. 

# Community-driven documentation

Knowing our target audience is key to great documentation, so being able to get to know our users and directly communicate with them is a huge advantage. As we have an amazing relationship with our community, we decided to involve them in all phases and aspects of our documentation process. 

Engaging them early on in an agile and iterative process ensured that we can test and validate all of our assumptions, and quickly modify anything if needed. This is a time and cost-efficient approach: Although we edit and rewrite our content and change things on our documentation site all the time, we don’t run the risk of creating large chunks of work that have to be thrown away because they don’t correspond to the needs of our users. 

Constant collaboration also builds trust: as our process is completely transparent, our community continuously sees what we’re working on and how our docs evolve, and community members can be sure that their opinions are heard and acted upon. 

Involving the community from an early stage means that our users will see lots of stuff that’s partially done, missing, or will be totally rewritten. So, for all of this to work, our users have to be mature enough to give feedback on half-done content. 

## Contributor Experience

We’d like to serve a diverse, highly motivated, active community, and provide everything they need to contribute to our documentation. To find the most fitting tools and workflow, we had to think about contributor experience (CX) first, and explore what makes a great CX when contributing to documentation. Here are the aspects we considered and how we addressed them:

* **Ease of getting on board**: We describe ways for our community members to get involved in our contributor guide. We made the guide as short as possible (less than a page) with links to relevant content (e.g. style guide, templates).   
* **Entry points for different types of contributors**: We wanted to make it very easy to get involved for all segments of our target audience, so we offer different ways to contribute both regarding the time contributors have to put in and the skill level they need. 
  * For quick feedback, we added a feedback block at the bottom of each documentation page, where the minimum input is clicking on a smiley, but users can answer a question and share their suggestions, too. 
  * For some quick editing, like fixing typos or adding links, contributors can edit the content easily on the GitHub UI. 
  * For heavy editing, adding new content, or developers who prefer to use git, we provide a complete docs as code workflow.  
* **Clear expectations**: We know it’s easier to get started on editing or writing a topic with clear guidelines to follow. Our [style guide](https://documentation.platformos.com/style-guide/documentation-style-guide) contains guidelines for writing technical content (e.g. language, tone, etc.) and each content type in our documentation (e.g. tutorials, concept topics, etc.). 
* **Ease of contribution**: To make contribution easier and to keep content on our documentation site consistent, we created [templates](https://github.com/mdyd-dev/nearme-documentation/tree/master/marketplace_builder/views/pages/doc-templates) for all content types. The templates provide an outline and instructions that contributors can follow.  
* **Clear workflow**: We developed an editorial workflow that works for both internal and external contributors, and ensures that contributors get quick and precise feedback. 
* **Familiar tools**: We chose a tool that most of our target audience is familiar with, GitHub. As our users usually already use git or some other version-control system, extending its use to external content contributors was a logical step. 
* **Appreciation**: We thank all of our contributors, and display them on our GitHub repository’s README page, and on each topic on the documentation page. 

![](/images/platformos/platformos_part3/contributors.png)  

_Contributors displayed on a documentation topic_

# Communication

In order to encourage collaboration and keep our community up-to-date with what we’re doing, we are consciously building and extending our channels of communication. We provide different types of communication channels (asynchronous, real-time, face-to-face, etc.) to accommodate community members with different schedules and communication styles. 

## Slack channel 

Our main communication channel for now is a dedicated Slack channel, where community members **ask questions, share ideas, and get to know our team members and each other**.

Here, they can ask questions about anything related to platformOS, and someone from our team, or another community member who has the answer will jump in to reply. We get a wide variety of questions from business related enquiries like pricing to specific questions about development.

This is also the place where both we and our community members **share news**. We let them know of new **features planned, bugs fixed, articles posted, and new docs added, and they show what they’re building on platformOS**. This constant exchange of information is extremely valuable for all involved: community members can share what they’ve learned, plan their module development in sync with our roadmap and each other’s projects, and allocate their resources according to what’s going on in the business and the wider community.   

The Slack channel also provides a great opportunity for community members to start conversations, share relevant news and articles, and engage with like-minded professionals.

![](/images/platformos/platformos_part3/slack.png)  

_A conversation in our Slack channel_

Being actively involved with the community through the Slack channel helps us see how to shape our documentation. Questions are good indicators of what needs to be documented, and when we share news of new topics added to our docs or our plans for future changes, we can get immediate feedback. 

## Documentation Status Reports

To keep our community up-to-date with the work on our documentation, we share weekly status reports each Monday. The status reports include what we’ve been working on the previous week, what topics we added, what we are planning and any other news regarding our documentation. 

The status reports were a request from the community to have a regular digest of what’s going on. Based on further requests, we now also send the reports to subscribers as a newsletter (through our SendGrid integration), so that they can easily access them in their mailboxes and share them with their developer teams. 

![](/images/platformos/platformos_part3/status_report.png) 

_A documentation status report in our Slack channel_

## Weekly video conferencing 

Initiated by our community, Town Hall is a weekly video conference over [Zoom](https://zoom.us/), where community members and the platformOS team share news, demo features and modules, and have the opportunity to engage in real-time, face-to-face conversation. 

Our team and community members are distributed over different continents, so we try to accommodate participants in different time zones by rotating the time of this event so that everyone has the chance to participate. We also share the recording of each meeting. 

![](/images/platformos/platformos_part3/town_hall.jpg) 

_Town Hall meeting: A community member demoing an application he developed on platformOS_

## Surveys

Besides getting constant feedback from the community through the channels described above, we plan regular checkpoints in our process to facilitate testing and course-correction. During development, we tie these checkpoints to development phases. At the end of each larger release, we compile and share a short survey for community members to fill out. 

Our documentation site is in alpha now, so we’ve had our first survey round a couple of weeks ago. We put together a short 10 item questionnaire collecting both quantitative and qualitative data. 

* The 5 quantitative questions showed an average value to help us identify how much users like the whole site, the information structure, and the performance, and how they would rate understandability and trustworthiness. We are planning to reuse these questions in later questionnaires to compare the results and validate how our changes affected user satisfaction. These questions are also benchmarked by SurveyMonkey, which allows us to compare our results to others who used the same website feedback questions.
* We also included 5 qualitative questions to explore the reasons behind the scores of the quantitative ones. Our main goal was to have a general idea of how users think about the site. The results helped us identify what they’d like to keep, what we should change, and highlighted areas to focus on.

Based on our community members’ feedback and the results of our first questionnaire, we compiled a list of tasks and a roadmap for the beta phase, that includes a reorganization of main sections, subsections and topics, rewriting and editing topics, content production with a well-defined focus, and a couple of new features for the documentation site. 

We are dedicated to engaging community members further as we are working on these next steps. For example, we started the reorganization with compiling a plan for the new content structure based on the feedback we received, but also asked if any community members would be interested in providing their ideas and reviewing ours. Two members got actively involved, and shared their opinions on our plan. We fine-tuned the plan in a call with them, making significant changes based on their valuable insights. Having the opportunity to directly collaborate with members of our target audience gave us a chance to quickly and easily verify our ideas, and work out an approach that would best suit our users’ needs. Once done, we shared the plan with our community to see what they think about it. Reorganization started based on this plan that many contributed to and everyone agreed on. 

# Future plans

As our community grows, we are preparing to scale with it. Here are some of our plans for next year: 

* **Topic wish list**: A feature that allows community members to add topics they’d like to see documented.
* **Voting on topics**: Vote on topics, and we will start working on the topics with the most votes.
* **Community site**: Our community members are active on many channels now, including on some of their own initiatives, like an Airtable for keeping track of community members, questions and answers, and community activities. Although it works for now, we are planning to give the platformOS community a home — a site similar to Intel Devmesh, a developer community site we built for Intel on platformOS.
* **Community Manager**: In the near future, we are hiring a Community Manager to give the platformOS community dedicated attention from an experienced professional.
* **Gamification**: After building a solid user flow, we are planning to  strengthen it with gamification elements to help and reward the user’s journey from onboarding to mastering the site. 
* **Devcon**: We are planning a platformOS Devcon for 2019, a proper get-together for our community members with workshops and presentations by our team members and experienced members of our community.

Now that you’ve seen how we discovered the needs of our target audience, planned content and layout for our documentation site, and connected with our community, all that’s left from our series is to show you how we implemented our documentation site on platformOS. See you again in part 4! 

_We involved [UX Strategist Katalin Nagygyörgy](https://www.linkedin.com/in/nagygyorgykatalin/) in our process from the start. Through our collaboration, we could extract and collect all the necessary information using tried and true research methodologies and UX best practices._

_This article was originally written for the [platformOS Blog](https://www.platformos.com/blog/post/building-our-documentation-site-on-platformos-part-3-community)._
