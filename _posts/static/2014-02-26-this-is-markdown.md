---
published: true
layout: page
title: This is Markdown
permalink: this-is-markdown/
---

This page demonstrates some of [Markdown][1]'s capabilities.

---

## Basic formatting

This is a paragraph, it forms the basic structure of a Markdown document. This is some Lorem Ipsum text to pad out the paragraph a bit more. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc vestibulum ornare erat vitae bibendum. Integer porttitor purus nec justo faucibus pulvinar. Nulla ultrices lectus et viverra imperdiet.

Paragraphs are separated by a blank line. Basic formatting of *italics* and **bold** is supported.

---

## Lists

### Ordered list

1. Item 1
2. A second item
3. Number 3
4. Ⅳ

*Note: the fourth item uses the Unicode character for [Roman numeral four][2].*

### Unordered list

* An item
* Another item
* Yet another item
* And there's more...

---

## Paragraph modifiers

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

### Quote

> This is a blockquote. Quotes are automatically indented when they are used. They can also contain **bold** text and [links to other things][6].

---

## Headings

There are six levels of headings. They correspond with the six levels of HTML headings. You've probably noticed them already in the page. Each level down uses one more # (hash) character.

# h1. Heading
## h2. Heading
### h3. Heading
#### h4. Heading
##### h5. Heading
###### h6. Heading    

Also...

### Headings can contain formatting such as *italicised* text

### They can even contain `inline code`

---

## URLs

URLs can be made in a handful of ways:

* A named link to [GPMD][3]
* Another named link to [GPMD](http://www.gpmd.co.uk/)
* Sometimes you just want a URL like <http://www.gpmd.co.uk/>

---

## Horizontal rule

A horizontal rule is a line that goes across the middle of the page. It's sometimes handy for breaking up blocks of content.

---

## Images

Markdown can also contain images.

![Mark](/assets/uploads/mark.jpg)

*This is the lovely Mark, our Managing Director*

---

## Finally

There's actually a lot more to Markdown than this. See the official [introduction][4] and [syntax][5] for more information.

[1]: http://daringfireball.net/projects/markdown/
[2]: http://www.fileformat.info/info/unicode/char/2163/index.htm
[3]: http://www.gpmd.co.uk/
[4]: http://daringfireball.net/projects/markdown/basics
[5]: http://daringfireball.net/projects/markdown/syntax
[6]: http://www.gpmd.co.uk/