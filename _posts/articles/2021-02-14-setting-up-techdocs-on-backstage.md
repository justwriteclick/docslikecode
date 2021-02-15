---
layout: post
title: Setting up Techdocs on Backstage
excerpt: "Techdocs is Spotify's homegrown docs like code solution. it allows the user to store documentation to near code thus allowing it to be easily discovered."
last_modified_at: Sun Feb  12 14:39:05 CST 2021
categories: articles
author: padraig_o_brien
tags: [backstage, techdocs, roadie, spotify, mkdocs, service catalog]
image:
  path: /images/backstage.jpg
  caption: "[Flickr](https://flic.kr/p/o6Sdy6)"
comments: false
share: true
---
TechDocs is Spotify’s homegrown docs-like-code solution built directly into Backstage. This means engineers write their documentation in Markdown files which live together with their code. In this post we will walk you through how to setup Backstage and Techdocs.

**Table of contents**

- Introduction.
- Basic concepts and structure of backstage and techdocs.
- Install Backstage.
- Setup tech docs.
- Creating and publishing documentation.
- Publish to cloud storage
- Recap

## **Introduction**

Backstage is a platform for building developer portals.

Its main benefit is allowing you to ship high quality code fast.

The main features you get out of the box are

- Service catalog.
- Software templates.
- Plugins which allow you to extend backstage functionality.
- Techdocs, which is the focus of this post.

These features allow you to create standards and best practices across teams.  It increases the speed of development. It creates a  good developer experience for everyone who uses it. You centralise  all your tools and info in one place.

In this post I will take you through the following

- Learn basic concepts and structure of backstage and techdocs
- Install Backstage
- Setup tech docs
- Creating and publishing documentation.
- All on local machine

## **Basics concepts and structures of backstage and techdocs**

The focus of this article is techdocs so i will go through the other main features at a high level.

- Service catalog. It keeps track of ownership and metadata for all the software in your ecosystem. it does this by putting metadata in YAML files stored together with your code. You process these files and then you can visualise the catalog in backstage. This will enable your teams to manage and maintain the software they own. it also makes the software discoverable.
- Software templates - This feature allows you to create templates or skeletons of code. These templates are published to github.
- Plugins - Allow you to integrate third part tools or any kind of infrastructure into backstage. They are open source and you can view a list [here](https://backstage.io/plugins)
- Techdocs- yay, finally, why we are here. Techdocs is Spotify's homegrown docs like code solution. it allows the user to store documentation to near code thus allowing it to be easily discovered.

When you deploy backstage with Techdocs enabled you get a basic out of the box experience.

At its core it is MKDocs plugin and other MkDocs plugins and Python Markdown extensions which allows it to standardize the configuration of MkDocs used for TechDocs.

You can see the code [here](https://github.com/backstage/mkdocs-techdocs-core)

The other moving parts are

- The techdocs container which can be found on Docker-hub, It builds static content through MKDocs
- The Techdocs backend plugin This is the backend part of the techdocs plugin.
- The Techdocs CLI, Command line tool for managing techdocs sites in backstage
- The Techdocs reader, it fetch's remotes pages , run transformers against them and renders them in a shadow DOM
- Transformers API is a function that takes in parameters from the reader component and returns a function which gets passed the dom of the fetched page.

Architecture

![Architecture diagram](https://backstage.io/docs/assets/techdocs/architecture-basic.drawio.svg)

When you open a techdocs sites a request is made the techdocs reader calls the techdocs-backend with the entity id and the path of the current page, the response contains the static content

The static content contains HTML and CSS, javascript is removed for security reasons

Transforms are then applied which modiy the generated static HTML files for a number of reasons like removing certain headers etc

For the following instructions we will use the local file storage but it is better to use cloud storage like S3.

## **Install Backstage**

### Perquisites
Mac running MacOS

Node version 14.x

cookiecutter

If you already have backstage installed then skip this.

```jsx
npx @backstage/create-app
```

You are asked some questions on setup, The recommendation for this tutorial is to go with SQLLite.

![npx install](/images/techdocs/Untitled.png)

If successful you will see this message

![successful](/images/techdocs/01.png)

cd into your directory  and run 

```jsx
yarn workspace backend start
```

![yarn workspace](/images/techdocs/02.png)

Open a new terminal window and 

```jsx
run yarn start
```

![yarn start](/images/techdocs/03.png)

If successful a browser window will open up and you should be presented with a window

![successfull register](/images/techdocs/04.png)

Well done, you have successfully installed backstage on your machine.

## Setup TechDocs

Historically you had to manually add Techdocs , the  latest version of create-app bundles tech docs.

to verify this you should be able to see entries for the following plugin 

```jsx
'@backstage/plugin-techdocs';
  
```

in the following files

```jsx
packages/app/src/plugins.ts
packages/app/src/App.tsx
```

## Creating and publishing techdocs

To create docs manually from scratch click on create component

![manuall](/images/techdocs/05.png)

From here choose the Documentation template

![template](/images/techdocs/06.png)

Fill out Name and Description

![Name Desc](/images/techdocs/07.png)

Type in the owner, the Github repo you want to call it , ensure their is no Github repo that exists with the same name or the Templater will fail

![owner](/images/techdocs/08.png)

Once you click on create you will be presented with a Create component status popup.

![create component](/images/techdocs/09.png)

Once the repository has been published to github the create component status popup will go green like below.

![popup](/images/techdocs/10.png)

You will be able to navigate to the docs.

![navigate](/images/techdocs/11.png)

If it is the first time you are loading them you could receive this message while it converts from MD to html

![loading](/images/techdocs/12.png)

Here is what you will be presented with.

![results](/images/techdocs/13.png)

You now have techdocs up and running on your machine, if you want to view the files manually they are located at the following location on you machine

```jsx
backstage/node_modules/@backstage/plugin-techdocs-backend/static/docs/default/Component/
```

The recommended setup is to place the output on to cloud storage and not on the local machine

## Publish to cloud storage

![cloud](/images/techdocs/14.png)

When you startup backstage you should see this message in the logs to confirm you are using cloud storage

![registered](/images/techdocs/15.png)

You will also see the content in the S3 bucket.

![s3](/images/techdocs/16.png)

## Recap

In summary, we went through an introduction on backs stage, techdocs and how to publish techdocs locally and to cloud storage via s3. if you want to learn more about backstage i would recommend visiting [https://backstage.io](https://backstage.io) or if you want to learn more about techdocs then [https://backstage.io/docs/features/techdocs/techdocs-overview](https://backstage.io/docs/features/techdocs/techdocs-overview)

If you like the idea of backstage but don't want the inconvenience of managing backstage yourself then i would check out   [https://roadie.io](https://roadie.io).