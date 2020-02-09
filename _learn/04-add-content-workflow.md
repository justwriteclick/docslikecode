---
title: "Working with content in GitHub repositories"
layout: learn
image:
  path: /images/learn/octocat.png
  thumbnail: /images/learn/octocat-github-logo400x200.png
  caption: "Logo from [GitHub](https://github.com)"
---

This section goes through the workflow for adding content, editing pages, and generally working on a docs site in a GitHub repo.

## Prerequisites

* A GitHub, GitLab, or other Git online account.
* A Git repository already created online in one of those services (GitHub, GitLab, or other) and already cloned locally.

These steps are shown from within a directory that contains the Git repository files.

## Add content to the site

Once you have created files required by your static site generator, you can start writing. Begin with the index, or home page.

For Sphinx, you can write in either Restructured Text (`.rst`) or Markdown (`.md`). For Jekyll and Hugo, you write your source files in Markdown.

Introduce your documentation and what you intend for the reader to find on the docs site. Explain some background, and feel free to add more pages with the `.rst` or `.md` file extension.

You can organize your source documentation files in folders, and those folder names become part of the URL for the documentation page.

A simple starter set of files could look like this for Sphinx:
```
source/index.rst
source/prerequisites.rst
source/how-to-create-a-project.rst
source/reference-list.rst
```

Or this for Jekyll:
```
index.html
_pages/prerequisites.md
_pages/how-to-create-a-project.md
_pages/reference-list.md
```
Or this for Hugo:
```
content/_index.md
content/prerequisites.md
content/how-to-create-a-project.md
content/reference-list.md
```

Once you have your starter files, you want to create a new branch and add them to another commit.
```
$ git checkout -b new-branch
Switched to a new branch 'new-branch'
$ git add .
$ git commit -a -m "Adds initial set of doc files"
[new-branch b5ce0d9] Adds initial set of doc files
 3 files changed, 3 insertions(+)
 create mode 100644 how-to-create-a-project.rst
 create mode 100644 prerequisites.rst
 create mode 100644 reference-list.rst
$ git push origin new-branch
Counting objects: 5, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (5/5), 573 bytes | 573.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0)
To github.com:annegentle/do-docs-as-code.git
 * [new branch]      new-branch -> new-branch
```

## Creating a pull request for the new branch

1. Next, go to the GitHub URL for the new repo, `do-docs-as-code`. For example, with a username, `annegentle`, the URL would be https://github.com/annegentle/do-docs-as-code. You should see a new yellow notifier on the **Code** tab:
`Your recently pushed branches: new-branch (5 minutes ago)`
1. Click the **Compare & pull request** button.
1. On the Open a Pull Request window, observe that your commit message becomes filled in the web form, comparing your `new-branch` to the base `master` branch.
1. Click **Create pull request**.
1. Once GitHub checks for merge compatibility, you should see a green button and click it, **Merge pull request**.
1. Click **Confirm merge** to merge your new-branch into the master branch on GitHub.
1. Notice that your local copy of the master branch does not yet contain these changes. In your Terminal window, run these commands to update your master branch locally.

```
$ git checkout master
$ git remote update
$ git pull origin master
```
Now, your local environment is all ready for new changes.
1. Repeat these steps each time you want to make a new branch, make a commit, make a PR, merge it, and then get your local all set up to begin again!

## Editing the site with a branch and pull request workflow

When you're the only person working in a repo, you can use a simple workflow, where you simply create a branch for whatever amount of work you want to do, and then merge that branch to the master branch when you want to publish. If you're on a small team, each team member can do the same, keeping the workflow simple, where the `master` branch is the one that is published each time. Here's a walkthrough for a branch and pull workflow.

1. Every time you work in a folder that's a GitHub repo, run a `git status` command to figure out if you have any changes on the branch you're working within.
  ```
  $ git status
  ```
1. Once you know what changes you have on a local branch, decide whether to keep working in that branch, or start over with the current `master` branch. To start again with a new copy of master from the remote, run these commands to update your master branch locally.
  ```
  $ git checkout master
  $ git remote update
  $ git pull origin master
  ```
1. Next, create a new branch to make new changes in:
  ```
  $ git checkout -b new-branch
  ```
1. Make your edits in the files, and add new files if needed.
1. Double-check that the changes are what you expect, by building locally.

    These are the basic build commands on the three SSGs:
    **Sphinx**:
    ```
    $ make html
    ```
    Open `build/html/index.html` in your browser.

    **Jekyll**:
    ```
    $ bundle exec jekyll serve
    ```
    Open http://127.0.0.1:4000 in your browser.
    **Hugo**:
    ```
    $ hugo server
    ```
    Open http://127.0.0.1:1313 in your browser.

    Repeat the editing and building steps to your satisfaction.

1. Once you have the changes you need, commit to the branch:
  ```
  $ git commit -a -m "These are my changes, such as edits"
  ```
1. Now, push your changes to the remote so that you can create a pull request.
  ```
  $ git push origin new-branch
  ```
1. Open the GitHub.com repository URL to open the Pull Request, comparing `new-branch` to `master`.
1. On the Pull Request in GitHub, make sure that your continuous integration tests pass.
1. Once you are satisfied with all the changes, merge the changes to the `master` branch by clicking the Merge button on GitHub.
1. Now, look for the continuous deployment site online on readthedocs.org, GitHub Pages, or Netlify.
1. Don't forget to reset your local branch to the `master` branch that is now available in the newly-merged master on GitHub! This is the same as in step 2 above, but uses semi-colons so you can run the commands all in one line.
  ```
  $ git checkout master; git remote update; git pull origin master
  ```

## What's next

* [Continuous Deployment (CD) for Documentation Sites](https://www.docslikecode.com/learn/05-cd-for-docs/)
* [Set Up Automated Tests for Docs](https://www.docslikecode.com/learn/06-test-docs-as-code/)

## Evaluating options

* [Evaluating Static Site Generator themes](https://www.docslikecode.com/learn/07-evaluating-ssg-themes/)
* [Evaluating table layouts and formatting](https://www.docslikecode.com/learn/08-evaluating-table-layouts/)
* [Evaluating Static Site Generator search options](https://www.docslikecode.com/learn/09-ssg-search-implementations/)

## Additional references

* [Comparing Git Workflows](https://www.atlassian.com/git/tutorials/comparing-workflows)
* [Git Branching - Branching Workflows](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
