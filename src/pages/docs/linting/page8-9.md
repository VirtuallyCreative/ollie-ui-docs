---
title: ESLint Config - Automated Builds
weight: 9
template: docs
---

Now, as we've been talking through this process you might be wondering why we should be bothering to lint via an
automated build process, because many editors offer ESLint integration built-in, so they just monitor your code and
output results inline right there within the editor.

However, I prefer to integrate ESLint with my build process for multiple reasons: First, outputting all feedback on my
code to the command line gives me one single place to check for all the feedback related to my code quality. This means
I have one place to check not just for linting issues but also for any compile time errors or any testing errors. This
is especially helpful on teams where developers all use different editors. We all have the same development work flow
because we all utilize the same starter kit and a command line.

Pair programming is also easier when everyone has the same development process, and most importantly, ESLint should be
part of your build process so that the build is broken on your continuous integration server when someone commits any
code that throws a linting error. This helps protect your application from slowly getting sloppy. Even if a developer
ignores ESLint locally the build can be rejected automatically by your continuous integration server.