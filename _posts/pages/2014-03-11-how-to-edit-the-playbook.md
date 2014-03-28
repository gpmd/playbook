---
layout: page
published: true
title: How To Edit The Playbook
permalink: "how-to-edit-the-playbook"
---

The Playbook is a flat file site built on [Jekyll](http://jekyllrb.com/) and hosted on [GitHub Pages](http://pages.github.com/).

---

**NOTE: If you use [prose.io](http://prose.io/) to edit the site there are a number of known issues/bugs. If you encounter any strange behaviour it's usually best to just close the browser window and then reload the page.**

---

## Signing up and logging in

1. In order to edit the site please ask one of the administrators to add you to the Github team. If you don't have a Github account you can [sign up for a free one here](https://github.com/join).
2. Once you have a Github account and an administrator has added you to the team visit [prose.io](http://prose.io/) and click "Authorise On Github".
3. In the right sidebar click on the group called "GPMD" and you should see the "Playbook" project in the main column. Click on "View Project".

## Project structure

1. Prose is set up to allow you to edit pages and the "Table Of Contents". All other files are hidden from view.
2. Pages are found in `_posts/pages/`.
3. "Table of Contents" can be found in `_includes/table-of-contents.md`.
4. You can also edit `index.md` (FYI, the TOC is automatically pulled in below the content).

## Markdown

1. All content is written in [Markdown](http://daringfireball.net/projects/markdown/basics).
2. For a demonstration of what you can do with Markdown [click here](http://playbook.gpmd.io/markdown-demo/).
3. For a reference of Markdown syntax [click here](http://daringfireball.net/projects/markdown/syntax).

## Style

1. *(To do) Please follow the [style guide](http://playbook.gpmd.io/) when writing content*

## Adding pages

1. Browse to the `_posts/pages/` directory and click "New File".
2. Where it says "Untitled" enter a page name.
3. Delete the sample content and enter your own content.
4. Click on the "Meta Data" icon and enter a "Permalink". For example, if your page is called "My Page" you would enter "my-page" as your permalink, then click "Done".
5. Finally, click the "Save" floppy disk icon and then click "Commit".

## Editing Pages

1. Simply browse to the `_posts/pages/` directory and open one of the pages to edit the contents.
2. Content should be written using Markdown syntax - you can use the simple Prose toolbar if you need some help (see below).
3. You can also use regular HTML in Markdown documents if you want to do something more complicated (see the [Markdown Demo](http://playbook.gpmd.io/markdown-demo/) for examples).
4. Once you have finished editing the page click on the "Save" floppy disk icon and then click "Commit". Your edit should be visible on the site after a few seconds (Github Pages has to rebuild the site after each "Commit").

![prose-toolbar.png](/assets/uploads/prose-toolbar.png)

*The Prose Toolbar*

## Publishing pages

1. When you have created and commited a page for the first time it will still be "Unpublished". To publish it you need to browse away from, and then back to the page.
2. You should now see the word "Unpublished" in the Prose toolbar. Click on "Unpublished", then click on "Save" and finally "Commit".
3. The page will now be published.

## Adding pages to the Table Of Contents

1. Once you have published a page you need to add it to the TOC. Open `_includes/table-of-contents.md` to edit it.
2. Using Markdown syntax add your new page to one of the lists.
3. Links must start with a preceeding slash.
4. You can create new sections within the TOC by adding an h6 tag (in Markdown this is done by prefixing the line with 6 hashes: `###### My Section Heading`