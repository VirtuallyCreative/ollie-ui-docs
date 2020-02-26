---
title: CI on Linux - Travis-ci
weight: 1
template: docs
---

Travis CI is a popular continuous integration server. It offers handy integration with GitHub, which makes it quick and
easy to add to your project.

Travis is configured via `.travis.yml`. Inside, we're going to declare just two things. We're going to declare that the
language that we're working with is node_js and then we can add a list of versions. I'm just going to check version six,
but I could have add other lines here to have it check version five, version four, and so on.

```yml
language: node_js
node_js:
- "10"
```

And that's all it takes to configure Travis for our continuous integration server (when we're working with GitHub).