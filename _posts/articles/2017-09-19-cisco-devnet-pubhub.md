---
layout: post
title: DevOps-friendly Docs Publishing for APIs
excerpt: "From Mandy Whaley's presentation at All Day DevOps 2017."
modified: Tue Sep 19 13:36:15 CDT 2017
categories: articles
author: anne_gentle
tags: [documentation, docs, api, rest api, standards, openapi, raml]
image:
  feature: spacewalk-nasa2explore.jpg
  credit: NASA Johnson
  creditlink: https://flic.kr/p/iKTgKf
comments: true
share: true
---

Here at Cisco, we have a developer experience team that focuses on making Cisco APIs easier to use as well as work with developers and Cisco partners in manytechnology areas including IoT, Collaboration, and Software Dened Networking. Mandy Whaley is the Director of Developer Experience and I wanted to share details about docs-like-code solutions here at Cisco. So, I used her presentation and dug into the technology as well. Here's the story.

APIs need great docs. Manyorganizations end up with a jungle of wiki pages, swagger docs and api consoles, and maybe just a fewsecret documents trapped in chat room somewhere... Keeping docs updated and in sync with code canbe a challenge.We’ve been working on a project at Cisco DevNet to help solve this problem for engineering teamsacross Cisco. The goal is to create a forward looking developer and API doc publishing pipeline that:
1. Has a developer friendly editing flow.
1. Accepts many API spec formats (Swagger, RAML, etc). 
1. Supports long form documentation in markdown. 
1. Is CI/CD pipeline friendly so that code and docs stay in sync. 
1. Flexible enough to be used by a wide scope of teams and technologies. 

What did they come up with? Let's look at the source, processing, and output layers.

Source


Processing


Workflows

Output


Results


Integration points

