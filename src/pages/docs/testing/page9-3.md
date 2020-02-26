---
title: Helper Libs
weight: 3
template: docs
---

There's another question to answer before we start writing tests.

Should we use a helper library? And if so, which one?

JSDOM is an implementation of the browser's DOM that you can run in Node.js.

So with JSDOM, we can run tests that rely on the DOM without opening an actual browser. This keeps your testing configuration for automated tests simpler and often means that tests run faster because they're not reliant on running in the browser. JSDOM is useful when you want to write tests that involve HTML and interactions in the browser using Node.