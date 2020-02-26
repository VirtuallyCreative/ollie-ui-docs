---
title: Selective Pollyfilling
weight: 3
template: docs
---

Now you might be wondering if Fetch is already supported natively in some browsers, why are we sending our polyfill down to all browsers?

Well in short, we did so because it was easy and it's also quite common. The idea is that you can remove the polyfill altogether later when all the browsers that you care about have added support for Fetch.

But if you want to send a polyfill only to browsers that need it, there's a handy service called [Polyfill.io](http://polyfill.io/) which does just that, it offers a wide array of polyfills.

Here's an example of using [polyfill.io](http://polyfill.io/) to polyfill only the Fetch feature, so if we put this at the top of index.html, [Polyfill.io](http://polyfill.io/) will read the user agent and use that information to determine if the browser requires a polyfill for the feature or features listed. Since I'm using Chrome it will send back an empty response since my browser doesn't need it, pretty slick.

```html
<script crossorigin="anonymous" src="https://polyfill.io/v3/polyfill.min.js?features=fetch"></script>
```