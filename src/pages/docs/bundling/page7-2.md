---
title: Webpack /w ExpressJS
weight: 2
template: docs
---

We've configured Webpack, but to actually put it to use, we need to also set up our development server to serve our Webpack bundle. So we also configure Express to make that happen. To do so, we'll go over into the core folder and open `srcServer.js`, since this is where we configure Express.

```javascript
import express from 'express';
import path from 'path';
import open from 'open';
import webpack from 'webpack';
import config from '../webpack.config.dev';

/* eslint-disable no-console */

const port = 3000;
const app = express();
const compiler = webpack(config);

app.use(require('webpack-dev-middleware')(compiler, {
  noInfo: true,
  publicPath: config.output.publicPath
}));
app.use(express.static('public'))

app.get('/', function(req, res) {
  res.sendFile(path.join(__dirname, '../src/index.html'));
});

app.get('/users', function(req, res) {
  // Hard coding for simplicity. Ideally, "Pretend" this hits a real database
  res.json([
    {"id": 1,"name":"Alexander","website":"https://ollie-ui.dev","email":"alexander@virtuallycreative.ca"},
    {"id": 2,"name":"Alex","website":"https://ollie-ui.dev","email":"alexander.romano@live.com"},
    {"id": 3,"name":"Al","website":"https://ollie-ui.dev","email":"viperousmango@gmail.com"}
  ]);
});

app.get('/temp', function(req, res) {
  // Hard coding for simplicity. Ideally, "Pretend" this hits a real database
  res.json([
    {"amount": 12345,"goal":40}
  ]);
});

app.listen(port, function(err) {
  if (err) {
    console.log(err);
  } else {
    open('http://localhost:' + port);
  }
});
```

And first, I'll add two imports to the file. We will import Webpack, and we will import the Webpack config that we just created. Then down here, below where we have created an instance of express, let's call Webpack and pass it to config, that we referenced up here above. So now we have a reference to the Webpack compiler.

And we can put that to use down here on line 11. And what we'll do is call `app.use`, which is a way for us to tell Express other things we'd like to use. We're going to tell Express to use our Webpack dev middleware. And we'll pass it, the compiler, that we set up here on line 9. Inside of here, we'll define two options. Not to display any special info, and then also we'll configure our public path. So here, we're just referencing a variable that we defined when we set up our Webpack config. And that's all it takes for us to integrate Webpack with express.