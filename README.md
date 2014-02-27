# Colophon

This site outlines how we work and make stuff at GPMD.

[http://gpmd.github.io/colophon/](http://gpmd.github.io/colophon/)

## About

This is a static site built using [Jekyll](http://jekyllrb.com/) and hosted on [Github Pages](http://pages.github.com/).

## Requirements for local development

* [Ruby](http://www.ruby-lang.org/en/downloads/)
* [RubyGems](http://rubygems.org/pages/download)
* [Jekyll](http://jekyllrb.com/): `gem install jekyll`
* [Sass](https://rubygems.org/gems/sass): `gem install sass`

## Installation

Clone the repo into your project folder:

```bash
$ git clone https://github.com/gpmd/colophon.git .
```

Run `git fetch` and check out the `gh-pages` branch. From now on all work should be done on the `gh-pages` branch.

## Basic Jekyll usage

**To build the project:**

```bash
$ sass assets/stylesheets/main.scss:assets/stylesheets/main.css && jekyll build
```

This runs two commands concurrently: `jekyll build` and `sass`.

**To Preview the site locally and watch for changes:**

```bash
$ jekyll serve --watch --baseurl= & sass --watch assets/stylesheets/:assets/stylesheets
```

This runs two commands concurrently: `jekyll serve` and `sass --watch`.

Then open `http://0.0.0.0:4000` in your browser. You will need to refresh the browser window to see changes.

## Editing content

### For developers

Layouts are a mixture of HTML and [Liquid](http://wiki.shopify.com/Liquid). Content is written in [Markdown](http://daringfireball.net/projects/markdown/).

### For site editors

Sign up for a [Github account](https://github.com/). Ask one of our developers to add you to the Colophon project. Then use [prose.io](http://prose.io/) - when you first visit prose you will be asked to authorise access to your Github account.

More information on using prose can be found on their [website](http://prose.io/#about) and on the [wiki page of their Github repo](http://prose.io/#about).

## Deployment

**Note: Don't forget to pull before you push!**

Simply commit and push changes to the `gh-pages` branch to Github. Because Github Pages uses Jekyll to build its pages it will automatically build and publish the site for you, pretty much immediately.

```bash
$ git push origin gh-pages
```

## Author

**Matt Bailey**

* [https://github.com/matt-bailey](https://github.com/matt-bailey)
* [https://twitter.com/_mattbailey](https://twitter.com/_mattbailey)

## License

*To do...*