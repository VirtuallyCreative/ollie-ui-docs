---
title: Webpack /w CSS
weight: 3
template: docs
---

Have Webpack handle CSS by defining a CSS loader in our Webpack config.

```javascript
// ... import MiniCSS
import MiniCssExtractPlugin from "mini-css-extract-plugin";

export default {
    // ...
    plugins: [
        // ... setup MiniCSS
        new MiniCssExtractPlugin({
            // Options similar to the same options in webpackOptions.output
            // both options are optional
            filename: '[name].css',
        })
    ],
    module: {
        rules: [
            // .. setup the Rule
            {
                test: /\.css$/i,
                use: [MiniCssExtractPlugin.loader, 'css-loader'],
            },
            // ..
        ]
    }
}
```

Now, since we taught Webpack how to handle CSS, now all we have to do to put this to use is add a single line in our application's entry point, which is `index.js`. The order in which you import your CSS is important as that's the order they're bundled. Just like I would import a JavaScript file, I can import a CSS file. Looks pretty weird... thanks Webpack.

```javascript
// index.js

// Import CSS
import './index.css';
```

How did that work? Well, behind the scenes, Webpack parsed our style sheets. And then it used JavaScript to inject the style sheets onto the page.

If we pull up `bundle.js` in web inspector, you can find the style sheets right in here. You can see that our style sheets are bundled into our JavaScript, and then is being injected onto the page. Now, we could use a similar approach to handle SASS, LESS, images, and more if we need to.

Of course, for production, you'll likely want to generate a traditional separate file. And that is handled in the production build configuration.