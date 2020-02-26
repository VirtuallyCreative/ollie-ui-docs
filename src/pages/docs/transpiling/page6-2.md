---
title: Transpiling Build Scripts
weight: 2
template: docs
---

Another tough decision is whether to transpile your build scripts or to continue using ES5 and Node's commonJS style for your build scripts. ES5 is the most efficient approach since transpiling does slightly slow down your build scripts. And it also helps avoid depending on a transpiler at all.

But of course, using ES6 or newer is attractive because we can enjoy all of JavaScript's latest features. And this also means that all the code in our project uses the same style. This makes it easier to read and understand and avoids confusing people with intermixing ES5 and common JS in our build scripts with ES6 or newer code and module import styles in the rest of our application. Transpiling our build scripts also means that we can use the same linting rules everywhere.

And finally, as Node's modern JavaScript support improves, depending on the features that we use, we can eventually remove the need for transpiling altogether.

Ollie-UI transpiles the build scripts as well so that developers can enjoy modern JavaScript when writing our build tooling.