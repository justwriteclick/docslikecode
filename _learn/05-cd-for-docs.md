---
title: "Continuous Deployment (CD) for Documentation Sites"
layout: page
image:
  path: /images/learn/netlify-logo400x200.png
  thumbnail: /images/learn/netlify-logo400x200.png
  caption: "[Netlify logo](https://netlify.com)"
---

Continuous deployment lets you build the docs on another system and then place the files where the web server can serve them. CD can include both the building of the HTML files as well as deploying them to a host.

Continuous deployment is game-changing for documentation sites. You can get free or super inexpensive hosting, make sure that all your pull requests build correctly, and make gorgeous web sites, all with automated builds. Until you have used automation for docs it's hard to describe how freeing it can be. You don't have to take the time to build the site locally and then FTP the files to a remote host. You don't have to fiddle with the HTTPS certificates or make sure that the web server itself is configured "just so."

Webhooks are a mechanism for triggering an event based on a change in the repository. You can choose from different services that provide webhooks to build your site automatically. Some examples include:

* [Read the Docs](https://readthedocs.org/)
* [Netlify](https://www.netlify.com/)
* [GitHub Pages](https://pages.github.com)

Let's walk through some examples of CI/CD for websites so you can automate your documentation workflow.

## Build Python Sphinx project to Read the Docs

Once you have a simple set of pages, you can set up continuous deployment on the Read the Docs website, where open source projects can choose to build for free while supporting the site with ethical ads, or by paying a small fee. Follow these steps to get started.

1. Go to https://readthedocs.org/ and sign up for an account.
1. Once you've logged in, go to **Settings** and then choose **Connected Services**.
1. Click the prompts to connect your GitHub account, giving Read the Docs permissions for the repository you want to build docs from, to read the repo and clone the repo.
1. Once you have a connected account, go to your profile on readthedocs.org and click **My Projects** to see a list of your repositories that Read the Docs service can access.
1. To import your new project, click the **+** import icon next to the repository name. Click **Import Manually** if you do not see the repository listed after refreshing your accounts.

### Next: Deploy a Sphinx project to readthedocs.org

When you have a local project you want to deploy to a web site, you can set up the configuration for Continuous Deployment (CD) on readthedocs.org.

You can complete this setup online at readthedocs.org through an account, or you can [manually add the webhook](https://docs.readthedocs.io/en/latest/webhooks.html#webhook-creation) to your repository in GitHub, GitLab, or Bitbucket.

Since this lesson is intended to be prescriptive, let's go through the manual settings in GitHub so that you see how webhooks work.

1. Log into GitHub.
1. Go to the **Settings** page for your project that contains the Sphinx project.
1. Click **Webhooks** and then click **Add webhook**.
1. For the Payload URL, use the URL of the integration on Read the Docs, found in the **Dashboard** > **Admin** > **Integrations** settings. For example, use https://readthedocs.org/api/v2/webhook/rockthedocs-demo/40722/ for a generic webhook. However, while RTD gives you a "token" that is intended for the **Secret** field, the tooling is not yet complete to respect that token. The example URL for the project Integration page is this URL: https://readthedocs.org/dashboard/rockthedocs-demo/integrations/40708/.
1. For Content type, you can use either `application/json` or `application/x-www-form-urlencoded`.
1. Select **Just the push event**.
1. Finish by clicking **Add webhook**.
1. You can verify if the webhook is working at the bottom of the GitHub page under **Recent Deliveries**. If you see a `Response 200`, then the webhook is correctly configured.

>Note: You can configure a Sphinx project to use Markdown as source files. You update your `conf.py` file with this line when you want to use Markdown (`.md`) rather than ReStructured Text (`.rst`) files. Here's an example:
   ```
   # The suffix(es) of source filenames.
   # You can specify multiple suffix as a list of string:
   source_suffix = ['.rst', '.md']
   source_parsers = {
      '.md': 'recommonmark.parser.CommonMarkParser',
   }
   ```

## Deploy a Jekyll Project using GitHub Pages

[GitHub Pages](https://pages.github.com/) is a hosted offering from GitHub itself so you can make web sites by building from GitHub repositories. For your GitHub account, you get one site and with an organization account you get another site, plus you can have unlimited project sites.

Because GitHub Pages supports building sites using a gem-based theme, you can add a line to your `Gemfile` in your repo and then deploy using GitHub Pages from the branch of your choosing in your repository settings.

1. In your local files, edit the `Gemfile` to make sure it contains the line `gem "github-pages", group: :jekyll_plugins` -- replacing the `gem "jekyll"` line:

```
source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins
gem "minimal-mistakes-jekyll"
```
1. Run `bundle install` locally to make sure your local builds are being build with that `Gemfile`.
1. Open your local `_config.yml` file. Remove any existing `theme:` entries and replace with this entry:
```
remote_theme: "mmistakes/minimal-mistakes"
```

By default, you are specifying the `master` branch of the Minimal Mistakes theme with this configuration. You can also "pin" to a specific release by using `"mmistakes/minimal-mistakes@4.9.0"` instead of `"mmistakes/minimal-mistakes"`. I'd recommend using a specific release if you have an active docs site because it helps you with troubleshooting output. Your output remains stable when you pin to a release value and you can test first before a theme upgrade.
1. Create a commit and push these changes to your GitHub repository. Once merged to the branch configured in your repo, the changes show up in a few seconds at username.github.io/project-name.

## Deploy a Hugo Project using Netlify

Once you have a Hugo site working locally, you can set up continuous deployment on Netlify with a free account.

1. [Sign up for free first](https://app.netlify.com/signup).
1. Next, go to https://app.netlify.com/.
1. Click **New site from Git**. One great feature of Netlify is that it can deploy from GitHub, GitLab, or BitBucket, no small feat!
1. Click **GitHub** for this tutorial, but definitely feel free to explore other options later.
1. Grant access by clicking **Authorize Netlify**.
1. Enter your GitHub password to grant access.
1. In the next window, choose the repository that you want to deploy. Of course, you want to choose the one that has Hugo-based documentation source files.
1. In the Netlify window, choose which branch to deploy from (such as `master`), the command to use (Hugo, which by default uses version 0.17), and the directory the deployed files are in (`public` by default).
   > Note: If you want to use Hugo 0.20 or a later specific version, you should later enter it in a `netlify.toml` file in your repository. Or, click **Advanced** and then **New variable** if you want to use the `HUGO_VERSION=0.47` variable in the `[context.deploy-preview.environment]` and `[context.production.environment]` sections.
1. Click **Deploy site**.

## Alternative CI/CD options for deploying and hosting docs sites

You can also deploy documentation sites using free hosting options as alternatives to GitHub Pages.

* [GitLab](https://gitlab.com) also offers GitLab Pages, read more [about how to set it up to learn how](https://about.gitlab.com/2016/04/07/gitlab-pages-setup/).

*  [Netlify](https://www.netlify.com) provides the same capability as GitHub and GitLab with the Ruby gem configuration described in [this tutorial](https://www.netlify.com/blog/2015/10/28/a-step-by-step-guide-jekyll-3.0-on-netlify/) and in the [Minimal Mistakes theme documentation](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#ruby-gem-method).

## What's next

* [Working with content in GitHub repositories](https://docslikecode.com/learn/04-add-content-workflow/)
* [Set Up Automated Tests for Docs](https://www.docslikecode.com/learn/06-test-docs-as-code/)

## Evaluating options

* [Evaluating Static Site Generator themes](https://www.docslikecode.com/learn/07-evaluating-ssg-themes/)
* [Evaluating table layouts and formatting](https://www.docslikecode.com/learn/08-evaluating-table-layouts/)
* [Evaluating Static Site Generator search options](https://www.docslikecode.com/learn/09-ssg-search-implementations/)

## Additional references

* [TravisCI Core Concepts for Beginners](https://docs.travis-ci.com/user/for-beginners)
* [Convert AsciiDoc to HTML/PDF & publish to GitHub Pages with Travis CI and Asciidoctor Docker containers](http://mgreau.com/posts/2016/03/28/asciidoc-to-gh-pages-with-travis-ci-docker-asciidoctor.html)
