---
layout: post
title: Case Study - Pantheon, Rachel Whitton
excerpt: "In this use case, the Technical Content Editor at Pantheon, Rachel Whitton, describes their use of GitHub for documentation."
modified: Sat Mar 18 09:50:27 CDT 2017
categories: articles
author: rachel_whitton
tags: [case study, use case, github, docs, repos, web, content, workflows]
image:
  feature: stevensnodgrass-bolt.jpg
  credit: Flickr stevensnodgrass
  creditlink: https://flic.kr/p/8jKjE2
comments: true
share: true
---

Pantheon is a website management platform for Drupal and WordPress. In this use case, their Technical Content Editor Rachel Whitton describes the use of GitHub for documentation as well as their workflow.

#### What site or sites do you create from GitHub source? 

[pantheon.io/docs](https://pantheon.io/docs)

#### What are the repositories that build the deliverables? 
[github.com/pantheon-systems/documentation](https://github.com/pantheon-systems/documentation)

#### Can you give an idea of the size, such as how many pages (source and output)? If they're private, that's fine too, talk about what led to that decision.
Source files: 588 These are all publicly-editable source files.
Output files: 602

#### When did your migration to GitHub occur?
We began the process in November of 2014 by creating a private repository for the content migration and initial development of a new static site (built with [Sculpin](https://sculpin.io)). The site went live in January 2015 and the repository went from private to public in April 2015.

#### What factors led your team to choose GitHub for docs? 

We chose to host our documentation repository on GitHub to align ourselves with tools and workflows adopted by other teams across our organization for better collaboration. Our secondary goal was to tap into the collective intellect of our developer community by allowing public contributions. Over time, we began documenting upcoming features in the open prior to their full release which resulted in new levels of participation in the project on GitHub (feedback on product functionality and design, bug reports, etc). 

#### What type of audience are you writing for? Do your readers write with you? If so, how?

Pantheon’s audience for documentation consists primarily of developers and technical  advocates for digital agencies. Public contributions are most often initiated from a call to action on the site. Visitors start by clicking the Contribute button, then either edit the current page, report an issue, or suggest new content. Depending on the selection, a new tab for GitHub will open to either edit the page or open an issue using a pre-filled template. [We encourage all contributors to create a profile](https://github.com/pantheon-systems/documentation/blob/master/CONTRIBUTING.md#contributors) and attribute their work alongside any pull requests. 

#### How active is your review queue? How often do you publish?

The documentation project receives an average of almost 40 commits per week. The site is continuously delivered upon each commit to the default branch.

#### Do you merge or rebase? Have you kept the same workflow always? How long has the workflow been in place? 

It depends. Generally, our workflow is to merge into the default branch once updates have been peer reviewed on a “feature” branch. We use rebase as needed or as an alternative to merging when including work in progress from one feature branch on another during their simultaneous development to ensure changes are aligned and accounted for. Our workflow is constantly evolving to better serve the project.

#### What's your biggest win from using GitHub for docs? Tell a story. 

We try our best to prevent gaps in documentation, but one area that’s really challenging for us is covering external integrations. I didn’t know it at the time, but making the move to GitHub set us up to receive high value contributions from other organizations. Chris Tietzel, CEO and Founder of Lockr, submitted an article (https://pantheon.io/docs/guides/lockr/) to the docs via GitHub after receiving support requests from users for help installing and integrating Lockr on Pantheon-hosted websites. 

#### What would you warn others about when thinking about GitHub for docs? 

Think about the contributor and moderator experiences - don’t be afraid to adjust workflows as your project matures. Be aware that moderators won’t have write access to forks unless granted by the maintainer of the fork - this means you’ll need to have a plan for copy edits on Pull Requests from a fork that are initiated from non-org members. We handle these by using GitHub’s suggested workflow for merging locally on the command line: checkout a new branch, pull commits from the fork, make copy edits, stage and commit, switch to the default branch, then merge and push to GitHub. The Pull Request will update to reflect its merged status within the default branch. 

#### Would you suggest migrating content or only building new? 

It depends. We migrated a lot of content because it didn’t make sense to start over. I’d say migrate what you can but don’t be afraid to start fresh depending on the needs and goals of your project. If you do migrate, automate the process as much as possible. Your sanity will thank you. 

#### Do you have automation? If so, what type or tooling, and where is the automation in the workflow? 

Pantheon uses CircleCI for continuous integration which builds all commits pushed to GitHub then tests and deploys changes to either a staging environment or to production. Deployments to production occur via rsync after tests have run successfully. If any test fails (broken link, performance regression, etc.) The build will fail on CircleCI and the deployment to production is skipped until a passing build occurs. Branches other than our default branch get deployed to isolated cloud development environments for staging with unique and publicly accessible URLs. Deployments to staging environments happen before the test suite is run to help debug issues and/or failures. Once builds have been deployed to a staging environment, a comment is created on the commit in GitHub with a link to the changes for quick and easy peer review. Once a feature branch has been merged into the default, the associated staging environment is automatically deleted along with the branch. The automation procedures are scripted in Bash and configured in the `circle.yml` file within the project’s root directory. The staging environments are created using Pantheon’s command line tool, [Terminus](https://pantheon.io/docs/terminus/), and our [Multidev](https://pantheon.io/features/multidev-cloud-environments) feature. 

This workflow is not available to forks for security reasons. For details, see CircleCI’s documentation: [Security Implications of Running Builds for Pull Requests from Forks](https://circleci.com/docs/fork-pr-builds/#security-implications-of-running-builds-for-pull-requests-from-forks).

#### Are there any questions you wish you had asked before using GitHub for docs? 

How do the needs of open source software projects differ from those of a documentation project? Where does GitHub fail to fulfill the needs of documentation projects and how can those gaps be filled?

{% include sign-up.html %}