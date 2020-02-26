---
title: Ecosystem
excerpt: >-
  To make it easy to write documentation in plain Markdown, most UI components
  are styled using Markdown elements with few additional CSS classes.
template: docs
---

# Ecosystem

Ollie is a rapid SPA starter kit meaning it makes little assumptions about what front-end stack you're going to use with it.

Out of the box, Ollie contains a micro CSS framework also made by Virtually(Creative) called, [Allegretto](https://allegretto.herokuapp.com).

This light-weight framework helps with making simple layouts with easy to pick-up selectors, helpers and utility classes.

- Fast and lively (~9kb gziped). With Unpkg CDN goodness.
- Build with Accessability in mind; A.O.D.A / W.C.A.G.
- Great for quick wireframing/prototyping
- Simple 12-Col grid using flexbox
- Easy to extend with your own CSS variables
- Comes with a handful of components & utils
- Expects proper HTML5 semantic markup
- Normalize CSS reset baked in
- No Pre-Processer here, just vanilla CSS-3

But, you can easily swap it out for whatever front-end framework you wish - a few favourites at Virtually(Creative) are listed below!

## Allegretto CSS

To replace it, swap the Allegretto reference in the `<head>` tag in `/src/index.ejs`.

```html
  <!-- Load Allegretto from CDN -->
  <link rel="stylesheet" href="https://unpkg.com/allegretto@latest/dist/retto.min.css" type="text/css" media="all">
```

| Project | Status | Description |
|---------|--------|-------------|
| [Allegretto](https://github.com/VirtuallyCreative/allegretto)          | [![Build Status](https://travis-ci.org/VirtuallyCreative/allegretto.svg?branch=master)](https://travis-ci.org/VirtuallyCreative/allegretto) | Lightweight CSS Framework |

## Other Frameworks

Ollie also plays well with (in no particular order...),

- [Bulma](https://bulma.io/documentation/overview/start/)
- [Bootstrap](https://getbootstrap.com/docs/4.3/getting-started/introduction/)
- [Tachyons](http://tachyons.io/#getting-started)
- [Foundation](https://foundation.zurb.com/develop/getting-started.html)
- [PureCSS](https://purecss.io/start/)
- [Teutonic](https://teutonic.co/usage)
- [Mustard UI](https://mustard-ui.com)

Follow their getting started instructions and replace the Allegretto reference with the framework you wish.
