---
title: NPM Scripts
weight: 1
template: docs
---

## NPM Scripts

Expanding on the the pre-made scripts in Ollie should be pretty straightforward. Ideally to add more features along with your app you can
add on, extend or duplicate scripts to help organize as your project grows.

And the actual `"scripts":{}` section in `package.json`,

```javascript
  "scripts": {
    "prestart": "babel-node build/startMsg.js",
    "start": "npm-run-all --parallel open:src lint:watch start-mockapi test:watch",
    "open:src": "babel-node build/srcServer.js",
    "lint": "esw webpack.config.* src build --color",
    "lint:watch": "npm run lint -- --watch",
    "localtunnel": "lt --port 3000",
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
