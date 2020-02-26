---
title: Asset Bundling
excerpt: >-
  Breakdown of the Webpack Configs in play for bundling all assets together in Ollie-UI.
template: docs
---

## What is Bundling?
These days, when you write JavaScript, it likely needs to be bundled up for usage. As a JavaScript developer, it's important to understand that NPM packages use the commonJS pattern traditionally. Node can handle this just fine, but browsers don't understand it. So you need to bundle NPM packages into a format that the browser can consume. But bundlers aren't just for apps that run in the browser. You may use a bundler to package any JavaScript into a single file. Or strategically into separate files, for different portions of your app. Imagine you've created an app with five separate pages. A powerful bundler can intelligently create separate bundles of JavaScript for each page. That way, the user only has to download the relevant JavaScript for the first page on initial load. This saves bandwidth and speeds page loads. Finally, remember that bundlers aren't just for the Web. You may want to use bundlers if you're coding in Node as well, since Node's require is slow. But bundling your code for Node, you can compile away the require calls, which can often improve performance.

## Module Formats
If you've been coding in JavaScript for long, you're probably not surprised that there are currently not less than five different module formats out there to choose from. That sounds overwhelming, but as you'll see in a moment, there's arguably only one option that makes sense for new development today.

The five common module formats include,

- Immediately-Invoked Function Expressions, also known as IIFEs .
- Asynchronous Module Definition, also known as AMD.
- CommonJS, which was popularized by Node.
- The Universal Module Definition, which blends AMD with CommonJS.
- And finally, the ES6 module format.

If you're working in Node, you can continue to use CommonJS. But if you're working in ES6, or in newer versions of JavaScript, you can finally enjoy the power of ES6 modules. Yes, we finally have a standards-based way of encapsulating our code. And for future application development, we should choose ES6 modules.

## Why ES6 Modules?
ES6 modules are also known as ES2015 modules since ES2015 was the official name of the 2015 release, which released this feature. Now as we discussed in a previous, all future JavaScript versions will be named after the year of their release. So anyway, why should we choose ES6 modules? Well first, they're standardized. This means in the future, when the platforms you run on have full support for ES6 and modules, you won't have to transpile your code. It also means anyone joining your team is more likely to feel comfortable with your code.

ES6 modules are also a win because you can't declare them dynamically. Now that sounds like a drawback because it reduces power, but this reduced power was a deliberate design decision because it makes our code statically analyzable. That's a fancy way of saying that it means that our code can be read and analyzed in a predictable way because the behaviour of our imports can't be changed at runtime. When code can be analyzed this way, we get benefits that I alluded to earlier when discussing editors. We get improved autocompletion support since your editor can determine clearly what functions are currently in scope from each imported module. This power leads to other wins, such as the ability to quickly alert you to invalid imports, to functions that don't exist, and so on.

Effectively, choosing ES6 modules means that your code fails fast. You find out about your mistakes more quickly, and often in a clearer manner.

ES6 imports also enable tree shaking, also known as dead code elimination. In short, this feature reduces the size of your final production code by eliminating unused code. And for tree shaking to work, we need statically analyzable code, which is exactly what we get with ES6 modules. ES6 modules are also easier to read than the more redundant alternatives, like AMD and UMD. And you can further clean up your code using named imports. Named imports allow you to easily declare variables that reference pieces of the file that you're importing. And default exports, which specify clearly how others can consume your module. Bottom line, although there are many ways to handle modules in JavaScript, if you're writing new code today, ES6 modules are the clear, logical, and attractive way to get things done. So ES6 modules are the format that I'll be using to modularize our code through the rest of the course.

## Why Webpack?
Now that we've picked a module format, our next decision is to select a bundler. Bundlers take all your JavaScript files and intelligently package them for a target environment, such as a browser or node. And as you'll see, some add a variety of additional features on top of that.

The first bundler to reach mass adoption was RequireJS. RequireJS popularized the AMD pattern, also known as Asynchronous Module Definition, that we saw on a previous slide. However, since we're moving on to ES6 modules today, RequireJS has largely fallen out of favour. So let's shift our focus to more modern bundlers that we should be considering today.

Webpack is interesting because it can handle much more than just JavaScript. Webpack offers a huge ecosystem of loaders, so you can easily teach Webpack to intelligently handle your CSS, images, fonts, and more. With Webpack, you can import all these file types just like you do JavaScript. And it can intelligently bundle your application accordingly. Webpack's even smart enough to inline images in styles if they're small enough to justify saving an HKP request. And as we saw earlier in the development web server module, Webpack includes a built-in hot reloading Web server. Webpack serves files from memory, which speeds development, builds, and automatically updates client-side state to reflect code changes. And not just JavaScript, but also your styles, images, and HTML.

Webpack is the most full-featured and powerful of the bunch, so Webpack's what Ollie-UI uses.

What really makes Webpack special is its ability to intelligently bundle and generate your CSS, images, fonts, and even your HTML. This means you can do things like inline images via Base64 encoding when they're small enough to justify saving an HTTP request. And it means you can hot reload your CSS changes in memory, via the built-in Web server. Webpack offers strategic bundle splitting. This helps avoid your users downloading all of your JS upfront. Instead, you can generate separate bundles for different sections of your app, so they're downloaded on demand.

Webpack also includes a built-in Web server that supports hot module reloading. Which means depending on the library or framework you're using, you may be able to hit save and immediately see the changes without having to do a full refresh. This helps speed development because you don't lose client-side state. This is especially helpful on complicated user interfaces and multi-step forms because you don't have to refill the form every time to test your changes. The code is hot reloaded in place, and your existing input field values and so on are maintained.
