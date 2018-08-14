# CSS Notes

Notes on reading [CSS: The Definitive Guide](http://amzn.eu/6m7B078)

## Chapter 1 - CSS and Documents
- `img`, `input` are _replaced_ elements; most are _nonreplaced_

### Display
- block elements: generate breaks before and after themselves; cannot appear within another element without disrupting it's display; `div`, `p`
- inline els do not generate breaks; `a`, `strong`, `em`
- in HTML, block elements cannot descend from inline elements
- list items are special cases of block elements - they generate the markers

### Stylesheets
- `link` els can have the `rel` attribute as `alternate stylesheet`
- alternate stylesheets should have a `title` attribute too; are grouped by title
- if given a title, a stylesheet is considered "preffered"; once an alt stylesheet is selected, it is not used at all
- alternate stylesheets supported by Gecko-based browsers, like Firefox
- can use media with `import`: `@import url(sheet1.css) projection, screen`
- can link stylesheets with the `Link` header; config is web-server dependend; FF/Opera

### CSS Rule Structure
- `<selector>: { <property>: <value>; }`
- each `<property>: <value>;` tuple constitutes a "declaration"
- in general, CSS is whitespace-insensitive
- comments are removed before parsing; do not count on them for whitespace

### Media Queries
- `media` attr of `link` element
- `media` attr of a `style` element
- `media` descriptor portion of an `@import` statement
- `media` descriptor portion of a @media declaration
- `<link href="a.css" media="print and (color), screen and (color-depth: 8)" rel="stylesheet" />`
- `@import url(print-color.css) print and (color), screen and (color-depth: 8);
- in the two exaples above, if _any_ of the queries evaluates to true, the stylesheet is applied
- can use `and` and `not`, but `not` can only be used in the begginning of a query
- `@import url(foo.css) only all` - not applied by browsers which do not understand MQ; applied otherwise
- the commas separating queries are acting as `or` statements
- all descriptors: https://www.w3.org/Style/CSS/all-descriptors.en.html
- `@supports (display: grid) { ... }` - applies if what is between parens is understood/supported
- `@supports not (display: grid)` - apply rules when something is _not_ understood
- `@supports (shape-outside: circle()) or (-webkit-shape-outside: circle()) { ... }`

## Chapter 12 - Flexible Box Layout
- can alter order; but screen readers still read in source order (for now, at least)
- flex containers can be block or inline
- `display: flex` == `display: flex block`
- `display: flex inline` == `display: inline-flex`
- **only immediage children are _flexed_**
- flexbox is intended for single-dimensional content distribution, not grid-like layouts
- by default, non-fitting items don't wrap; they shrink if allowed by `flex` prop, and/or overflow
- `flex-wrap` - controls whether the flex container is limited to being single-line
