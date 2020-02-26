---
title: Babel Config
weight: 1
template: docs
---

Babel offers two methods for configuration. A `.babelrc` file and within `package.json`.
The most common approach is to use a dedicated `.babelrc` configuration file and that is what Ollie-UI includes.

```json
{
  "presets": [
    [
      "@babel/preset-env",
      {
        "targets": {
          "esmodules": true
        }
      }
    ]
  ]
}
```

This configuration file should be placed in your project's root. The advantage of using the `.babelrc` configuration file is it's not NPM specific. So even if you're working on a project that doesn't use NPM, you can configure Babel using a `.babelrc` file. It's also often easier to read the configuration in a separate file since it's isolated from all your other configuration and package.json.

It's also worth noting that Babel can transpile experimental features. You can view links to the different experimental JavaScript features under the [Plugins page on Babel's website](https://babeljs.io/docs/en/plugins). As you can see, JavaScript features progress through different stages. They're initially just ideas, which is called stage-0.

- Stage-1 is a formal proposal.
- Stage-2 is a draft spec.
- Stage-3 is a completed spec with the initial browser implementations.

So as you can see, the risk goes down as the stages progress. Bottom line, if you want to use these experimental features, you'll want to install the appropriate plugin and configure Babel to use this plugin.

Ollie-UI uses only standardized JavaScript features in comparison but felt important to be aware of this option if you prefer to use experimental features.

And as a quick note, if you're deploying JavaScript code to a known environment then you're lucky because you know a lot about your deployment environment. This gives you the power to intelligently only transpile the new parts of JavaScript that your target environment doesn't understand. Node environments have recently added excellent support for ES6, so there aren't many features that you need to transpile. So to avoid transpiling features unnecessarily, you can select from one of these two plugins for Babel. They both accomplish the same thing, but the one on top is Node-specific because it determines what needs to be transpiled by sniffing for your Node version. The one on the bottom sniffs for features instead and thus, isn't Node-specific. Both options are intelligent enough to only transpile the pieces that your environment doesn't currently support.