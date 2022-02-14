# Docs Like Code

[![Netlify Status](https://api.netlify.com/api/v1/badges/a47374ca-f840-4191-b695-f34651a2078c/deploy-status)](https://app.netlify.com/sites/docs-like-code/deploys)

## The Website

This website is intended to offer stories and articles about how to treat docs like code, and lessons learned along the way. You are welcome to tell your story here as well.

## To Contribute

You can directly submit a pull request using the fork-and-pull workflow to add an article, or submit to the [justwriteclick/docs-like-code-stories](https://github.com/justwriteclick/docs-like-code-stories) repo if you want to follow a question-and-answer template.

Pushing to the `build` branch lets you preview the build output using Netlify. You must log into Netlify to view the preview deploy.

Pushing to the `main` branch builds output to https://www.docslikecode.com using Netlify. Auto publishing is on as a setting in Netlify, so deploys from `main` are published automatically.

## Theme Colophon
Theme courtesy of https://mmistakes.github.io/so-simple-theme/

## To Build Locally (MacOS)

Test your additions and changes to content by running a local build.

On macOS you need to install brew, bundler.io, and Ruby version manager so that you can use a particular version of Ruby:

1. Use brew to install a Ruby version manager.

   ```
   $ brew install rbenv ruby-build
   ```

1. Add rbenv to bash so that it loads every time you open a terminal. If you are using macOS Catalina, your profile file may be `.zshrc`.

   ```
   $ echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
   ```
   or
   ```
   $ echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.zshrc
   ```

1. Source your `.bash_profile` file. If you are using macOS Catalina, your profile file may be `.zshrc`.

   ```
   $ source ~/.bash_profile
   ```
   or
   ```
   $ source ~/.zshrc
   ```

1. Install the required Ruby version:

   ```
   $ rbenv install 2.7.1
   $ rbenv global 2.7.1
   $ rbenv version
   ```
   In return, you should see `ruby 2.7.1 2.7.1 (set by /Users/username/docslikecode/.ruby-version`.

1. Run `gem install bundle` to install the bundler gem, which helps with Ruby dependencies.
1. Run `bundle install` the first time you are in the `docslikecode` directory.

To build locally:
Once you have completed preparing your environment, then you can build locally and review the site in your browser.

1. Run the serve command.

   ```
   $ bundle exec jekyll serve
   ```

1. Use the **Server address** URL  `http://127.0.0.1:4000/` in a browser to preview the content.
1. Press `Ctrl+C` in the serve terminal to stop the server.

> ***Tip***  
> Leave the serve terminal open and running. Every time you save changes to a file, it automatically regenerates the site so you can test the output immediately. The only file where changes require a restart is the `_config.yml` file.
