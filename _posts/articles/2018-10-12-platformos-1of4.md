---
layout: post
title: "Building Our Documentation Site on platformOS — Part 1: Information Architecture"
excerpt: This article series describes our process for building the platformOS documentation site, with in-depth insights into our approach, decisions, and plans. In this part, we share how we started, how we got to know our audience, how we figured out what content we need, and how we outlined a sitemap for our documentation site.
last_modified_at: Fri Oct 12 21:01:44 CDT 2018
categories: articles
author: diana_lakatos
tags: [developer documentation, Design Thinking, Information Architecture, docs, documentation, UX]
image:
  path: /images/platformos/platformos_part1/part1_cover.jpg
  caption: "[Courtesy platformOS blog](https://www.platform-os.com/blog/post/building-our-documentation-site-on-platform-os-part-1-information-architecture)"
comments: false
share: true
---

This article series describes our process of building our [documentation site](https://documentation.platform-os.com/) for [platformOS](https://www.platform-os.com/), with in-depth insights into our approach, decisions, and plans. We have planned four parts for this series, each describing a unique aspect of our journey:  

* Part 1: **Information Architecture**  
  In this part, we share how we started, how we got to know our audience, how we figured out what content we need, and how we outlined a sitemap for our documentation site.
* Part 2: **Layouts and Content Production**  
  In this part, we discuss how we started building templates and wireframes, how we approached the design, and how we started producing content.  
* Part 3: **Community**  
  We build our site for our community. Learn more about community-driven documentation, and the mechanisms we built in to support our users and continuously improve our docs, like feedback options, contribution through GitHub, pre-made templates for each content type, and a style guide to make it easier to keep everything consistent.  
* Part 4: **Implementation**  
  In this part, we take a look under the hood, and discuss the technologies we used, how we built our auto-generated API Reference, and how we pull content and related information from Github. We also share our future plans with you.  

All these articles together will show you a complete framework for building a documentation site on platformOS.

We are continuously working on our documentation, but decided to make it public early on to get valuable feedback and show you the whole process, so please expect the documentation site to change and evolve while you learn more about it through these articles. At the time of the publication of this article, our documentation site is in alpha.  

# Building Information Architecture through Design Thinking

Because of the strategic role our documentation plays in the adoption and use of our product, we approached the development of our docs with a mindset that ensures that:  

* Our community gets the most out of our documentation as early on as possible.
* We receive feedback as soon as possible.
* We never lose sight of our long-term goals.  

All throughout the process, we used the user-centered, solution-based [Design Thinking](https://en.wikipedia.org/wiki/Design_thinking) method.  

![](/images/platformos/platformos_part1/design_thinking.png)

At the start, we explored our audience, our documentation needs, existing and missing content through in-depth interviews and workshops. In Design Thinking terms, this was the **Empathize** phase. Then, we defined personas and our Content Inventory (**Define**), and shared our ideas for content and features through a Card Sorting exercise (**Ideate**). Based on our findings, we created a sitemap and prioritized content needs. Layouts, wireframes, and content production (**Prototype**) started based on the results of our discovery phase.

We decided to follow an iterative, docs like code approach: at each stage, we work with quick feedback rounds, deploy often (multiple times a week), and improve features and content based on feedback from real users (**Test**). We have an overarching plan outlined for our documentation that we keep in mind, but we always focus on the next couple of action steps we’d like to take.  

## Discovery 

We knew that knowing our audience is the key to writing documentation that best supports their needs. For efficiency, we also needed to know what we already have, and how existing content could be reused. This is why we started our journey with a discovery phase. By asking the right questions, we got the answers we could build on, and outlined the Information Architecture and content needs of our documentation site.  

### Proto-personas

The first output from our workshops was a detailed description of each persona — the types of users that will be interacting with our documentation site. The user personas help team members share a specific, consistent understanding of various audience groups. We use these personas to see how well proposed solutions meet their needs, and to prioritize features based on how well they address the needs of one or more personas. We plan to revisit and revalidate these personas in later phases of the project as the product is evolving.  

We found out that we have the following four main personas:  

* Experienced Developers
* Junior Developers
* Site Builders
* Marketplace Owners

![](/images/platformos/platformos_part1/protopersonas.jpg)

_Descriptions of our proto-personas with sample photos and names to make them easier to relate and refer to_

### Content Inventory

Taking into account our proto-personas’ needs and sites we considered our inspiration, we created a detailed list of content from our previous documentation site, and identified missing, reusable, and non-reusable content for our future site.   

![](/images/platformos/platformos_part1/content_inventory.png)

_Content Inventory ready for the Card Sorting Session_

### Card Sorting Sessions

Through a [Card Sorting](https://www.usability.gov/how-to-and-tools/methods/card-sorting.html) exercise, we defined connected elements, and mapped out the best site structure for our goals and proto-personas.

![](/images/platformos/platformos_part1/cardsorting.png)

![](/images/platformos/platformos_part1/cardsorting2.png)

_Screens from [Mural](https://mural.co/) during our Card Sorting sessions_  

### Sitemap

Based on the Content Inventory and the results of the Card Sorting sessions, we outlined a sitemap for our future site. Our sitemap shows the structure of the site. We can also use it as a roadmap to keep track of site improvements, content needs, and project phases, because following our iterative approach, we created several sitemaps — one for each phase of the process (e.g. alpha, beta, etc.).

![](/images/platformos/platformos_part1/sitemap.png)

_Sample page from our sitemap_  

We have already changed some parts of our sitemap based on new information we gathered and business decisions we made. For example, we are now planning to build a separate community site, instead of having a community section on our documentation site. We decided to link to content on [platform-os.com](https://www.platform-os.com/blog/post/platform-os-blog-module) (like the blog, terms & conditions, etc.) in the beginning to focus on other parts of the site, and reevaluate these sections later. We believe that both product and content development can benefit from a process that allows for such flexibility.  

### Persona-based content prioritization

Now that we had data about the personas and our sitemap, we put the data into the proper context and outlined coherent stories. These stories, similar to user journeys, show the order of actions taken by the user personas during their interaction with the site. During the Card Sorting sessions, we explored areas of interest for each user persona. This helped us see where to focus first to help them from the beginning. We also validated the importance of these areas to assign higher priorities to the ones that need more attention. We then displayed their interaction with the site on the sitemap.

![](/images/platformos/platformos_part1/userjourneys1.png)

_Exploring areas of interest based on the persona’s actions taken on the site_  

![](/images/platformos/platformos_part1/sitemap_userjourneys.png)

_Persona interactions with the site displayed on the sitemap_  

This concluded our Information Architecture phase. We have discovered and organized all the information we needed to continue on to the next phase, where we started creating templates for content types, building the wireframes for each page, producing content, and making decisions about design.

**We will discuss these aspects in part 2 of our series. Stay tuned!**

_We involved [UX Strategist Katalin Nagygyörgy](https://www.linkedin.com/in/nagygyorgykatalin/) in our process from the start. Through our collaboration, we could extract and collect all the necessary information using tried and true research methodologies and UX best practices._

_This article was originally written for the [platformOS Blog](https://www.platform-os.com/blog/post/building-our-documentation-site-on-platformos-part-1-information-architecture)._

{% include sign-up.html %}
