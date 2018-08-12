---
title: "Set Up Go with Hugo"
image:
  path: /images/learn/hugo-docs-page.png
  thumbnail: /images/learn/go-logo400x200.png
  caption: "Screenshot using Gravatar theme"
---

To build Hugo sites locally, install Homebrew and Hugo. You do not need to install Go to use Hugo as your static site generator. These instructions are for a Mac or Linux system, but you can also read the Windows installation instructions on the [gohugo.io](https://gohugo.io/getting-started/installing#windows) site.

Since Hugo is built on Go, you can use the binary for your operating system. No need to maintain a development environment. Upgrades are easy too, get a new binary and install it and you're upgraded.

## Set up Hugo on Windows with Git Bash and Docker

You can also set up Docker and then use this [Docker image](https://hub.docker.com/r/jguyomard/hugo-builder/), and set up alias commands for `hugo` running in Docker, but using the same `hugo` commands in Git Bash on Windows.

## Set up Hugo on MacOS
1. Install Homebrew. See the [Homebrew site](https://brew.sh) for instructions.
1. Use Homebrew to install Hugo.

   ```
   $ brew install hugo
   ```

1. Verify the `hugo` installation by checking the version value.

   ```
   $ hugo version
   Hugo Static Site Generator v0.42.1 darwin/amd64
   ```

## Starting a Hugo site

For a Hugo static site, you can choose your specific theme after you create the source files. The theme we'll use in this tutorial is hugo-theme-learn(). To start a new site in the current folder, run:

   ```
   $ hugo new site docs-as-code
   ```

1. Take a look at the files created in the directory with an `ls` command:

```
$ ls -A
archetypes	content		layouts		themes
config.toml	data		static
```
1. Edit `config.toml` in any text editor you like to get started. Choose a title for your site and the theme, in our case, `hugo-theme-learn`. The theme name in your configuration file must match the name of the specific theme directory inside the `/themes` directory, so we will add those files in the next step.

```
baseURL = "http://example.org/"
languageCode = "en-us"
title = "Learning Hugo Site"
theme = "hugo-theme-learn"
```
1. To get the theme files in the `/themes` directory, change to the themes directory, and then use a `git clone` command to get the required theme files.
```
$ cd themes
$ git clone https://github.com/matcornic/hugo-theme-learn.git
```
1. For Hugo, the `content` folder contains the site source content. For your home page, make an `_index.md` document in the `content` folder and write it with Markdown content. Switch back up one level since you just cloned the theme files.
```
$ cd ..
$ hugo new _index.md
```
1. Next, add a new page using the `hugo` command, `hugo new`:
```
$ hugo new prerequisites.md
/Users/agentle/src/hugo-example/doc-machine/content/prerequisites.md created
```
1. You can keep adding files with the `hugo new` command so that the Markdown files are pre-populated with the front matter:

```
---
title: "Prerequisites"
date: 2018-06-16T10:38:19-05:00
draft: true
---
```

## Build a Hugo site locally

Once you've prepared your local system, you can build locally and review the site in your browser.

For Hugo, it's important to know that draft pages are only served when using the `-D` parameter.

1. Run the `hugo server` command with the `-D` parameter.

   ```
   $ hugo server -D

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

1. Open the **Web Server** URL, `http://localhost:1313/` in your local browser to view the site.

1. Press `Ctrl+C` in the server terminal to stop the Hugo server.

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
