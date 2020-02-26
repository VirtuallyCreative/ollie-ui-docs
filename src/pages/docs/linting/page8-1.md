---
title: ESLint Config
weight: 1
template: docs
---

Much like the rest of life in JavaScript land, ESLint is filled with decisions. Let's explore some of the key decisions that we'll make configuring it. Choosing ESLint was the easy part. The hard part is this next set of decisions that we need to make.

Out of the box, Ollie-UI includes a base-level ESLint configuration that upholds some standard rules for all projects.

```json
{
  "root": true,
  "extends": [
    "eslint:recommended",
    "plugin:import/errors",
    "plugin:import/warnings"
  ],
  "parserOptions": {
    "ecmaVersion": 7,
    "sourceType": "module"
  },
  "env": {
    "browser": true,
    "node": true,
    "mocha": true
  },
  "rules": {
    "no-console": 1
  }
}
```
