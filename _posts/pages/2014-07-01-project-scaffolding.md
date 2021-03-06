---
layout: page
published: true
title: Project Scaffolding
permalink: "development/project-scaffolding"
---

When setting up new projects we follow the process outlined below.

---

## 1. Directory structure

```
my-project/shared
my-project/site
my-project/sql
```

* `shared` contains files/folders we don't want to track in Git, such as environment files, log files, media/uploads directories etc. These files/folders are symlinked into their relevant locations in the project.
* `site` is the root directory of the main project. It contains things such as `public_html`, the project's theme/skin directory (symlinked into the relevant location) and Composer and Vagrant configs.
* `sql` contains databases we want to import into our Vagrant virtual machine.

---

## 2. Vagrant

![logo_wide-cab47086.png](/assets/uploads/logo_wide-cab47086.png)

We work in virtual machines in order to maintain a consistent development environment. Each project has a Vagrant config based on this [boilerplate](https://github.com/gpmd/vagrant-puppet-boilerplate).

---

## 3. Composer

![logo-composer-transparent.png](/assets/uploads/logo-composer-transparent.png)

We use [Composer](https://getcomposer.org/) to manage external PHP packages/modules.

---

## 4. Set-up script

```
my-project/site/.shell/frontend-setup.sh
```

**Example [frontend-setup.sh](https://gist.github.com/matt-bailey/22122af72c7be33e3bf6#file-frontend-setup-sh) file →**

We use set-up scripts for some of the 'first run' tasks. For example, our `frontend-setup.sh` script creates symlinks to our Git hooks, installs Node modules and Bower components, and runs the front-end build process for the first time.

---

## 5. Git

![Git-Logo-1788C.png](/assets/uploads/Git-Logo-1788C.png)

We use [Git](http://git-scm.com/) as out version control system. We run our own Git server, and also use [Github](https://github.com/).

#### Gitflow

We follow a Git branching model called [Gitflow](/development/gitflow).

#### Git hooks

```
my-project/site/.githooks/post-merge
```

**Example [post-merge](https://gist.github.com/matt-bailey/bfdaaa290954e1a23f2f#file-post-merge) file →**

We use Git hooks to automate the running of repetitive tasks when certain Git commands are run. For example, our `post-merge` hook automatically checks to see if any of our Node modules or Bower components need installing, updating or removing, and runs the Grunt build process whenever we `pull` or `merge`.

---

## 6. Grunt

![grunt-logo.png](/assets/uploads/grunt-logo.png)

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

---

## 7. Bower

![bower-logo.png](/assets/uploads/bower-logo.png)

We use [Bower](http://bower.io/) to manage external front-end components.

---

## 8. Optimisation

Building on [research and recommendations by Ilya Gregorik at Google](https://www.youtube.com/watch?v=YV1nKLWoARQ&feature=youtu.be), we are investing time in "optimising the critical rendering path". This focuses particularly on optimising sites when viewed on lower bandwidth 'mobile' devices.

#### Images

1. Theme images are optimised using the [grunt-contrib-imagemin](https://github.com/gruntjs/grunt-contrib-imagemin) Grunt task.
2. We also use the `picture` element (and [Picturefill 2](http://scottjehl.github.io/picturefill/) polyfill as a fallback for legacy browsers) to serve up different sized images for different sized screens and bandwidth capabilities.

#### CSS

1. We develop CSS in a modular and layered, component based fashion (using [SCSS](http://sass-lang.com/) or [Less](http://lesscss.org/) as preprocessors), making it easy to create page, or feature specific CSS files.
2. We maintain a consistent CSS writing style ([principles](https://github.com/necolas/idiomatic-css)).
3. We minify the CSS on all our production sites.
4. We inline critical CSS in the head.
5. We then load less critical CSS conditionally, and in a non-blocking manner (asynchronously) in order to speed up the page rendering time using [this script](https://gist.github.com/matt-bailey/602b40c77a5d3381ff26#file-async-and-conditional-css-loading-html).

#### Javascript

1. We load javascript asychronously from the foot of the page in order to not block the rendering.
2. We use an asynchronous script loader called [Yep Nope](http://yepnopejs.com/) for this purpose.
3. We minify all the Javascript on all our production sites, and concatenate as much of it as possible into page, or feature specific files.

## 9. Documentation

All projects contain clear and easy-to-follow developer documentation ([example](https://github.com/gpmd/vagrant-puppet-boilerplate/blob/master/README.md)).