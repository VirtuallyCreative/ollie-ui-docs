---
title: Webpack Sourcemaps
weight: 4
template: docs
---

Now that we're bundling our code, there's another important tool that we need: Source maps. Once we start bundling, minifying, and transpiling our code, we create a new problem. Our code becomes an impossible-to-read mess when it's running in the browser.

The solution is to generate a sourcemap. Sourcemaps map the bundled, transpiled, and minified code back to the original source. This means that when we open our browser developer tools and try to inspect our code, we'll see the original ES6 source code that we used.

Now, the sourcemaps can be generated automatically as part of our build process. You might be wondering how minifying the code actually saves any bandwidth if we have to generate a big map back to the original source. The beauty of sourcemaps is they're only downloaded if you open the developer tools. So this way, your users won't even download the sourcemaps, but they'll be available for you in case an issue arises, in either your development environment or in production. So effectively, sourcemaps give you all the benefits of being able to read your original code, without any additional cost to regular users.

When we set up Webpack for development, we told Webpack to generate a sourcemap by specifying the `devtool` setting that you see here.

```javascript
devtool: 'inline-source-map',
```

There are many potential settings to consider, but I'm using inline sourcemap for Ollie-UI.