---
layout: post
title: "Protecting a Branch so Only the Docs Team Merges and Publishes"
excerpt: When you want to allow the docs team members to maintain docs within a code repo, while giving the docs team autonomy over their own reviews and merges, you can use a protected branch and a CODEOWNERS file.
last_modified_at: Sun Oct  1 11:05:31 CDT 2023
categories: articles
author: annegentle
tags: [cicd, reviews, docs, settings, GitHub]
image:
  path: images/guarded-lightbulb-rob-sinclair.jpg
  caption: "[Lightbulb in a protective cage, Attribution: Rob Sinclair.)"
comments: false
share: true
---

# Designate a review team for a directory or collection of files

With GitHub, you have the capability to designate a review team. This setup works well for a scenario where a `docs` directory should be completely controlled by the documentation team. With a [CODEOWNERS](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners) file configuration, the documentation team does not need to ask for other reviewers for small changes like a typo or grammar fix. When a team member's account name or team name is in the `CODEOWNERS` file, you can protect the branch or folder from merges from any account not found in the file. 

A `CODEOWNERS` file can be stored in a directory, or in the `.github` folder, where many configuration files are stored by default. You can protect a branch or multiple branches based on a naming pattern match using [protected branches](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches). 

A straightforward example involves protecting the `docs` folder in the `main` branch, where the `main` branch is the branch used to publish the documentation. In this example, the org name is `justwriteclick` and the username is `annegentle`. You would name the file `CODEOWNERS` and store it in a `docs` directory.

Example `CODEOWNERS` file:
```
@justwriteclick/annegentle
```

You can also use an email address instead of an account name. See an example with lots of use cases in the GitHub documentation [Example of a CODEOWNER file](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners#example-of-a-codeowners-file).

Then, make sure that the branch is protected using the repository's **Setting** > **Branches** > **Branch protection rules** > **Add protection rule** button. Enter `main` for the **Branch name pattern** and then select **Require a pull request before merging**. The settings expand so you can also choose **Require review from Code Owners**. Once you have the settings, click the **Create** button at the bottom of the page. More details are in the [GitHub Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).

<img src="../../images/branch-protection-rule.png" alt="GitHub Branch protection rules settings.">

To see an example of this setup, look at the Microsoft 365 community documentation repository at [https://github.com/MicrosoftDocs/microsoft-365-community/](https://github.com/MicrosoftDocs/microsoft-365-community/). The `CODEOWNERS` file contains a team name, `@microsoftdocs/officedocs-admin`, and those team members can review and merge the list of documents in the `CODEOWNERS` file. The documents contain configuration information as well as the `CODEOWNERS` file itself. 

Example `CODEOWNERS` file from MicrosoftDocs:
```
docfx.json                          @microsoftdocs/officedocs-admin
.openpublishing.build.ps1           @microsoftdocs/officedocs-admin
.openpublishing.publish.config.json @microsoftdocs/officedocs-admin
CODEOWNERS                          @microsoftdocs/officedocs-admin
.acrolinx-config.edn                @microsoftdocs/officedocs-admin
```

Think about ways you can protect your branches with a known group of reviewers. This workflow builds trust and safety while also ensuring you can move fast when needed in a larger team and repository setting. 
