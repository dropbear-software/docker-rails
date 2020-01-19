# Using Docker for local Rails development

## Overview
This repository is designed to provide you with a completely self-contained Rails application development environment.

## Getting Setup
### 1. Build Docker Images
In order to get started you are going to need to first `build` the appropriate environment by typing `docker-compose build` in the root directory of this project.

This will ensure that it build all of the necesarry images that will be required to both bootstrap a Rails project as well as providing an environment that you can continue to use afterwards.

### 2. Create a new Rails application
As a part of building the images we have created a container based on a slimmed down version of Debian 10 Buster Linux which comes preinstalled with the latest version of Ruby as specified in the `RUBY_BUILD` variable inside the docker-compose.yml file at the root of this project. It also fetches the latest version of the rails gem as a part of the setup process.

Normally in order to create a new Rails application we might just type `rails new` into our terminal but as our development environment is containerised we need to instead perform these commands from the console of our Debian container. In order to access this console we will type `docker-compose run --rm runner` which asks Docker Compose to run the runner service inside of a throwaway container that will automatically remove itself when we are done with it.

You will then be presented with a regular terminal just like you are used to and from where we can run all of our commands that we might do as a part of the development lifecycle. From here we will run `rails new YourApplicationName --database=postgresql --skip-test --webpack=stimulus`
