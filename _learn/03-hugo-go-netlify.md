---
title: "Set Up Hugo with Go"
layout: learn
image:
  path: /images/learn/hugo-docs-page.png
  thumbnail: /images/learn/go-logo400x200.png
  caption: "Screenshot using Gravatar theme"
---

To build Hugo sites locally, install Homebrew and Hugo. You do not need to install Go to use Hugo as your static site generator. These instructions are for a Mac or Linux system, but you can also read the Windows installation instructions on the [gohugo.io](https://gohugo.io/getting-started/installing#windows) site.

Since Hugo is built on Go, you can use the binary for your operating system. No need to maintain a development environment. Upgrades are easy too, get a new binary and install it and you're upgraded.

## Prerequisites
* Windows, MacOS, or a Linux-based environment.
* On MacOS, you will install [Homebrew](https://brew.sh).
* On Windows, you must install Docker.
* On Windows, you must install [Git for Windows](https://gitforwindows.org/) which includes Git Bash.

## Set up Hugo on Windows with Git Bash and Docker

You can also set up Docker and then use this [Docker image](https://hub.docker.com/r/jguyomard/hugo-builder/) to install Hugo. With the Docker image, you set up alias commands for `hugo` running in Docker, but can work in Git Bash and follow this tutorial using the same `hugo` commands in Git Bash on Windows.

## Set up Hugo on MacOS
1. Install Homebrew. See the [Homebrew site](https://brew.sh) for instructions.
1. Use Homebrew to install Hugo.

   ```
   $ brew install hugo
   ```

1. Verify the `hugo` installation by checking the version value.

   ```
   $ hugo version
   hugo v0.135.0+extended darwin/amd64 BuildDate=2024-09-27T13:17:08Z VendorInfo=brew
   ```

## Starting a Hugo site

For a Hugo static site, you can choose your specific theme after you create the source files. The theme we'll use in this tutorial is [hugo-theme-relearn](https://themes.gohugo.io/themes/hugo-theme-relearn/). To start a new site in the current folder, run:

   ```
   $ hugo new site docs-as-code
   $ cd docs-as-code
   ```

1. Take a look at the files created in the directory with an `ls` command:
  ```
  $ ls -A
  archetypes	content		hugo.toml	layouts		themes
  assets		data		i18n		static
  ```
  
1. Initialize the current directory as a Git repository, which will enable you to bring the theme in as a Git submodule. 
   ```
   $ git init
   Initialized empty Git repository in /Users/agentle/src/hugo-example/.git/
   ```

1. Edit `hugo.toml` in any text editor you like to get started. Choose a title for your site and the theme, in our case, `hugo-theme-relearn`. (Find the [installation documentation for the Relearn Theme here](https://mcshelby.github.io/hugo-theme-relearn/basics/installation/index.html).) The theme name in your configuration file must match the name of the specific theme directory inside the `/themes` directory, so we will add those files in the next step.
  ```
  baseURL = "http://example.org/"
  languageCode = "en-us"
  title = "Learning Hugo Site"
  [module]
  [[module.imports]]
    path = 'github.com/McShelby/hugo-theme-relearn'
  ```
1. To get the theme files in the `/themes` directory, and keep them updated, use a `git submodules` command to get the required theme files as well as keep them updated.
  ```
  $ hugo mod init example.com
  ```
  The terminal returns something like this:
  ```
  go: creating new go.mod: module example.com
  go: to add module requirements and sums:
	go mod tidy
  ```
  Next, add the theme as a Git submodule with this command:
  ```
  git submodule add --depth 1 https://github.com/McShelby/hugo-theme-relearn.git themes/hugo-theme-relearn
  ```
1. For Hugo, the `content` folder contains the site source content. For your home page, make an `_index.md` document in the `content` folder and write it with Markdown content. Switch back up one level since you just cloned the theme files.
  ```
  $ cd ..
  $ hugo new --kind home _index.md
  Content "/Users/agentle/src/hugo-example/hugo-example/content/_index.md" created
  ```
1. Next, add a new chapter page using the `hugo` command, `hugo new`:
  ```
  $ hugo new --kind chapter get-started/_index.md
  /Users/agentle/src/hugo-example/content/get-started/_index.md created
  ```
1. You can keep adding files with the `hugo new` command so that the Markdown files are pre-populated with the front matter such as:
  ```
  +++
  archetype = "chapter"
  title = "Get Started"
  weight = 1
  +++
  ```

## Build a Hugo site locally

Once you've prepared your local system, you can build locally and review the site in your browser.

For Hugo, it's important to know that draft pages, where `draft = true` is in the front matter, won't be served.

1. Run the `hugo server` (or `hugo serve`) command to run a local server with your draft website.

   ```
   $ hugo server

                         | EN
      +------------------+----+
        Pages            | 12
        Paginator pages  |  0
        Non-page files   |  0
        Static files     | 67
        Processed images |  0
        Aliases          |  0
        Sitemaps         |  1
        Cleaned          |  0

      Total in 48 ms
      Watching for changes in /Users/agentle/src/hugo-example/doc-machine/{content,data,layouts,static,themes}
      Watching for config changes in /Users/agentle/src/hugo-example/doc-machine/config.toml
      Serving pages from memory
      Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
      Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
      Press Ctrl+C to stop
   ```
2. Open the **Web Server** URL, `http://localhost:1313/` in your local browser to view the site. (By default, the theme may be purple instead of green.)
    ![Example Hugo site](/images/learn/hugo-docs-page.png)
3. Press `Ctrl+C` in the server terminal to stop the Hugo server.
4. You can add your files to a Git commit. Refer to [Working with content in GitHub repositories](https://docslikecode.com/learn/04-add-content-workflow/) for a documentation workflow with your Hugo site.

## Modify the Hugo theme

By default, the Hugo Theme "Learn" has a purple sidebar. How about changing the color and logo displayed in the sidebar? Here's how. While we're at it, let's make sure to configure the search tool that works best with this theme.

1. Edit the `config.toml` file and add these lines to the `config.toml` file. This example shows setting the `themeVariant` to `green`.
```
[params]
themeVariant = "green"
```
1. You can make sure that the theme works with the `lunr.js` [JavaScript search engine](https://lunrjs.com/) by adding these lines to the `config.toml` file.
```
[outputs]
home = [ "HTML", "RSS", "JSON"]
```

## What's next

* [Working with content in GitHub repositories](https://docslikecode.com/learn/04-add-content-workflow/)
* [Continuous Deployment (CD) for Documentation Sites](https://www.docslikecode.com/learn/05-cd-for-docs/)
* [Set Up Automated Tests for Docs](https://www.docslikecode.com/learn/06-test-docs-as-code/)

## Evaluating options

* [Evaluating Static Site Generator themes](https://www.docslikecode.com/learn/07-evaluating-ssg-themes/)
* [Evaluating table layouts and formatting](https://www.docslikecode.com/learn/08-evaluating-table-layouts/)
* [Evaluating Static Site Generator search options](https://www.docslikecode.com/learn/09-ssg-search-implementations/)

## Additional references

* [Hugo Quickstart](https://gohugo.io/getting-started/quick-start/)
* [Hugo Themes web site](https://themes.gohugo.io/)
