---
title: "Set Up Automated Tests for Docs"
image:
  path: /images/learn/travis-ci-logo400x200.png
  thumbnail: /images/learn/travis-ci-logo400x200.png
  caption: "Logo from [Travis CI](https://travis-ci.org)"
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

## Test with Travis CI

 First you must set up a Travis CI account at https://travis-ci.org by connecting to your GitHub account.

 Open source and public repositories are free to use with Travis CI. Read more about plans and pricing at https://travis-ci.com/plans if you need to build docs in private repos.

 Next, configure your docs repository to use Travis to run your test scripts, such as the link checker.

### Enable Travis builds for your GitHub repository

 1. Log in to https://travis-ci.com and go to your profile.
 1. Look for the repository in the list that you want to enable doc builds.
 1. Toggle the switch for that repository.
 1. Next, make sure you have scripts available to run as tests for each pull request.

### Create automation scripts in your repository

For Sphinx, let's set up a script that only checks links, both external and internal.

1. In your file editor, create a `linkcheck.sh` file in a `scripts` directory.
1. Edit the file so that it contains the following bash commands to make the script:
  ```
  !/usr/bin/env bash
  # halt script on error
  set -e
  # Build locally, deleting any existing doctrees, and then check links
  sphinx-build -E -W -b linkcheck source build
  ```
1. Save the `linkcheck.sh` file in a `scripts` directory.

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

For Jekyll, follow the steps in this Jekyll documentation page, [Travis Ci](https://jekyllrb.com/docs/continuous-integration/travis-ci/).

To see a working example of Jekyll with TravisCI, look at the [versions-jekyll](https://github.com/justwriteclick/versions-jekyll/) repository. Here's the `.travis.yml` file:
```
language: ruby
rvm:
- 2.2.5

script: ./script/build-travis.sh

env:
  global:
  - NOKOGIRI_USE_SYSTEM_LIBRARIES=true # speeds up installation of html-proofer

sudo: false # routes build to container-based infrastructure for a faster build
```

The `/script/build-travis.sh` file contains these lines. Notice that the script passes in the `_config.yml` file.
```
#!/usr/bin/env bash
set -e # halt script on error

bundle exec jekyll build --config _config.yml
```

If you wanted to check links instead, you could make a link checking script like so:
```
#!/usr/bin/env bash
set -e # halt script on error

bundle exec jekyll build
bundle exec htmlproofer ./_site
```

Look for more inspiration beyond link checking in the additional resources section. Enjoy higher-quality doc builds with some quality tests up front!

## Additional resources

[Test the Docs](https://testthedocs.org/)

Pantheon docs examples
* [Merge conflict test](https://github.com/pantheon-systems/documentation/blob/master/scripts/merge_conflicts.sh)
* [CircleCI example configuration](https://github.com/pantheon-systems/documentation/blob/master/circle.yml)

[How we spotted--and fixed--11 errors in our docs with our new markdown proofer](https://circleci.com/blog/markdown-proofer/)
