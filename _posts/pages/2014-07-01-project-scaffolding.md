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

![logo_wide-cab47086.png](/assets/uploads/logo_wide-cab47086.png)

We work in virtual machines in order to maintain a consistent development environment. Each project has a Vagrant config based on this [boilerplate](https://github.com/gpmd/vagrant-puppet-boilerplate).

## Composer

![logo-composer-transparent.png](/assets/uploads/logo-composer-transparent.png)

We use [Composer](https://getcomposer.org/) to manage external PHP packages/modules.

## Set-up script

**Example directory structure:**

```
my-project/site/.shell/frontend-setup.sh
```

**Example [frontend-setup.sh](https://gist.github.com/matt-bailey/22122af72c7be33e3bf6#file-frontend-setup-sh) file →**

We use set-up scripts for some of the 'first run' tasks. For example, our `frontend-setup.sh` script creates symlinks to our Git hooks, installs Node modules and Bower components, and runs the front-end build process for the first time.

## Git

![Git-Logo-1788C.png](/assets/uploads/Git-Logo-1788C.png)

We use [Git](http://git-scm.com/) as out version control system. We run our own Git server, and also use [Github](https://github.com/).

### Gitflow

We use Git as out version control system. We follow a process called Gitflow

### Git hooks

**Example directory structure:**

```
my-project/site/.githooks/post-merge
```

**Example [post-merge](https://gist.github.com/matt-bailey/bfdaaa290954e1a23f2f#file-post-merge) file →**

We use Git hooks to automate the running of repetitive tasks when certain Git commands are run. For example, our `post-merge` hook automatically checks to see if any of our Node modules or Bower components need installing, updating or removing, and runs the Grunt build process whenever we `pull` or `merge`.

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
* `package.json` defines the Grunt task dependencies required for the build

## Bower

We use [Bower](http://bower.io/) to manage external front-end components.

## Optimisation

Building on [research and recommendations by Ilya Gregorik at Google](https://www.youtube.com/watch?v=YV1nKLWoARQ&feature=youtu.be), we have invested time in optimising the critical rendering path on our projects. This focuses particularly on optimising sites when viewed on lower bandwidth 'mobile' devices.

** Images **

Theme images are optimised using the [grunt-contrib-imagemin](https://github.com/gruntjs/grunt-contrib-imagemin) Grunt task.

We also use the `picture` element (and [Picturefill 2](http://scottjehl.github.io/picturefill/) polyfill as a fallback for legacy browsers) to serve up different sized images for different sized screens and bandwidth capabilities.

** CSS **

We develop CSS in a modular and layered, component based fashion (using [SCSS](http://sass-lang.com/) or [Less](http://lesscss.org/) as preprocessors), making it easy to create page, or feature specific CSS files. We minify the CSS on all our production sites.

We inline critical CSS in the head, and then load less critical CSS conditionally and in a non-blocking manner (asynchronously) in order to speed up the page rendering time using [this script](https://gist.github.com/matt-bailey/602b40c77a5d3381ff26#file-async-and-conditional-css-loading-html).

** Javascript **

We load javascript asychronously from the foot of the page in order to not block the rendering. We use an asynchronous script loader called [Yep Nope](http://yepnopejs.com/) for this purpose. We minify all the Javascript on all our production sites, and concatenate as much of it as possible into page, or feature specific files.