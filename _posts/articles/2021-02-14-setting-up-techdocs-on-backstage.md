---
layout: post
title: Setting up Techdocs on Backstage
excerpt: "Techdocs is Spotify's homegrown docs like code solution. it allows the user to store documentation to near code thus allowing it to be easily discovered."
last_modified_at: Sun Feb  12 14:39:05 CST 2021
categories: articles
author: padraig_o_brien
tags: [backstage, TechDocs, roadie, spotify, mkdocs, service catalog]
image:
  path: /images/backstage.jpg
  caption: "[Flickr](https://flic.kr/p/o6Sdy6)"
comments: false
share: true
---
TechDocs is Spotify’s homegrown docs-like-code solution built directly into Backstage. [Backstage](https://github.com/backstage/backstage) gives teams one front-end view for all their infrastructure tools, like Google Cloud Platform, Cloud Bigtable, CI pipelines, TensorFlow Extended, and others, all in a consistent, easy-to-use interface, or portal. It's open source software released by Spotify. 

With TechDocs built into Backstage, all the engineers write their documentation in Markdown files which live together with their code. In this post we will walk you through how to setup Backstage and Techdocs.

**Table of contents**

- Introduction
- Basic concepts and structure of Backstage and TechDocs
- Install Backstage
- Setup TechDocs
- Create and publish documentation 
- Publish to cloud storage (example)
- Recap and summary

## Introduction

Backstage is a platform for building developer portals, giving one view into developer tools.

Its main benefit is allowing you to ship high quality code fast thanks to consistent views of your tools and infrastructure.

The main features you get out of the box are:

- Service catalog
- Software templates
- Plugins which allow you to extend Backstage functionality
- TechDocs, which is the focus of this post

These features allow you to create standards and best practices across teams. It increases the speed of development. It creates a good developer experience for everyone who uses it. You centralise all your tools and information in one place.

In this post I will take you through the basic concepts and structure of Backstage and TechDocs, an installation of Backstage including the setup of TechDocs, creating and publishing documentation, all on a local machine on MacOS. 

## Basics concepts and structures of backstage and TechDocs

The focus of this article is TechDocs, so I will go through the other main features at a high level.

- Service catalog - It keeps track of ownership and metadata for all the software in your ecosystem. Backstage does this by putting metadata in YAML files stored together with your code. You process these files and then you can visualise the catalog in Backstage. This catalog enables your teams to manage and maintain the software they own, making the software discoverable.
- Software templates - This feature allows you to create templates or skeletons of code. These templates are published to GitHub.
- Plugins - Allow you to integrate third party tools or any kind of infrastructure into Backstage. They are open source and you can view a list [here](https://backstage.io/plugins).
- Techdocs - Yay, finally, why we are here. Techdocs is Spotify's homegrown docs like code solution. It allows the user to store documentation near the relevant code, thus allowing the docs to be easily discovered and maintained.

When you deploy Backstage with Techdocs enabled you get a basic out of the box experience.

At its core, TechDocs is an MKDocs plugin with other MkDocs plugins and Python Markdown extensions which allows it to standardize the configuration of MkDocs used for TechDocs.

You can see the source code for TechDocs [here](https://github.com/backstage/mkdocs-TechDocs-core).

The other moving parts are:

- The TechDocs container which can be found on Docker-hub, which builds static content through MKDocs.
- The Techdocs backend plugin which is the backend part of the TechDocs plugin.
- The Techdocs CLI, a handy command line tool for managing TechDocs sites in Backstage.
- The Techdocs reader, it fetches remotes pages, runs "transforms" against them, and renders them in a shadow DOM.
- The Transforms API takes in parameters from the reader component and returns a function which gets passed the DOM of the fetched page.

**Architecture**

![Architecture diagram](https://backstage.io/docs/assets/TechDocs/architecture-basic.drawio.svg)

When you open a TechDocs site, a request is made. The TechDocs reader calls the TechDocs-backend with the entity id and the path of the current page. The response contains the static content. The static content contains HTML and CSS, and any JavaScript is removed for security reasons.

Transforms are then applied which modify the generated static HTML files for a number of reasons like removing certain headers and so on.

For the following instructions, since we are using a local install for demonstration and trial, we will use the local file storage, but in production you would use cloud storage like S3.

## Install Backstage

### Prequisites

* Mac running MacOS

* Node Version Manager (nvm) so that you can ensure you're using Node version 14. Run: `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash` or `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | zsh` on MacOS Catalina and newer.

* Node version 14.x (Cannot use Node version 15.x) (You can use `brew install node` to install on MacOS if needed.) Run `nvm use --lts` so that you can run Node version 14.15.5 for this demo.

* Yarn (Use `brew install yarn` for this demo.)

If you already have Backstage installed, then you skip this "create-app" step. First, create the initial app in any directory you choose:

```jsx
npx @backstage/create-app
```

This will take a few minutes. 

You are asked some questions on setup. The recommendation for this local tutorial is to go with SQLLite by using the down arrow when prompted.

![npx install](/images/techdocs/create-app.png)

If successful you will see this message:

![successful](/images/techdocs/01.png)

Change into your created app's directory, the name you used for the app, in this example it's `infraportal`:

```
cd infraportal
```

Then run:

```jsx
yarn workspace backend start
```

![yarn workspace](/images/techdocs/02.png)

Open a new terminal window and change directories to the `infraportal` where you created the app. 
```
cd ~/src/backstage/infraportal
```

Then start the app with this command:

```jsx
yarn run start
```

![yarn start](/images/techdocs/03.png)

If successful, a browser window opens and you should be presented with a window.

![successfull register](/images/techdocs/04.png)

Well done, you have successfully installed Backstage on your local machine.

## Setup TechDocs

Historically you had to manually add Techdocs, but now the latest version of create-app bundles TechDocs.

To verify this setup, you should be able to see entries for the plugin `'@backstage/plugin-TechDocs';` in the following files:

```jsx
packages/app/src/plugins.ts
packages/app/src/App.tsx
```

## Creating and publishing TechDocs

To create docs manually from scratch, click on create component:

![manuall](/images/techdocs/05.png)

From here choose the Documentation template.

![template](/images/techdocs/06.png)

Fill out a Name and Description.

![Name Desc](/images/techdocs/07.png)

Have a GitHub org or owner and a GitHub repo ready to use for your docs. Type in the GitHub owner and the GitHub repo you want to use. Make sure there is no GitHub repo that exists with the same name or the Templater will fail.

![owner](/images/techdocs/08.png)

Once you click on create you will be presented with a Create component status popup.

![create component](/images/techdocs/09.png)

Once the repository has been published to GitHub, the create component status popup will show green like below.

![popup](/images/techdocs/10.png)

You will be able to navigate to the docs.

![navigate](/images/techdocs/11.png)

If it is the first time you are loading them you could receive this message while it converts from MD to html.

![loading](/images/techdocs/12.png)

Here is a screenshot of what you will be presented with.

![results](/images/techdocs/13.png)

You now have TechDocs up and running on your machine. Well done. If you want to view the files manually they are located at the following location on your machine:

```jsx
backstage/node_modules/@backstage/plugin-TechDocs-backend/static/docs/default/Component/
```

The recommended setup is to place the output on to cloud storage such as S3, and not on the local machine, so let's look at that next.

## Publish to cloud storage

![cloud](/images/techdocs/14.png)

When you startup Backstage you should see this message in the logs to confirm you are using cloud storage:

![registered](/images/techdocs/15.png)

You will also see the content in the S3 bucket.

![s3](/images/techdocs/16.png)

## Recap and summary

In summary, we went through an introduction on Backstage, TechDocs, and how to publish TechDocs locally and to cloud storage via S3. If you want to learn more about Backstage I would recommend visiting [https://backstage.io](https://backstage.io) or if you want to learn more about TechDocs then [https://backstage.io/docs/features/TechDocs/TechDocs-overview](https://backstage.io/docs/features/TechDocs/TechDocs-overview) offers a great overview. 

You can also read about the gains the team at Spotify has seen since using TechDocs for all their documentation in [Ten tips for maintaining a long-term relationship with docs like code](https://www.docslikecode.com/articles/ten-tips-maintaining-long-term-docs-like-code/).

If you like the idea of Backstage but don't want the inconvenience of managing Backstage yourself, then check out [https://roadie.io](https://roadie.io). Thanks for taking a look at this tutorial and happy documenting!