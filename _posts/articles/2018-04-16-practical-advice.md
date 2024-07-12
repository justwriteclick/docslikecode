---
layout: post
title: "Practical Advice On Publishing A Technical Book using GitHub and GitBook"
excerpt: What does it take to publish a technical book using GitHub? Let's dig into tools, processes, revenue, and costs.
last_modified_at: Fri Apr 20 21:01:44 CDT 2018
categories: articles
author: anne_gentle
tags: [book, publishing, GitHub, git, gitbook, lulu, self-publishing, collaboration, design, layout]
image:
  path: /images/designbyandren-lightbulb.jpg
  caption: "[Flickr designbyandren](https://flic.kr/p/cMiQAJ)"
comments: false
share: true
---

What does it take to put together a web site, a book, an ebook, all for sale online? Let's look at costs for tools and services that make it happen.

Let’s look at what you need for a book idea. You need an audience, an editor, a way to reach that audience, and a “pitch” for the book idea itself. You may chose self-publishing over pitching the book idea to a technical book publisher.

In my recent experience with *Docs Like Code*, the process led me to choosing to produce the site, epub, and printed book all using tools I had prior experiences with. Let's take a look.

## Reaching out to current contacts

First, I reached out to Andy Oram, a senior editor at O'Reilly who knows me from a couple of open source projects, asking if he thought O'Reilly would want a book proposal. He said he'd be happy to read what I had, but didn't see the initial concept fitting into their current catalog. Really great of him to offer to help out, and I simply thanked him and kept going with my idea.

In parallel, I reached out to the publisher for my first book, *Conversation and Community*. His name is Richard Hamilton and he runs [XML Press](https://xmlpress.com). When he looked at his schedule,
he couldn't read through at the draft copy for about 3 months. Well, I thought that the timing was essential, and I didn't want to wait that long, knowing both the market and my own availability.

## Finding like-minded collaborators

I also reached out to Diane Fleming, now Skwish, who had been teaching writers how to use Git and GitHub for docs over the same time as I had been. Over lunch, we realized we both wanted this book to be available for the next time we teach developers and writers how to write and review docs on GitHub. Diane is a talented writer and also a super editor. The best writers re-write a lot, and I knew Diane would provide an eagle eye for both technical accuracy as well as great writing.

Then, I realized I have a great friend in Kelly Holcomb, who edited my first book and I could talk her into editing this one, wahoo! Kelly also had experience in using GitHub for editing, so her contributions were super important for the final copy.

One area I did skip on for this book was a professional-level index, which Kelly was able to do for a great job on for *Conversation and Community*. I haven’t missed the index yet, and for a smaller book it seems like an index could look like padding.

## Design materials and promotional work

I also was able to do all the design imagery myself, including the book cover. This part was thanks to [Canva](https://www.canva.com/) and some nice templates that service has online. I used the free trial for Canva to make the book cover and stickers and t-shirt design. (Updated to add: the t-shirt store cost $300/year which was not profitable so I stopped offering t-shirts in 2019.)

That said, I was not willing to take on the layout work myself. So, when [Gitbook](https://www.gitbook.com/) did not output a PDF that I considered "print-ready", I went to [Upwork](https://www.upwork.com). I wanted more fine-tuned layout and design for the print copy, including proper page breaks and nice tables. So I hired a designer with access to Indesign who could take the epub and turn it into a print book.

## Pull it together!

And so, with all those bits of input from others, it created a quest to be a product manager for my own information product! I went that route, and for me, [Lulu](https://www.lulu.com/) was a tool I was already familiar with because we had done publishing with it for OpenStack.

There are other publishing options - IngramSpark, Amazon, LeanPub, and I’m sure others. I did sign up and get approved for an account with IngramSpark, which is the print-on-demand service that XML Press uses.

To me, after reading the [origin story for Lulu](https://www.lulu.com/about/our-story), I feel that Lulu is a bit more "open source" based than say, Amazon. I don't know much about LeanPub. Since I was using Markdown on a private GitHub repo anyway, it doesn't seem to offer more than Lulu for the marketplace reach. I'm not trying to make money at it; only trying to increase reach.

Finding a freelance editor would be a huge leg up on the writing process itself, especially if you also need a bit of developmental editing for the book idea.

For the print layout, I had a great experience with UpWork and was also able to hire the same person to work on the second edition. I learned from using a freelance site that I can find and manage freelancers for projects that I want to get done but don’t want to carve out time or buy tools for myself to finish them.

## List of tools and services

| Tools     | Site                                                             |
|-----------|------------------------------------------------------------------|           
| Calibre   | [https://www.calibre-ebook.com/](https://www.calibre-ebook.com/) |
| Canva     | [https://www.canva.com/](https://www.canva.com/)                 |             
| GitBook   | [https://www.gitbook.com/](https://www.gitbook.com/)             |
| GitHub    | [https://www.github.com/](https://www.github.com/)               |
| Lulu      | [https://www.lulu.com/](https://www.lulu.com/)                   |
| Mailchimp | [https://www.mailchimp.com/](https://www.mailchimp.com/)         |
| Printful  | [https://www.printful.com/](https://www.printful.com/)           |
| Shopify   | [https://www.shopify.com/](https://www.shopify.com/)             |
| Upwork    | [https://www.upwork.com/](https://www.upwork.com/)               |

## Ongoing and startup costs

Here’s a high-level overview of the startup costs for creating a book like *Docs Like Code*.
I calculated the starting costs for six or five months, when I needed a monthly subscription for a service.

| Service                    |  Costs              |
|----------------------------|---------------------|                                     
| Domain name registration   |	$20/year           |
| GitHub for Private repo    |  $42 ($7/month x 6) |
| GitBooks for Private repo  |  $35 ($7/month x 5) |
| GitHub Pages for website   |  $0                 |
| Canva for Work (cover art) |  $0 trial           |
| Lulu (printed copies) 		 |  $82 for 15 printed |
| Editing/Writing						 |	$250 celebration   |
| Design for PDF layout 		 |  $250               |
| MailChimp (ongoing) 			 |	$42 ($7/month x 6) |
| Twitter ads 							 |	$25 for ads        |
| Stickers                   |  $82 for 200        |
| **Total startup costs**    |  **$828**           |

Based on Lulu reporting, I see the book brought in about $2500 in 12 months of the first and second edition being available. So while the startup costs are not nothing, I did see a profit from the effort. Really, though, the effort is paid off in helping others see the benefits I've observed and in sharing and learning. Let me know what you think about this method, the tools, and of course, the resulting book, *Docs Like Code*.
