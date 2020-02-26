---
title: CI on Windows - Appvayor
weight: 2
template: docs
---

Appveyor supports a number of different online repositories, but we're going to look at Azure DevOps.

Now Appveyor is configured with a file called appveyor.yml and it should again reside out in the root of your project.

The recommended Appveyor configuration is a little more involved.

```yml
# Test against this version of Node.js
environment:
  matrix:
  # node.js
  - nodejs_version: "10"

# Install scripts (runs after repo cloning)
install:
  # Get the latest stable version of node.js or io.js
  - ps: Install-Product node $env:nodejs_version
  # install modules
  - npm install

# Post-Install test scripts.
test_script:
  # Output useful info for debugging
  - node --version
  - npm --version
  # run tests
  - npm test

# Don't actually build
build: off
```

As you can see, we're telling Appveyor that we should be using `node.js` version 6. We could add other versions here below with another dash if desired, and the rest of this boilerplate is recommended by Appveyor so that we can declare that we want to install our npm packages and also run our tests.

We're telling it the specific npm tasks that it should run. And this output is just here because it's useful to see the Node and npm version that is being run when we're trying to debug.