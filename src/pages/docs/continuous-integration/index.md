---
title: C.I. and Testing
excerpt: >-
  Ollie-UI uses CI and Testing to make sure code quality stays
  high while keeping development streamlined.
template: docs
---

While we're talking about assuring quality with testing there's another important practice to consider, continuous integration.

When we commit code, it's handy to confirm immediately that the committed code works as expected when on another machine.
Setting up a continuous integration server to assure that we're notified when builds break is critical. That's what a continuous integration server is for. The CI server catches a number of potential mistakes.

*Have you ever forgotten to commit a new dependency?*

*Have you ever installed an npm package but forgotten to save the package reference to package.json?*

*Maybe you added a new step to the build script but it doesn't run cross-platform?*

*Perhaps the version of Node that you're running locally is different from the one you're using in production, so the app may build just fine with the version on your local machine but fail on the continuous integration server?*

*Maybe someone just completed a merge but made a mistake along the way that broke the build?*

These are just a few great reasons to run a continuous integration server. The point is, a **C.I. server catches mistakes quickly**.

### What Does Continuous Integration Do?
First, it builds your application automatically the moment that you commit. This assures that your application builds on another machine. A CI server makes it clear who broke the build by checking every commit. It also runs your test suite.

Of course, you should be running your tests before committing but, a CI server assures it always happens and it assures that the tests pass on multiple machines. If the tests don't pass, then your commit has issues. So it's important to have a separate server run your tests to confirm they pass on more than just your machine. A CI server can run tasks like code coverage and reject a commit if code coverage is below a specified threshold. And finally, although it's not required, you can even consider automating deployment using a CI server. With this scenario, if all these aforementioned checks pass your application is automatically deployed to the production.

### Choosing a CI Server
Travis CI is a Linux-based continuous integration server.
Appveyor is s a Windows-based continuous integration server.

Ollie-UI has set up two continuous integration servers, Travis CI and Appveyor out of the box. Why two? Because Travis CI runs on Linux and Appveyor runs on Windows.

This means we can be assured that our build process runs on Mac, Linux, and Windows.
