---
title: Linting CSS, HTML & JS
excerpt: >-
Learn how Ollie-UI uses ESLint to provide powerful feedback during
the development process.
template: docs
---

Today's linters are so powerful that they can catch many errors at compile time. It's wonderful finding out that you
made a mistake the moment you hit Save, rather than waiting until run time to hunt some cryptic issue down.

## Why Lint?
So, why do you need a linter? I see two core reasons. First, a linter programmatically enforces consistency. Once you've
chosen JavaScript coding standards as a team, a linter can help enforce those programmatically and provide rapid
feedback so issues are caught during development instead of potentially slipping by during code reviews.

Examples include enforcing the position of curly braces or warning about the use of built-in features that your team has
decided to avoid, like confirm and alert. Many teams prefer to use nicely styled dialogue boxes instead of the native
implementations of these features. Linting helps programmatically restrict their usage. Or leaving in a trailing comma,
or forgetting to add a trailing comma if your team prefers trailing commas as a standard. Or declaring a global
variable, or disallowing the use of eval since it's potentially dangerous and often misused. All of these are examples
of enforcing consistency through a linter.

Second, a linter helps avoid mistakes. Just consider the long list of potential mistakes that you can make writing
JavaScript today. Such as adding an extra parenthesis when wrapping a statement. Or overwriting a function when you
don't realize that the function with the same name already exists. How about performing an assignment in a conditional
when you almost certainly meant to perform a comparison instead? It's really easy to leave out that extra equals sign.
Or forgetting to define a default case in a switch statement, which can lead to hard-to-debug fall through issues. How
about leaving debugging-related junk in your code, like debugger or console.log? It's easy to accidentally leave these
in and have them slip into production. With a linter, you'll know immediately when you do, and you can even fail to
build on your continuous integration server when a developer overlooks warnings and commits any of these issues. This
list just scratches the surface.

## Linters
JSLint was the original, created by Douglas Crockford many years ago. It's extremely opinionated, and while some may
consider that a feature, the public has largely moved on to more powerful and configurable alternatives today. One such
alternative is JSHint. JSHint is an improvement on JSLint which offers more configurability.

But in recent years, the most popular linter **by far** has become ESLint. In fact, it's become so powerful and
configurable that ESLint has become the de facto standard.