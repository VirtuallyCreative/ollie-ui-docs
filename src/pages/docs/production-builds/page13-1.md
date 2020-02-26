---
title: Minification & Sourcemaps
weight: 1
template: docs
---

Minification is about speeding page loads and saving bandwidth. A JavaScript minifier uses a number or tricks. It will shorten variable and function names, remove comments, remove whitespace, new lines, and more. The code still functions the same, but the resulting file size is much smaller, which helps speed page loads.

Minification basically removes all the things that only humans care about, and leaves all the things that computers need. And some of the newer bundlers like RollUp and Webpack4 go even further by eliminating unused code via a process that's commonly called tree-shaking.

And through the beauty of source maps, we can still debug our minified code.

### Sourcemaps
First changed item from Development is the `devtool` setting. Remember that this setting specifies how source maps should be generated. It's a little bit slower to build but it provides the highest quality sourcemap experience. This will assure that we can still see our original source code in the browser, even though it's been minified, transpiled, and bundled. That's the beauty of source maps.

```javascript
export default {
    mode: 'production',
    resolve: {
        extensions: ['*', '.js', '.jsx', '.json']
    },
    devtool: 'source-map',
```

### /dist Folder
Ollie-UI writes our production build to a folder called `dist`. When building the app for production, Ollie-UI writes physical files to a folder called `dist`. This is a popular convention and it stands for distribution.

```javascript
    output: {
        path: path.resolve(__dirname, 'dist'),
```

### Minification
We want to minify our code for production so let's add our first plugin to the array of plugins. Before we minify, let's use another handy webpack plugin that will eliminate any duplicate packages when generating the bundle. This plugin's called the Dedupe plugin. So this will look through all the files that we're bundling and make sure that no duplicates are bundled.

```javascript
    // Webpack 4 removed the commonsChunkPlugin.
    // Use optimization.splitChunks instead.
    optimization: {
        splitChunks: {
            cacheGroups: {
                commons: {
                    test: /[\\/]node_modules[\\/]/,
                    name: 'vendor',
                    chunks: 'all'
                }
            }
        }
    },
```
```javascript
    module: {
        rules: [
            {
                test: /\.js$/,
                exclude: /node_modules/, loader: 'babel-loader'
            },
            {
                test: /\.css$/i,
                use: [MiniCssExtractPlugin.loader, 'css-loader'],
            },
            {
                test: /\.(png|jpg|gif)$/,
                use: ['file-loader']
            },
            {
                test: /\.(woff(2)?|ttf|eot|svg)(\?v=\d+\.\d+\.\d+)?$/,
                use: ['file-loader']
            }
        ]
```