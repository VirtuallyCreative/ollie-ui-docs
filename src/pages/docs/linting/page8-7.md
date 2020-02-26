---
title: ESLint Config - Watching Files
weight: 7
template: docs
---

Ollie-UI uses ESLint to check your JS code and run Babel to compile down ES6/7/8/9 syntax down to ES2015 and below for
better legacy compatibility.

ESLint doesn't currently include a watch setting built-in so if you want to automatically run ESLint each time that you
hit Save running ESLint by itself won't work.

Here are two ways to get around ESLint's lack of file watching capability. Fist, since we're using webpack, one option
is to use eslint-loader so webpack will run ESLint each time we run our build. The advantage of this approach is all
files being bundled by webpack are re-linted every time that you hit Save.

So, you see an ongoing summary of any linting issues. However, I recommend going a different route using an npm package
called eslint-watch. This npm package is simply a wrapper around ESLint that adds file watching capability. So, this
stands alone and isn't tied to webpack in any way so you can use this approach to linting regardless of the bundler that
you choose. eslint-watch also adds some other nice tweaks like better looking warnings and error messaging and it
displays a message when linting comes back clean unlike eslint-loader, which is completely silent when there are no
linting issues. But, finally, the biggest win with this approach is that you can easily lint all your files even if
they're not being bundled as part of your app. So, this means you can lint your tests, webpack config, and any build
scripts as well. I really like this so that I can ensure that all the code in my project is held to the same standard
and has a consistent style.