# Docs Like Code

## The Website

This website is intended to offer stories and articles about how to treat docs like code, and lessons learned along the way. 

## To Contribute

You can directly submit a pull request using the fork-and-pull workflow to add an article, or submit to the [justwriteclick/docs-like-code-stories](https://github.com/justwriteclick/docs-like-code-stories) repo if you want to follow a question-and-answer template.

## Theme Colophon
Theme courtesy of https://mmistakes.github.io/so-simple-theme/

## To Build Locally (Mac only)

Test your additions and changes to content by running a local build.

To prepare your environment to build locally, you need to install brew, bundler.io, and Ruby version manager:

1. Use brew to install a Ruby version manager.

   ```
   $ brew install rbenv ruby-build
   ```

1. Add rbenv to bash so that it loads every time you open a terminal.

   ```
   $ echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
   ```

1. Source your `.bash_profile` file.

   ```
   $ source ~/.bash_profile
   ```

1. Install the version Ruby we need:

   ```
   $ rbenv install 2.3.1
   $ rbenv global 2.3.1
   $ ruby -v
   ```
 
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

> ***TIP***  
> Leave the serve terminal open and running. Every time you save changes to a file, it automatically regenerates the site so you can test the output immediately. The only file where changes require a restart is the `_config.yml` file.

## To build locally (Docker required)

1. Install Docker Community Version.

2. In the root directory where the `docslikecode` repo is cloned, create a file named `Dockerfile` containing:

```
FROM grahamc/jekyll:latest

# Install whatever is in your Gemfile
WORKDIR /tmp
ADD Gemfile /tmp/
ADD Gemfile.lock /tmp/
RUN bundle install

# Change back to the Jekyll site directory
WORKDIR /src

```
3. Create a `_config.dev.yml` file, also in the root directory, containing the following:

```
# Develop override settings
# Use when building with Docker container and preview.sh script locally

url                      : http://192.168.99.100:4000

# Analytics
analytics:
  provider               : false
```

4. Create a `preview.sh` file, also in the root directory, containing the following:

```
#!/usr/bin/env bash

# Set to the name of the Docker machine you want to use
DOCKER_MACHINE_NAME=default

# Set to the name of the Docker image you want to use
DOCKER_IMAGE_NAME=dlc-site

# Stop on first error
set -e

# Create a Docker host
if !(docker-machine ls | grep "^$DOCKER_MACHINE_NAME "); then
  docker-machine create --driver virtualbox $DOCKER_MACHINE_NAME
  fi

  # Start the host
  if (docker-machine ls | grep "^$DOCKER_MACHINE_NAME .* Stopped"); then
    docker-machine start $DOCKER_MACHINE_NAME
    fi

    # Load your Docker host's environment variables
    eval $(docker-machine env $DOCKER_MACHINE_NAME)

    if [ -e Dockerfile ]; then
      # Build a custom Docker image that has custom Jekyll plug-ins installed
        docker build --tag $DOCKER_IMAGE_NAME --file Dockerfile .

	  # Remove dangling images from previous runs
	    docker rmi -f $(docker images --filter "dangling=true" -q) > /dev/null 2>&1 || true
	    else
	      # Use an existing Jekyll Docker image
	        DOCKER_IMAGE_NAME=grahamc/jekyll
		fi

		echo "***********************************************************"
		echo "  Your site will be available at http://$(docker-machine ip $DOCKER_MACHINE_NAME):4000"
		echo "***********************************************************"

		# Start Jekyll and watch for changes
		docker run --rm \
		  -e JEKYLL_ENV=production \
		  --volume=/$(pwd):/src \
		    --publish 4000:4000 \
		      $DOCKER_IMAGE_NAME \
		       serve --watch --drafts --force_polling -H 0.0.0.0
 ```
