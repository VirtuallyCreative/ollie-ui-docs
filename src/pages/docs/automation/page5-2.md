---
title: Pre/Post Hooks
weight: 2
template: docs
---

NPM supports a convention-based pre and post hooks allowing any scripts that you prefix with the word pre will run before the script with the same name.

And any scripts you prefix with the word post will run after the script with the same name.

Currently, these commands have pre and/or post hooks,

- `start`
- `start-mockapi`
- `staging`
- `build`

### Use-Case Examples
`$ npm run start` contains a prestart hook. It displays a custom message the developer can set for the project.
The `startMessage.js` file is just a single import and `console.log()` line.

```javascript
  // startMessage.js
  import chalk from 'chalk';
  /*eslint-disable no-console */
  console.log(chalk.green('Productizing Deliverables...'));
```

```javascript
  // package.json
  "prestart": "babel-node core/startMessage.js",
  "start": "npm-run-all --parallel open:src lint:watch test:watch start-mockapi",
```

Now, when you run the `$ npm run start` command, the prestart will automatically fire first, printing our start message to the console.

If you wanted to auto-run something after start you could make a poststart script and it will automatically run after the start command.