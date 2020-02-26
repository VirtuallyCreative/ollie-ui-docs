---
title: ESLint Config - File Formats
weight: 2
template: docs
---

Let's begin with decision one. Where should you put your configuration?

The `.eslintrc` file in the /root/ of the app folder structure.

ESLint flexability means it supports five different file name conventions for configuration out of the box.

To cut down on this confusion and forge a path that solidifies practices across the framework, picking the `.*rc` style of file to hold configuration settings seems the most approprate since we've picked this method in the past for other settings.