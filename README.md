# ezplatform-docker
Docker setup for eZPlatform

# Usage
## Add as git submodule
In your project folder, add this repository as a submodule:

    git submodule add -b <branch-name> git@github.com:benegetto/ezplatform-docker.git

## Setup .env file
Enter submodule folder and copy file .env.dist into .env, then edit it

    cd ezplatform-docker
    cp .env.dist .env


## Build
From submodule folder build with docker compose

    docker-compose build

## Up
    docker-compose up -d

# First time setup

## Install dependencies
There is a problem with cache:clear script, to make it work edit composer.json at post-install script section replace "cache:clear" with "cache:clear --no-warmup". Now you can run:

    docker-compose exec php-fpm composer install

## Create clean ezplatform database
If starting from scratch, you should setup a clean db:

    docker-compose exec php-fpm composer ezplatform-install


# READY!
Now head to http://localhost and you should see eZPlatform welcom page.
At http://localhost/admin you'll find the backoffice, and at http://localhost:8080 the phpMyAdmin interface.