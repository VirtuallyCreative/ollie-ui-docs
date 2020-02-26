---
title: JS goes in .js
weight: 2
template: docs
---

Ollie-UI follows some opinions on how a developer approaches development in the Virtually(Creative) technical stack.

When matters of front-end are conserned some best-pratice mantras have formed over several years forged from the JIRA fires and battle scars of many things broken and fixed again.

With these learnings, some things are baked-in to Ollie-UI and should guide how developers expand upon the starter-kit provided for a safe, and easy breasy development journey.

# Mantra: JavaScript belongs in a. js file.

Writing JavaScript inline within an html file should be avoided;
Use the EJS and config files to properly set tracking scripts/snippts.

Ollie-UI is a dynamic JavaScript development environment that can bring all the benefits even to small, simple snippits when inserted properly.

If you wrote logic snippits inline, how do I write automated tests for this?
How do I link this code?
How do I reuse this?
Now what if I want to use ES6, typescript, or some alternative language that transpiles the JavaScript?
What if I want to be explicit about my code's dependencies by using ES6's import keyword?

The answer to all of these questions is, you can't. By putting your code inline with an html, you're losing all of this power. Please don't do it.

# Mantra: Use Configuration Object Pattern (C.O.P.) whenever possible.

Inject JSON from the server into your application.

How webpack's `.config.js` files are setup so that you can 'feed' them to the application is a great example to parallel when talking about a way to extract DB from a database in a straightforward way from back-end to front-end.

# Mantra: Avoid dynamically generating JavaScript code.
Instead, dynamically generate some data that your JavaScript code can use. Not the code itself.