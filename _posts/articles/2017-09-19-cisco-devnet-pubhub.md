---
layout: post
title: DevOps-friendly Docs Publishing for APIs
excerpt: "From Mandy Whaley's presentation at All Day DevOps 2017."
last_modified_at: Tue Sep 29 13:36:15 CDT 2017
categories: articles
author: anne_gentle
tags: [documentation, docs, api, rest api, standards, openapi, raml, swagger, stripe]
image:
  path: /images/david-huang-366041.jpg
  caption: "[Photo by David Huang on Unsplash](https://unsplash.com/collections/964729/milky-way-galaxy?photo=R3E2kEIC-G4)"
comments: true
share: true
---

Here at Cisco, we have a developer program called DevNet that focuses on making Cisco APIs easier to use as well as work with developers and Cisco partners in many technology areas including IoT, Collaboration, and Software Defined Networking. The Cisco DevNet team loves working with developers, network administrators, and collaborators of all kinds. Mandy Whaley is the Director of Developer Experience for DevNet. I wanted to share details about Cisco's docs-like-code solution, PubHub, to publish both internally and externally here at Cisco. So, I used her presentation and dug into the technology as well. Here's the story of how PubHub was developed for publishing content for DevNet.

> APIs need great docs. Many organizations end up with a jungle of wiki pages,
> Swagger docs and API consoles, and maybe just a few secret documents trapped
> in chat room somewhere... Keeping docs updated and in sync with code can be a > challenge.
>
> We’ve been working on a project at Cisco DevNet to help solve this problem
> for engineering teams across Cisco.
>
> The goal is to create a forward looking developer and API doc publishing
> pipeline that:
>
> 1. Has a developer friendly editing flow.
>
> 2. Accepts many API spec formats (Swagger/OpenAPI, RAML, etc).
>
> 3. Supports long form documentation in markdown.
>
> 4. Is CI/CD pipeline friendly so that code and docs stay in sync.
>
> 5. Flexible enough to be used by a wide scope of teams and technologies.
>

What did the DevNet team come up with? Let's take a look.

## What site or sites do you create from a set of Git-based repositories?

The site is [developer.cisco.com](https://developer.cisco.com), and content comes from multiple repository sources, with multiple source types including markdown, RAML, and OpenAPI built with YAML or JSON.

There's also [learninglabs.cisco.com](https://learninglabs.cisco.com), which is also built from repositories containing markdown for content, and JSON files for navigation elements.

Plus, if a team wants to host content on their own site, the PubHub system provides links to content stored in S3 or any object storage system that can be embedded on a site. The technology that enables consistent display, styling, and seamless interaction across multiple sites and repos for all these rendered HTML snippets is a JavaScript SDK, the PubHub front-end SDK.

## What are the repositories that build the deliverables?

The repositories for [developer.cisco.com](https://developer.cisco.com) content are all private and hosted on an internal Enterprise GitHub installation, moved over from an internal GitLab installation originally. There are over 450 content repos stored privately and internally, meaning that you must work at Cisco and be invited to collaborate on a particular repo.

Some repositories are public, such as those for the [Learning Labs](https://learninglabs.cisco.com), so they can be browsed publically and patched by anyone on GitHub. There are nearly 200 repos for the DevNet organization itself, but those are not necessarily building learning labs, and the Learning Labs system can accept repos from any organization. There are over 300 Learning Labs available today including 25 written in Japanese.

## What factors led your team to choose a development approach for docs? Why and when was it chosen?

Around 2014, some members of the DevNet team, including Mandy Whaley and API evangelist Ashley Roach, saw a need to work across all of Cisco on API and developer needs. Mandy outlines the needs the development approach met quite well in her All Day DevOps talk: developer workflows for writing and editing, friendly to continuous integration and continuous deployment systems, and flexible enough to spread across all of Cisco as a centralized supporting system for API documentation.

## What type of audience are you writing for?

These sites are for all of Cisco's products, which vary from IoT (Internet of Things) to collaboration such as WebEx video conference, sophisticated phone systems with Voice Over IP (VOIP), Spark for enterprise chat, to cloud services such as Meraki, and of course our business base, networking products. The audience includes network administrators and developers who automate or manage network configuration and setup. For example, you may have seen Meraki in the small business and organizations you frequent, such as coffee shops or schools, managing the wifi for both customers and staff needs. The audience and their use cases vary and our APIs cover many use cases.

## How active is your review queue?

Because the system is meant for individual teams to review their own content, the centralized team does not have to review each content change. That said, the DevNet team has tech writers help with content updates, and provides a service for on-boarding new teams who want to use PubHub.

## Do you have automation? If so, what type or tooling, and where is the automation in the workflow?

Yes, absolutely as that's one of the drivers for the system, is to enable automation and integration into existing CI/CD workflows to keep in sync with code changes. The PubHub system uses Apache Kafka to manage notifications on updates for each repo and then publish them as static files. The automation for publishing is triggered when the team makes a "release" of the repository, indicating that the content is ready for public consumption.

{% include sign-up.html %}
