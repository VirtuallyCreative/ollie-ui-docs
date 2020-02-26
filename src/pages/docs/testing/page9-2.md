---
title: Chai
weight: 2
template: docs
---

Mocha doesn't come with an assertion library, so we have to pick our own. An assertion is a way to declare what you expect.

For example, here I'm asserting that two plus two should equal four. This is an assertion because I'm telling my test what I expect to happen.

If the statement is false, then the test fails.

There are many potential ways to declare assertions and test. Some frameworks might look like this example, others might use a keyword like assert instead of `expect`.

The most popular assertion library is Chai, but there are other assertion libraries out there to consider like `Should.js` and Expect. Most frameworks include their own assertions built-in, but since Mocha doesn't, Ollie-UI picked Chai for assertions because it's popular and offers an array of assertion styles to choose from.