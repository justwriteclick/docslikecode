---
layout: post
title: Animated GIFs Pause and Play - Balsamiq, Leon Barnard
excerpt: "Learn how to play and pause animated GIFs on static sites such as Hugo on GitHub from Leon Barnard, Designer and Writer at Balsamiq."
last_modified_at: Sat May 13 18:37:48 CDT 2017
categories: articles
author: leon_barnard
tags: [case study, balsamiq, static sites, use case, wireframes, github, docs, repos, hugo, tools, gif, animated gifs]
image:
  path: /images/rogerjones-wireframe.jpg
  caption: "[Flickr rogerjones](https://flic.kr/p/i4ZAW)"
comments: true
share: true
---

# Use Case Part II: Balsamiq

After learning about [documenting multiple product versions with a static site generator](https://docslikecode.com/articles/balsamiq-case-study-part-1/), this week we hear how Leon Barnard, Writer, Designer, and aspiring Developer at Balsamiq, figured out how to use animated GIF files in user assistance while also not annoying people with an endless looping animation. Not annoying and also not streaming video? Plus the cleanest Markdown source files you could create? Do tell.

## Background

[Balsamiq set up a new documentation site](https://blog.balsamiq.com/new-documentation-site/) about a year and a half ago. We converted our old, flaky documentation system over to a "docs like code" system using [Hugo](https://gohugo.io/), [Gulp](https://gulpjs.com/), and [GitHub](https://github.com/), with content written in Markdown. The conversion took a while, so in the end we were pleased simply to get working.

Once it was part of our daily workflow, and we could begin to look to the future, we started envisioning the next version. In doing so, we recognized the limitations and looked for solutions that kept writers writing and readers reading. This series tells the tale of three of these problem areas and how we solved the challenges.

## Challenge #2: Adding play/pause to animated GIFs

In a very different challenge from [our first one](https://docslikecode.com/articles/balsamiq-case-study-part-1/), we noticed that our support team was getting great feedback when they would send animated GIFs to customers to explain solutions to problems they were having. The classic case of "show, don't tell." We realized that adding them to our documentation could be helpful too, and we added a few of them in the first version of our docs.

But it can be distracting to read an article when there's an endlessly-looping animation in your line of sight. But if you only play it once, readers could miss it.

I came across several sites that gave users an option to play the animated GIF when they clicked on it and I thought that would be great for our docs.

I found a great jquery plugin that I wanted to use called [**gifplayer**](https://rubentd.com/gifplayer/).

[![You know you want to click](https://media.balsamiq.com/images/docslikecode/gifplayer.png)](https://rubentd.com/gifplayer/).

There was just one problem. Markdown. Again.

Triggering the gifplayer code is as easy as adding a CSS class to an image. Like this:

```html
<img class="gif" src="https://rubentd.com/img/banana.png">
```

But native Markdown doesn't support adding CSS. Of course, Markdown *does* support inline HTML, and we *could* have just written HTML whenever we wanted to add an animated GIF. But, again, **I'm stubborn**. I like my Markdown to be clean. I didn't want to go down a slippery slope of adding special cases for departing from pure Markdown.

Now, there are two parameters that you give an image in Markdown: the file name, which I needed to tell it where the file is, and alt text, which we often leave blank (I know... accessibility). So I decided to customize the jquery function that initialized gifplayer. Instead of looking for images with a CSS class called 'gif', it would look for images with  alt text set to 'gif'.

Like this:

```javascript
<script>
  $(document).ready(function(){
    $("img[alt='gif']").gifplayer({ label: 'Play' });
	});
</script>
```

So, now, if we write:

```markdown
![gif](https://rubentd.com/img/banana.png)
```
it triggers the gifplayer script!

![party](https://rubentd.com/img/banana.gif)

Sorry, we didn't implement the pause/play capability on this site, so that banana is gonna keep on dancing. You can see the pause/play solution in action on our Balsamiq article on [common workarounds](https://support.balsamiq.com/tutorials/workarounds/#link-to-alternates).

{% include sign-up.html %}
