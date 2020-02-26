---
title: NPM Default Scripts
excerpt: >-
  Listing of all the NPM Script Commands out of the box in Ollie-UI.
template: docs
---

# NPM Default Scripts

Out of the box, here are the pre-configured scripts in Ollie,

- prestart                :: Sets the starting message from `startMsg.js`
- start                   :: Previews the Site in default browser with linting & test watchers
- start-mockapi           :: Starts Mock API with Express
- open:src                :: Opens SRC folder assets in default browser
- lint                    :: Lints all HTML,CSS,JS
- lint:watch              :: Adds watch tag to Lint script for file changes
- localtunnel             :: lets you open remote pipe
- share                   :: creates URL for someone to preview site
- test                    :: runs mocha/chai tests
- test:watch              :: adds watch tag to mocha/chai tests for test changes
- generate-mock-data      :: runs json-schema-faker to fake data
- prestart-mockapi        :: generates mock data for API
- start-mockapi           :: starts json-server for development
- clean-dist              :: deletes /dist
- prebuild                :: cleans dist, runs tests and lints
- build                   :: runs main build using webpack production config creatiing assets for `/dist`
- postbuild               :: sets up production server settings for Express
- deploy                  :: deploys `/dist/` to [surge.sh](https://surge.sh)

And the actual `"scripts":{}` section in `package.json`,

```javascript
  "scripts": {
    "prestart": "babel-node build/startMsg.js",
    "start": "npm-run-all --parallel open:src lint:watch start-mockapi test:watch",
    "open:src": "babel-node build/srcServer.js",
    "lint": "esw webpack.config.* src build --color",
    "lint:watch": "npm run lint -- --watch",
    "localtunnel": "ngrok http 3000",
    "share": "npm-run-all --parallel open:src localtunnel",
    "test": "mocha --reporter progress build/testSetup.js \"src/**/*.test.js\"",
    "test:watch": "npm run test -- --watch",
    "generate-mock-data": "babel-node build/generateMockData",
    "prestart-mockapi": "npm run generate-mock-data",
    "start-mockapi": "json-server --watch src/api/db.json --port 3001",
    "clean-dist": "rimraf ./dist && mkdir dist",
    "prebuild": "npm-run-all clean-dist test lint",
    "build": "babel-node build/build.js",
    "postbuild": "babel-node build/distServer.js",
    "deploy": "surge ./dist"
  },
```
