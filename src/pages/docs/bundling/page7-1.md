---
title: Webpack Configs
weight: 1
template: docs
---

Webpack will bundle all our assets up into a single file that runs in our target environment. For Ollie-UI, our target environment is the Web.

Ollie-UI uses multiple config files to set up Webpack for various web environment scenarios. Let's cover the Development environment first.

## webpack.config.env.js Pattern
Since we have Babel configured to transpile our code, we can write our Webpack config using ES6 features. Webpack is configured via a single object that we define here in a Webpack config.

- `webpack.config.dev.js`
- `webpack.config.prod.js`

The [Webpack docs go into great detail on the wide variety of options that you can configure](https://webpack.js.org/concepts/), but I'm showing a very simple setup for Ollie-UI.

Now, let's walk through each setting briefly to get a better understanding of what's going on under the hood.
As you can see, Webpack is configured by just exporting an object.

```javascript
import webpack from 'webpack';
import path from 'path';

module.exports = {
  mode: 'development',
  resolve: {
    extensions: ['*', '.js', '.jsx', '.json']
  },
  devtool: 'inline-source-map',
  entry: [
    path.resolve(__dirname, 'src/index')
  ],
  target: 'web',
  output: {
    path: path.resolve(__dirname, 'src'),
    publicPath: '/', // default for Development (localhost)
    filename: 'bundle.js'
  },
  // ...
};
```
I set the `devtool` to `inline-source-map`. There are a number of devtools to consider. The basic trade-off here is compilation speed versus quality. Higher quality sourcemap settings take longer to generate.

I'm setting noInfo to false. It means that Webpack will display a list of all the files that it's bundling. I typically turn off this data during production developments, since it adds a lot of noise to the command line.

Now, you can pass Webpack an array of entry points. And this is a good way to inject middleware for hot reloading. But I'm going to ignore hot reloading, just to keep things simple here. And just define our application's entry point as `src/index`. And I use the magic global `__dirname`, which is part of Node giving us a full path using the path package baked into Node.

And you can see, I use the same approach anywhere that I'm resolving paths within this file. And we're targeting the Web for this framework. But we could, of course, set this to Node if we were using Webpack to build an app running in Node. And that would change the way that Webpack bundles our code, so that Node could work with it instead of the browser. And there are other notable targets that you could include here, like Electron, which is useful for building desktop-style apps with JavaScript.

Now we need to define the output. Here, we tell Webpack where it should create our dev bundle. Now, this is confusing because as you'll see, with our development configuration, Webpack won't actually generate any physical files. It will just create a bundle and memory, and serve it to the browser. But we need to define the path and name, so it can simulate the physical file's existence. We'll use node's dirname variable to get the currently directory, and specify that our app will ultimately run from the source folder. But again, note that this won't actually write any files.

```javascript
  module: {
    rules: [
      {test: /\.js$/, exclude: /node_modules/, loader: 'babel-loader'},
      {test: /\.css$/, use: ['style-loader','css-loader']},
      // Handle images inside CSS files
      {test: /\.(png|jpg|gif)$/, use: ['file-loader']},
      // Handle custom fonts built using https://glyphter.com/
      {test: /\.(woff(2)?|ttf|eot|svg)(\?v=\d+\.\d+\.\d+)?$/,
                use: ['file-loader']
            }
    ]
  }
```

We need to tell Webpack the file types that we want it to handle. Webpack calls this concept loaders. Loaders teach Webpack how to handle different file types. As you can see, we want to handle JavaScript. The great thing about Webpack is, it can handle a lot more than just JavaScript, as you can see with the second loader. I've taught Webpack to handle CSS as well. I could add other loaders here to handle SASS, LESS, images, and more. So why teach Webpack to handle more than JavaScript? Well, adding a loader here means that I can import those file types at the top of my JavaScript files, and Webpack will intelligently bundle the files together for me.

It's also worth noting that there are various alternative syntaxes that work here. So other examples you see may look a little bit different.

I've come to really appreciate how terse Webpack's setup is. Ollie-UI declared many decisions in under 30 lines of code. Webpack is designed to cover our use case really well, which means we don't have to write much code to get a lot of power from our built process.