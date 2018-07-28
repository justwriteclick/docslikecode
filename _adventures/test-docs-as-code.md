---
title: "Set Up Automated Tests for Docs"
image:
  path: /images/chocolate-chip-cookies-lg.jpg
  thumbnail: /images/chocolate-chip-cookies-400x200.jpg
  caption: "Photo from [Pexels](https://www.pexels.com)"
---

You have choices for continuous integration systems that can run documentation tests. For this exercise, let's make a set of minimal tests: build the docs, and check the links and image references.

Bonus tasks for advanced users, think about how you could run a doc linter such as `write-good`, using the basics outlined here.

## Link tests

For all the continuous integration tools, you can create scripts that you store in the repo itself and tell the CI tool to run the script on each pull request as a trigger to run the script. Having CI tests in place means that you or other contributing writers can get information on tests results from each pull request to find out if it passes tests.

For Sphinx, you can run a `sphinx-build` command with parameters that only checks links, both external and internal. You and your contributors can then run this script locally prior to submitting a pull request. Here is an example script, where $BUILD_DIR and $DIRECTORY are the build location and source location:

```
!/usr/bin/env bash
# halt script on error
set -e
# Build locally, and then check links
sphinx-build -E -W -b linkcheck source build
```

For Jekyll, the `html-proofer` gem lets you build and then test links on the built site, both external and internal. You can write a small script to build the site and then check it and then run that script with your CI tool. Jekyll builds the output to a `_site` directory by default. Here's an example script:

```
#!/usr/bin/env bash
# halt script on error
set -e
# clean by deleting any existing output
rm -rf _site
# Build locally, then check links in built output
bundle exec jekyll build
# The url-ignore is optional depending on the links you have in the site
bundle exec htmlproofer ./_site --url-ignore "#"
```

For Hugo, you can use this `htmltest` tool, built for Go, at https://github.com/wjdp/htmltest. For local use, install it and run it locally.

For continuous integration use, you can install it in the CI system and then configure with a YAML file. Hugo automatically puts the built files into a directory named `public` or `static`. See [Using with Hugo](https://github.com/wjdp/htmltest/wiki/Using-With-Hugo).

You can store an `.htmltest.yml` file in the root of the project to configure `htmltest` for the location of the built files, `public`. That file contains a line like this example:

```
DirectoryPath: public
```

## Test with TravisCI

 First you must set up a TravisCI account at https://travis-ci.org by connecting to your GitHub account.

 Open source and public repositories are free to use with TravisCI. Read more about plans and pricing at https://travis-ci.com/plans if you need to build docs in private repos.

### Enable Travis builds for your GitHub repository

 1. Log in to https://travis-ci.com and go to your profile.
 1. Look for the repository in the list that you want to enable doc builds.
 1. Toggle the switch for that repository.

### Create automation scripts in your repository

For Sphinx, let's set up a script that only checks links, both external and internal.

In your file editor, create and save a `linkcheck.sh` file in a `scripts` directory that contains:

```
!/usr/bin/env bash
# halt script on error
set -e
# Build locally, deleting any existing doctrees, and then check links
sphinx-build -E -W -b linkcheck source build
```

### Configure the Travis build with a .travis.yml file

At the most basic level, Travis CI builds run two steps on its infrastructure, install and build. The `install` step in the `.travis.yml` config file makes sure the environment is set up with any dependencies needed for the build to run. The `script` step does the work of building.

For your Sphinx link checker, create and edit a `.travis.yml` file that contains the environment setup and the script you want run:

```
language: python
python:
  - '3.5'
  - '3.4'
  - '2.7'
  script: ./scripts/linkcheck.sh
```

For Jekyll, follow the steps in this documentation:
 https://jekyllrb.com/docs/continuous-integration/travis-ci/



### Test with Circle CI

https://circleci.com/docs/2.0/project-walkthrough/ See also https://circleci.com/blog/markdown-proofer/


https://github.com/pantheon-systems/documentation/blob/master/scripts/merge_conflicts.sh
and
https://github.com/pantheon-systems/documentation/blob/master/circle.yml
