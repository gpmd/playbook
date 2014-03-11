---
layout: page
published: true
title: Markdown Demo
permalink: "markdown-demo/"
---

This page demonstrates some of [Markdown][1]'s capabilities. It's worth pointing out that you can also use regular [HTML](http://developers.whatwg.org/) in your markdown document.

---

## Basic formatting

This is a paragraph, it forms the basic structure of a Markdown document. This is some Lorem Ipsum text to pad out the paragraph a bit more. Lorem ipsum dolor sit amet, consectetur adipiscing elit.

Paragraphs are separated by a blank line. Basic formatting of *italics* and **bold** is supported.

---

## Lists

### Ordered list

1. Item 1
2. A second item
3. Number 3
4. Ⅳ

*<strong>NOTE:</strong> the fourth item uses the Unicode character for [Roman numeral four][2].*

### Unordered list

* An item
* Another item
* Yet another item
* And there's more...

---

## Paragraph modifiers

### Quote

> This is a blockquote. Quotes are automatically indented when they are used. They can also contain **bold** text and even [links to other things][6].

---

## Headings

There are six levels of headings. They correspond with the six levels of HTML headings. You've probably noticed them already on this page.

# h1. Heading
## h2. Heading
### h3. Heading
#### h4. Heading
##### h5. Heading
###### h6. Heading

You can also add 'subheading' styling, but you will need to use HTML rather than markdown:

<h1>h1. Heading<br>
<span class="sub-heading">h1. Subheading</span></h1>

And here's the code for that:

```html
<h1>h1. Heading<br>
<span class="sub-heading">h1. Subheading</span></h1>
```

---

## Links

Links can be made in a handful of ways:

* A named link to [GPMD][3]
* Another named link to [GPMD](http://www.gpmd.co.uk/)
* Sometimes you just want a URL like <http://www.gpmd.co.uk/>

---

### Code block

```javascript
(function($) {
    $.fn.helloWorld = function() {
        this.each( function() {
            $(this).text("Hello, World!");
        });
    }
}(jQuery));
```

You can also make `inline code` to add code into other things.

---

## Horizontal rule

A horizontal rule is a line that goes across the middle of the page. It's sometimes handy for breaking up blocks of content.

---

## Images

Markdown can also contain images.

![Mark]({{ site.baseurl }}/assets/uploads/mark.jpg)

*This is the lovely Mark, our Managing Director*

You can do nice things with images, such as 'outset' them, but in order to do so you need to embed the image using regular HTML, like so:

<figure class="outset--center">
	<img src="{{ site.baseurl }}/assets/uploads/rainbow.jpg" alt="Rainbow">
	<figcaption>Up above the streets and houses, rainbow flying high...</figcaption>
</figure>

*<strong>Note:</strong> on smaller devices the outset is removed.*

Here's the markup (yes, we're using the [HTML5 figure element](http://developers.whatwg.org/grouping-content.html#the-figure-element)):

```html
<figure class="outset--center">
	<img src="{{ site.baseurl }}/assets/uploads/rainbow.jpg" alt="Rainbow">
	<figcaption>Up above the streets and houses, rainbow flying high...</figcaption>
</figure>
```

The 'outset' classes available are `outset--right`, `outset--center` and `outset--left`.

---

## Finally

There's actually a lot more to Markdown than this. See the official [introduction][4] and [syntax][5] for more information.

[1]: http://daringfireball.net/projects/markdown/
[2]: http://www.fileformat.info/info/unicode/char/2163/index.htm
[3]: http://www.gpmd.co.uk/
[4]: http://daringfireball.net/projects/markdown/basics
[5]: http://daringfireball.net/projects/markdown/syntax
[6]: http://www.gpmd.co.uk/