# Colophon

How we work and make stuff at GPMD

## About

This is a static site built using [Jekyll](http://jekyllrb.com/) and hosted on [Github Pages](http://pages.github.com/).

## Requirements for local development

* [Ruby](http://www.ruby-lang.org/en/downloads/)
* [RubyGems](http://rubygems.org/pages/download)
* [Jekyll](http://jekyllrb.com/), `$ gem install jekyll`

## Installation

Clone the repo into your project folder:

```
$ git clone https://github.com/gpmd/colophon.git .
```

Run `git fetch` and check out the `gh-pages` branch. From now on all work should be done on the `gh-pages` branch.

## Basic Jekyll usage

To build the project:

```
$ jekyll build
```

To Preview the site locally and watch for changes:

```
$ jekyll serve --watch --baseurl=
```

Then open `http://0.0.0.0:4000` in your browser.

## Deployment

Simply commit and push changes to the `gh-pages` branch to Github. Because Github Pages uses Jekyll to build its pages it will automatically build and publish the site for you, pretty much immediately.

```
$ git push origin gh-pages
```

## Author

**Matt Bailey**

* [https://github.com/matt-bailey](https://github.com/matt-bailey)
* [https://twitter.com/_mattbailey](https://twitter.com/_mattbailey)

## License

*To do...*