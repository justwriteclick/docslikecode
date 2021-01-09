---
layout: post
title: Survey Results for learning and teaching docs-like-code techniques
excerpt: "Review the results of a mid-2020 survey about learning and teaching team mates and yourself how to work with docs like code, Git, and GitHub for technical documentation."
last_modified_at: Sat Jan  9 13:39:05 CST 2021
categories: articles
author: anne_gentle
tags: [github, git, learning, teaching, documentation, developer, docs-like-code, onboarding]
image:
  path: /images/othree-github-stickers.jpg
  caption: "[Flickr othree](https://flic.kr/p/bGFTuT)"
comments: false
share: true
---

I asked three questions in a survey emailed to my mailing list and got more than 30 responses. Thanks to everyone who took the time to share their stories and respond. Here are the three questions:

* Question 1: When you talk to your leaders about docs-as-code, can they describe the benefits as well as the difficulties?

* Question 2: How do you onboard people who are new to your docs tools and processes?

* Question 3: What tips or discussions (from any source) was most helpful to you when learning docs-as-code techniques?

Docs-as-code processes are still new in the field and it seems many of the responses are split, with no overwhelming patterns in any single area. Let's look into the data and charts for the first two questions.

## Question 1: When you talk to your leaders about docs-as-code, can they describe the benefits as well as the difficulties?

![](/images/survey-charts/leadership-docs-tools.png)

**Legend**

**26.8**% Yes, my leader started our processes and makes it possible for us to use our current tools and processes.

**19.5**% Yes, my leader can provide their leadership complete justification for our choices.

**19.5**% No, I work in an environment where my tool selection does not need justification from a management chain.

**19.5**% No, my leadership chain doesn't really know what I do or why I use certain tools.

**14.6**% It depends on which leader I'm talking to.

In a way, nearly all the responses could be viewed as "leadership either supports the selection does not get in the way of tool selection." For about two-thirds of the responses, either leadership can justify, started the processes, or isn't a deciding factor.

Looking at the number of lone writer responses in the next question, this indicator makes sense as five of thirty-five respondents noted that they were the only writer in the organization, which would make up 14% of all responses. Let's take a look.

## Question 2: How do you onboard people who are new to your docs tools and processes?

![](/images/survey-charts/how-onboard-docs.png)

**Legend**

**14.6**% Internal write-up only

**20.2**% Meeting only

**1.1**% Pre-built environment only

**5.6**% Lone writer

**23.6**% Internal write up and meeting

**34.8**% Internal write-up, meeting, and pre-built environment

My favorite answer to this question was one I hadn't considered, where the person is a lone writer, but works with the devs to get the docs working in the source code repo. It's along the lines of "It's complicated."

> "Nothing, I'm the only person working on docs. The developers required documentation to work with our first attempt because we tried to use tool stacks that crossed different departments between authoring and publishing. Extensive process documentation was required in order for devs to figure out how the docs were to fit together despite the fact that we used markdown and the docs were in the source code repo. We switched tracks when the pain of the "throw it over the wall approach got too big. At which point we started a whole new docs site on a JAM stack platform. But still... Baby-steps."

## Question 3: What tips or discussions (from any source) was most helpful to you when learning docs-as-code techniques?

For question three, I wanted to share any nuggets found in the answers here on the Docs Like Code site, since the goal for this site is to learn these techniques together and share our stories. Here are some highlights.

> "Write the Docs community. Hustling the hard streets of Google search results. Your book!"

> "Trail and Error - lots of searching. Reliance on internal Dev Ops"

> "Familiarity with Git was key - I had already used Git on a smaller scale for personal projects and that helped me become comfortable when I had to  collaborate with other writers/devs. And even then I still had to constantly refer to Git-related resources online to make sure I wasn't messing anything up."

> "Your Docs as Code book was helpful, for certain.  Recently, Frank Miller and Rik Page had two broad discussions about using GIT in lieu of a cCMS (see Git Happens [part 1](https://vimeo.com/431452486) and [part 2](https://vimeo.com/449217243)). The main fear I have is different technical aptitudes and willingness to learn of the writers with whom I work. Some will adapt to GIT easily, while others will struggle mightily."

> "It's still writing. If you don't have documentation as business goal with the processes to produce it - e.g. customer expectation to receive docs with a new release so docs as part of Definition of Done - then docs in code won't help.
Also, engineers won't write unless they're told to. You need a push down from leadership. Don't try to grassroots it."

> "show people that the browser<>Git edit flow is ok, but IDE<>Git<>Browser is far better... show people how much support a good IDE plugin can give (asciidoctor plugin for IntelliJ has so many great features)"

> "We use GitHub already so the argument to switch was easy. When I told the dev teams they didn’t need to use different tools, they were sold. I did, however, make a big mistake early on in the transition. I failed to point out that any non-code related docs (team/training content) should be separate from the code-related docs (readme.md) because not everyone had GitHub work accounts. As a result, non-dev employees couldn’t access anything. That’s not a result of the technique but bad planning on my part. Other than that, it’s been a lean and efficient methodology for how we document our dev projects."

> "Putting the documentation in source code where the developers can get to it. Attempting to docs-as-code with 2 stacks requiring a conversion from markdown to HTML fragments ingested by a little known CMS (MODX) as the published content was a poorly thought out approach. I tried to warn the guys about this - especially since we didn't have a way to duplicate the nested CMS structure required on the publishing end... But we lived with it for a year before it became painfully obvious that another solution was required."


> "I studied your shared extent extensively when I was starting out. Other courses include Peter Gruenbaum's set on Udemy, Tom Johnson's blog, and chats in the Write the Docs Slack channel."

> "Sarah Parson’s Write the Docs presentation on static site generators and Tom Johnson’s explanation of his Documentation Jekyll theme."

This is not a section simply to point to the [Docs Like Code book](https://docslikecode.com/book/) as a resource, rather, it's to show that having additional resources including people you can ask questions is super valuable when learning how to treat docs like code. I'm grateful to the Write the Docs community and people who are also writing their experiences here and on other sites so we can all learn together. Thanks to everyone who shared their experiences and hard-earned wisdom!

{% include sign-up.html %}
