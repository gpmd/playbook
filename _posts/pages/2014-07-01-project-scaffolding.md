---
layout: page
published: true
title: Project Scaffolding
permalink: "development/project-scaffolding"
---

When setting up new projects we follow the process outlined below.

## Directory structure

```
my-project/shared
my-project/site
my-project/sql
```

* `shared` contains files/folders we don't want to track in Git, such as environment files, log files, media/uploads directories etc. These files/folders are symlinked into their relevant locations in the project.
* `site` is the root directory of the main project. It contains things such as `public_html`, the project's theme/skin directory (symlinked into the relevant location) and Composer and Vagrant configs.
* `sql` contains databases we want to import into our Vagrant virtual machine.

## Vagrant

We work in virtual machines in order to maintain a consistent development environment. Each project has a Vagrant config based on this [boilerplate](https://github.com/gpmd/vagrant-puppet-boilerplate).

## Composer

We use [Composer](https://getcomposer.org/) to manage external PHP packages/modules.

Composer uses a file called `composer.json` to define a project's dependencies. Below is a very simple example:

```Json
{
    "require": {
        "gpmd/mypackage": "*"
    }
}
```

## Set-up script

## Git Hooks

## Grunt

We use [Grunt](http://gruntjs.com/) to automate front-end tasks, such as minifying images, compiling SCSS into CSS, uglifying Javascript and so on.

A simple Grunt setup may look something like this:

```
my-project/site/theme/dist
my-project/site/theme/grunt
my-project/site/theme/src
my-project/site/theme/Gruntfile.js
my-project/site/theme/package.json
```

* `src` contains our working files
* `dist` is generated automatically each time we run the build process
* `Gruntfile.js` contains the core Grunt config
* `grunt` contains the config for each individual grunt task (requires [load-grunt-config](https://github.com/firstandthird/load-grunt-config))

## Front-end optimisation