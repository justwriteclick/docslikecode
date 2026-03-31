---
title: "Docs-as-Code Quick Start Guide"
layout: learn
image:
  path: /images/learn/mikecogh-trains.jpg
  thumbnail: /images/learn/github-logo400x200.png
  caption: "Photo from [Flickr:mikecogh](https://flic.kr/p/pEn3RB)"
---

# Docs-as-Code Quick Start Guide

**Build Your First Modern Documentation Workflow Using GitHub, Markdown, and Automation**

---

## Introduction: Why Documentation Feels Broken

If you’ve worked in documentation, you’ve probably experienced this:

* Content lives in Word docs, wikis, or scattered tools
* Developers don’t contribute—or avoid docs entirely
* Publishing updates is slow and manual
* Documentation quickly becomes outdated

The result? Frustration, inconsistency, and a constant feeling of playing catch-up.

There’s a better way.

---

## What Is Docs as Code?

**Docs as Code** is an approach where you create and manage documentation using the same tools and workflows as software development.

Instead of separate systems, you use:

* Version control (Git)
* Plain text files (Markdown)
* Collaborative workflows (pull requests)
* Automated publishing (CI/CD)

This brings documentation into the same ecosystem as your engineering team—making it faster, more collaborative, and more scalable.

---

## What You Can Build with This Guide

In the next 20–30 minutes, you’ll:

* Create a documentation repository
* Write content in Markdown
* Make and review changes using pull requests
* Understand how publishing can be automated

No advanced setup required—just a basic familiarity with Git concepts.

---

## Step 1: Create a Repository

Start by creating a new repository for your documentation, meaning a folder locally and a repository on a site like GitHub.

Suggested name:

```
docs-example
```

This repository holds all your documentation files.

### Why this matters

Storing documentation in a repository gives you:

* Version history
* Collaboration via pull requests
* A single source of truth

---

## Step 2: Add Your First Markdown File

Create a file called:

```
index.md
```

Add the following content:

```markdown
# Welcome to Our Documentation

This is our first docs-as-code project.

## Getting Started

This documentation is written in Markdown and managed in Git.
```

### Why Markdown?

Markdown is:

* Simple and readable
* Easy to edit
* Widely supported by documentation tools

It removes formatting friction so you can focus on content.

---

## Step 3: Make a Change Using a Pull Request

Instead of editing directly on the main branch, create a new branch:

```
update-intro
```

Edit your file:

```markdown
This documentation is written in Markdown and managed in Git.

We use a docs-as-code workflow to collaborate and publish content.
```

Now open a pull request.

### What’s happening here?

You’ve just:

* Proposed a change
* Made it visible for review
* Enabled collaboration

This is the core of docs-as-code.

---

## Step 4: Review and Collaborate

In a real team, someone would:

* Review your changes
* Leave comments
* Suggest improvements

This creates:

* Higher-quality documentation
* Shared ownership
* Better alignment with engineering

---

## Step 5: Merge and Publish

Once approved, merge the pull request.

At this point, your documentation is:

* Updated
* Versioned
* Ready to publish

---

## Step 6: (Optional) Add a Static Site Generator

To turn your Markdown into a website, you can use a static site generator like:

* Jekyll
* Hugo
* Sphinx

These tools:

* Convert Markdown into HTML
* Apply themes and navigation
* Create a professional documentation site

---

## Step 7: Automate Publishing

The final step is automation.

Using CI/CD, you can:

* Automatically build your site
* Deploy it when changes are merged
* Keep documentation always up to date

Now your workflow looks like this:

**Write → Review → Merge → Publish (automatically)**

---

## What You Just Achieved

In a short time, you’ve:

* Created a version-controlled documentation system
* Collaborated using pull requests
* Prepared content for automated publishing

This is the foundation of docs as code.

---

## Why This Changes Everything

Compared to traditional documentation, this approach:

* Reduces bottlenecks
* Improves collaboration with developers
* Enables faster updates
* Scales across teams and products

Instead of being an afterthought, documentation becomes part of the development process.

---

## What’s Next

This quick start only scratches the surface.

In the full book, you’ll learn how to:

* Design scalable documentation architectures
* Choose the right tools and platforms
* Implement CI/CD pipelines for docs
* Manage large documentation sets across teams
* Build a sustainable docs-as-code culture

---

## Ready to Go Further?

If you found this useful, the full [book](https://docslikecode.com/book/) will take you from a simple workflow to a complete, production-ready documentation system.

👉 Continue your journey with *Docs Like Code*

---
