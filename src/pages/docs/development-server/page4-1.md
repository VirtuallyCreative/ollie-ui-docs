---
title: ExpressJS
weight: 1
template: docs
---

# ExpressJS

Ollie has a very minimal Express setup. Ollie keeps all build-related tools in a single folder called `build` in the root of the project.

Inside, `srcServer.js` which holds all the config information for the development server, `distServer.js` holds all the production build config options.

`srcServer.js` will configure a web server that will serve up the `index.ejs` in our `src` directory and sets the `localhost` port to `:3000`,

```javascript
// ...
const port = 3000
// ...
app.get('/', function mainHandler(req, res) {
    res.sendFile(path.join(__dirname, '../src/index.ejs'))
})
// ...
app.listen(port, function(err) {
    if (err) {
        console.log(err) // eslint-disable-line no-console

        // Rollbar.com Error Tracking, uncomment to enable
        // rollbar.critical("Critical Error Caught: ", err)
    } else {
        open('http://localhost:' + port)
    }
})
```
