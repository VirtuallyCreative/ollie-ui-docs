---
title: Concurrent Tasks
weight: 4
template: docs
---

## NPM Tasks in Parallel
NPM allows for tasks to be run side-by-side rather than one-after-another using the --parallel flag in your task. The start, staging, and build steps all have parallel tasks that run along-side each other. Using this along with pre/post hooks are a great way to sequentially fire multiple tasks in a particular order.

**Note: should *any one* task fail, the whole task process fails.**

Running `$ npm run start` has several parallel tasks (and also has a pre-hook that runs before those tasks start).

- `open:src` uses the src directory for the webserver
- `lint:watch` runs (css/js) code checks and continues to check code ("watch") as you type and save changes.
- `test:watch` runs code unit testing with Mocha and continues to run tests as you type and save changes.
- `start-mockapi` starts the ExpressJS back-end to deliver a REST API endpoint you can mock data for and return to test any front-end data-consuming feature.