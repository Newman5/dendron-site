---
id: ba97866b-889f-4ac6-86e7-bb2d97f6e376
title: Markdown
desc: ''
updated: 1609605890636
created: 1598673110284
---

# Markdown

- Notice: all references of `MPE` in this guide is in reference to `Dendron Markdown Preview Enhanced`, the default markdown renderer of Dendron

## Markdown Basics

This article is a brief introduction to [GitHub Flavored Markdown writing](https://guides.github.com/features/mastering-markdown/).

## What is Markdown?

`Markdown` is a way to style text on the web. You control the display of the document; formatting words as bold or italic, adding images, and creating lists are just a few of the things we can do with Markdown. Mostly, Markdown is just regular text with a few non-alphabetic characters thrown in, like `#` or `*`.

## Syntax guide

### Headers

```markdown
# This is an <h1> tag

## This is an <h2> tag

### This is an <h3> tag

#### This is an <h4> tag

##### This is an <h5> tag

###### This is an <h6> tag
```

If you want to add `id` and `class` to the header, then simply append `{#id .class1 .class2}`. For example:

```markdown
# This heading has 1 id {#my_id}

# This heading has 2 classes {.class1 .class2}
```

> This is a MPE extended feature.

### Emphasis

<!-- prettier-ignore -->
```markdown
*This text will be italic*
_This will also be italic_

**This text will be bold**
__This will also be bold__

_You **can** combine them_

~~This text will be strikethrough~~
```

### Lists

#### Unordered List

```markdown
- Item 1
- Item 2
  - Item 2a
  - Item 2b
```

#### Ordered List

```markdown
1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b
```

#### Definition List

```markdown
Item 1
: Definition for Item 1

Item 2
~ Definition for Item 2
~ Another definition for Item 2, with a [link](http://www.example.com)
```

### Images

```markdown
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)
```

### Links

```markdown
https://github.com - automatic!
[GitHub](https://github.com)
```

### Blockquote

```markdown
As Kanye West said:

> We're living the future so
> the present is our past.
```

### Horizontal Rule

```markdown
Three or more...

---

Hyphens

---

Asterisks

---

Underscores
```

### Inline code

```markdown
I think you should use an
`<addr>` element here instead.
```

### Fenced code block

You can create fenced code blocks by placing triple backticks <code>\`\`\`</code> before and after the code block.

#### Syntax Highlighting

You can add an optional language identifier to enable syntax highlighting in your fenced code block.

For example, to syntax highlight Ruby code:

    ```ruby
    require 'redcarpet'
    markdown = Redcarpet.new("Hello World!")
    puts markdown.to_html
    ```

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```
### Task lists

```markdown
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
```

### Tables

You can create tables by assembling a list of words and dividing them with hyphens `-` (for the first row), and then separating each column with a pipe `|`:

<!-- prettier-ignore -->
```markdown
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
```

You can create a table from existing content using `> Markdown Shortcuts: Add Table` command.

![](https://raw.githubusercontent.com/mdickin/vscode-markdown-shortcuts/master/media/demo/table_with_header.gif)

### Abbreviation


The HTML specification

```markdown
_[HTML]: Hyper Text Markup Language
_[W3C]: World Wide Web Consortium
The HTML specification
is maintained by the W3C.
```
<!-- 
## Extended syntax

### Table

> Need to enable `enableExtendedTableSyntax` in extension settings to get it work.

![screen shot 2017-07-15 at 8 16 45 pm](https://user-images.githubusercontent.com/1908863/28243710-945e3004-699a-11e7-9a5f-d74f6c944c3b.png)

### Emoji & Font-Awesome

> This only works for `markdown-it parser` but not `pandoc parser`.  
> Enabled by default. You can disable it from the package settings.

```
:smile:
:fa-car:
```

### Superscript

```markdown
30^th^
```

### Subscript

```markdown
H~2~O
```

### Footnotes

```markdown
Content [^1]

[^1]: Hi! This is a footnote
```

### Mark

```markdown
==marked==
```

### CriticMarkup

CriticMarkup is **disabled** by default, but you can enable it from the package settings.  

There are five types of Critic marks:

- Addition `{++ ++}`
- Deletion `{-- --}`
- Substitution `{~~ ~> ~~}`
- Comment `{>> <<}`
- Highlight `{== ==}{>> <<}`

> CriticMarkup only works with the markdown-it parser, but not the pandoc parser.
-->

## VSCode Specific Commands

### Markdown Smart Select

This allows you to expand and shrink selections of markdown using a keyboard shortcut.
* Expand: ⌃⇧⌘→
* Shrink: ⌃⇧⌘←

Selection applies to the following, and follows a traditional hierarchical pattern:
* Headers
* Lists
* Block quotes
* Fenced code blocks
* Html code blocks
* Paragraphs

![preview](https://code.visualstudio.com/assets/updates/1_51/markdown-smart-select-demo.gif)
> Image by Microsoft

## Compatibility with CommonMark

[CommonMark](https://commonmark.org/) is *a strongly defined, highly compatible specification of Markdown*

When possible, Dendron will try to stay to `CommonMark` spec for syntax. That being said, many of the features we have (eg. block based note references) have no common mark equivalent which is why we've had to invent new syntax.

You can use the [[markdown pod|dendron.topic.pod.builtin.markdown]] to migrate both individual notes and your entire vault to a CommonMark compatible format.

## Other Resources

- [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)
- [Daring Fireball: Markdown Basics](https://daringfireball.net/projects/markdown/basics)
- [Markdown Guide](https://www.markdownguide.org/)

## References

The content of this page is derived from the following sources:

1. [markdown preview enhanced docs](https://shd101wyy.github.io/markdown-preview-enhanced/#/markdown-basics) published under the [University of Illinois/NCSA Open Source License](https://github.com/shd101wyy/markdown-preview-enhanced/blob/master/LICENSE.md)
2. [markdown shortcuts docs](https://marketplace.visualstudio.com/items?itemName=mdickin.markdown-shortcuts) published under the [MIT License](https://marketplace.visualstudio.com/items/mdickin.markdown-shortcuts/license)


