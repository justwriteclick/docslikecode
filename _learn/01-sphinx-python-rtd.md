---
title: "Set Up Sphinx with Python"
layout: learn
image:
  thumbnail: /images/learn/python-logo400x200.png
  caption: "Python and Sphinx"
---

Sphinx works with either major versions of Python active today, Python 2 and Python 3. Python 3 is the current and recommended version, and Python 2 is an unsupported Python version. Sphinx is a documentation tool that creates HTML, CSS, and JavaScript files from [ReStructured](http://docutils.sourceforge.net/rst.html) text files.

In case you need both versions, refer to the [Downloads on the Python site](https://www.python.org/downloads/).

## Prerequisites

* MacOS or a Linux-based environment in which to install Python.
* Homebrew installed on MacOS. Get installation instructions from https://brew.sh/.

## Installing Python 3.x

You want the latest version of Python 3 available.

1. Open a terminal and use `brew` to install the latest Python 3.x (currently 3.7).

    ```
    brew install python
    ```

### Verifying the Python installation

1. Open a terminal.
1. Verify that Python 3 is correctly installed.

    ```
    python -V
    ```
    Expected output for February 2020:
    ```
    Python 3.7.6
    ```

## Set Up Virtual Environment

Let's ensure that you know how to create Python Virtual Environments for each version of Python. These [Python Virtual Environments](https://docs.python.org/3/tutorial/venv.html) provide a method of creating isolated "environments" where you can work with specific versions of Python along with independent sets of libraries and dependencies.

Most people use Virtual Environments because it's a recommended practice when working in Python to ensure a known starting point or state.

**Python 3**

1. First create a Python 3 virtual environment using the `venv` module included with Python 3.

    ```
    python -m venv py3-sphinx
    ```

1. Now "activate" the environment. Look for the name of the virtual environment enclosed in parenthesis after activation.

    ```
    source py3-sphinx/bin/activate
    ```

    ```
    # Expected Output
    (py3-sphinx) $
    ```

1. Now verify that `python` is now linked to Python 3.

    ```
    (py3-sphinx) $ python -V
    ```

    ```
    (py3-sphinx) $ Python 3.7.6
    ```

## Install Sphinx in the Virtual Environment

1. With the virtual environment activated, install Sphinx.

   ```
   (py3-sphinx) $ pip install sphinx
   ```

1. To verify that Sphinx is installed, run the `sphinx-build` command with the `--help` parameter.

   ```
   (py3-sphinx) $ sphinx-build --help
   ```

## Create a Basic Sphinx Project

You can also get familiar with [ReStructured text](http://docutils.sourceforge.net/docs/user/rst/quickstart.html), a plain text markup syntax system that you use to write content in Sphinx documentation. Sphinx can also accept [Markdown](https://commonmark.org/help/) files.

1. Create a new directory for your project:
  ```
  (py3-sphinx) $ mkdir do-docs-as-code
  ```
1. With the virtual environment still activated, run `sphinx-quickstart`, which creates a starting project for a Sphinx documentation project.
  ```
  $ sphinx-quickstart
  ```
1. Answer all the questions from the prompts.
  You can choose enter to pick all the defaults and get a working project in the current directory (`.`).
  >Some notes for the context of this tutorial:
  * If you create a working directory in your home directory, such as `~/src/`, then you can use a `git clone` command in the `src` directory every time. For this tutorial, you can create a directory for your project, such as `~/src/project-name-here`. This directory becomes your root path.
  * You can either use a directory named `_build` within the root path, or have separate `source` and `build` directories, which is the default. To see an example directory structure with a `source` directory, refer to this [justwriteclick/rockthedocs-demo](https://github.com/justwriteclick/rockthedocs-demo) repo on GitHub.
  * When answering the questions, note that you can choose "githubpages set to yes" to create a `.nojekyll` file to publish the document on GitHub pages. In our case, though, our example builds to Read the Docs, so you can use the defaults throughout.

1. Once you have the basics answered, the script creates the necessary files and you can edit those to your liking.
1. Create a couple of `.rst` files and add skeleton information for starters.
  ```
  $ touch source/prerequisites.rst
  $ touch source/about.rst
  ```
1. Edit those new `.rst` files in your favorite text editor.
1. Now, you can build the docs to see the changes locally. Run this command in the directory with the `conf.py` file:
  ```
  $ make html
  ```
1. In your browser, open the `build/html/index.html` file to take a look at your Sphinx site locally. You can also look at `build/html/prerequisites.html` and `build/html/about.html` though they won't be linked to the main page until you add them as a link or in a table of contents entry.
1. Edit the `source/index.rst` file to include links to the additional pages.
   Here is an example:
   ```
    .. toctree::
       :maxdepth: 2
       :caption: Contents:

       about.rst
       prerequisites.rst
   ```
1. Build again to see these changes locally:
  ```
  $ make html
  ```
1. In your browser, refresh the `build/html/index.html` page to see the new Contents with two entries linked.
   ![Rock the docs example site](/images/learn/sphinx-docs-page.png)
1. Make sure you commit your changes to the Git repository by following the steps in [Working with content in GitHub repositories](https://docslikecode.com/learn/04-add-content-workflow/).

## What's next

* [Working with content in GitHub repositories](https://docslikecode.com/learn/04-add-content-workflow/)
* [Continuous Deployment (CD) for Documentation Sites](https://www.docslikecode.com/learn/05-cd-for-docs/)
* [Set Up Automated Tests for Docs](https://www.docslikecode.com/learn/06-test-docs-as-code/)

## Evaluating options

* [Evaluating Static Site Generator themes](https://www.docslikecode.com/learn/07-evaluating-ssg-themes/)
* [Evaluating table layouts and formatting](https://www.docslikecode.com/learn/08-evaluating-table-layouts/)
* [Evaluating Static Site Generator search options](https://www.docslikecode.com/learn/09-ssg-search-implementations/)

## Additional references

* [Sphinx Python Documentation Generator](https://www.sphinx-doc.org/en/stable/)
* [ReStructured text documentation](http://docutils.sourceforge.net/rst.html)
