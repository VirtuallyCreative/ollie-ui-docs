---
title: Editors & Configs
excerpt: >-
  Ollie-UI relies heavily on ESLint to help maintain standards. Learn more
  about the default configuration.
template: docs
---

# Editors & Configurations

To get things started, Ollie makes no assumption about what Javascript editor you prefer but does assume that
everyone on your team uses the same critical editor settings, like spaces versus tabs, line endings, and more, by using a standard called editorconfig.

If not then Ollie's default standards can be the base-line to help guide you or your team on what you would want to be the standards for everyone.

## What Ollie needs in a JavaScript Editor

Regardless of what platform/software IDE or editor you develop with if you're looking to develop modern Javascript applications your tools should support modern features too.

**Your IDE or editor should offer strong support for the latest JavaScript features.**

Most editors do so today, but keep in mind that the larger your editor is, the slower it will typically be to add support for new JavaScript features, and it's also likely to be slower to add support for alternative languages that transpile to JavaScript in the future.

Now when we talk about strong ES2015+ support, you should look for things like this: Does it index your JavaScript file so that it can intelligently provide autocompletion?
Does it parse ES6 imports?
Since ES6 imports are statically analyzable, strong JS
editors can report unused imports as well as typos and import statements.
Does it offer automated refactoring tools like rename and extract function?
Again, since ES6 imports are now statically analyzable, such refactoring can finally be handled in a safe and automated way. This is a great win that you get for free if you use a modern JS oriented editor.

Many editors now offer built-in support for popular frameworks and libraries like Node, React, and Angular.

For instance, WebStorm and VSCode both offer built-in node debugging, and WebStorm even recently added support for React proptype autocompletion.

Many more examples like this exist.

Finally, this is arguably the most important for using Ollie: *a built-in terminal*.

All the tools Ollie uses are Node based, and they rely on the command line. Having a terminal built-in gives you a single window with everything you need to know about the current status of your application. It's handy having one spot to check for any linting errors, broken tests, build status, code coverage, and more.
