---
title: "Set Up Sphinx with Python"
image:
  path: /images/learn/sphinx-docs-page.png
  thumbnail: /images/learn/python-logo400x200.png
  caption: "Screenshot from Read the Docs theme"
---

There are two major versions of Python active today, Python 2 and Python 3. Sphinx works with either version. Python 3 is the current and recommended version, however many scripts and programs were written in Python 2 and have yet to be upgraded.

Mac OS includes a version of Python 2 by default, but it is NOT the latest version of Python 2. Install the latest version of Python 2 using `homebrew`, a package manager on Mac.

#### Installing Python 2.7.14 on Mac

1. Open a terminal and use `brew` to install Python 2.7.14.

    ```bash
    brew install python@2
    ```

#### Installing Python 3.6.5

You also want the latest version of Python 3 available.

1. Open a terminal and use brew to install Python 3.6.5.

    ```bash
    brew install python
    ```

#### Verifying Python 2 and Python 3

1. Open a terminal.
1. Verify that Python 2 is correctly installed.

    ```bash
    python2.7 -V
    ```

    ```bash
    # Expected Output
    Python 2.7.14
    ```
1. Verify that Python 3 is correctly installed.

    ```bash
    python3.6 -V
    ```

    ```bash
    # Expected Output
    Python 3.6.5
    ```

1. Check the version set as the default version, the version of Python that is executed when you simply enter `python`.  The default version of Python remains a Python 2.7 version.

    ```bash
    python -V
    ```

    ```bash
    # Expected Output
    Python 2.7.14
    ```
## Set Up Virtual Environment

Let's ensure that you know how to create Python Virtual Environments for each version of Python. These [Python Virtual Environments](https://docs.python.org/3/tutorial/venv.html) provide a method of creating isolated "environments" where you can work with specific versions of Python along with independent sets of libraries and dependencies.

Most people use Virtual Environments because it's a recommended practice when working in Python.

**Python 3**

1. First create a Python 3 virtual environment using the `venv` module included with Python 3. Notice using `python3.6` to be clear which version of Python you want.

    ```bash
    python3.6 -m venv py3-sphinx
    ```

1. Now "activate" the environment. Look for the name of the virtual environment enclosed in parenthesis after activation.

    ```bash
    source py3-sphinx/bin/activate
    ```

    ```bash
    # Expected Output
    (py3-sphinx) $
    ```

1. Now verify that `python` is now linked to Python 3.

    ```bash
    (py3-sphinx) $ python -V
    ```

    ```bash
    (py3-sphinx) $ Python 3.6.5
    ```

## Install Sphinx in the Virtual Environment

1. With the virtual environment activated, install Sphinx.

   ```bash
   (py3-sphinx) $ pip install sphinx
   ```

1. To verify that sphinx is installed, run the `sphinx-build` command with the `--help` parameter.

   ```bash
   (py3-sphinx) $ sphinx-build --help
   ```

## Create a Basic Sphinx Project

1. Create a new directory for your project:
```
(py3-sphinx) $ mkdir do-docs-as-code
```
1. With the virtual environment still activated, run `sphinx-quickstart`, which creates a starting project for a Sphinx documentation project.

```bash
$ sphinx-quickstart
```

1. Answer all the questions from the prompts.

You can choose enter to pick all the defaults and get a working project in the current directory (`.`).

Some notes for the context of this tutorial:
* You can either use a directory named `_build` within the root path, or have separate `source` and `build` directories, which is the default.
* Note that you can choose "githubpages set to yes" to create a `.nojekyll` file to publish the document on GitHub pages. In our case, though, our example builds to Read the Docs, so you can use the defaults throughout.

1. Once you have the basics answered, the script creates the necessary files and you can edit those to your liking.
1. Create a couple of `.rst` files and add skeleton information for starters.
```
$ touch source/prerequisites.rst
$ touch source/about.rst
```
1. Edit those new `.rst` files in your favorite text editor.
1. Now, you can build the docs to see the changes locally:
```bash
$ make html
```
1. In your browser, open the `build/html/index.html` file to take a look at your Sphinx site locally. You can also look at `build/html/prerequisites.html` and `build/html/about.html`.
1. Make sure you commit your changes to the Git repository by following the steps in "Add the Project to GitHub."
