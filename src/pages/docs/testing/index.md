---
title: Testing & C.I.
excerpt: >-
  Learn how Ollie-UI uses Mocha & Chai to become a regular
  developer barista!
template: docs
---

Since JavaScript has no built-in opinions on handling testing, you need to spend a lot of time browsing the web and investigating strategies before you can get rolling. So in this module, I'd like to help outline the landscape to help you understand the key decisions that you need to make. Because if you're new to automated testing, just picking your tools and deciding how to use them is a major hurdle. So we'll begin by reviewing six key decisions Ollie-UI makes, including testing frameworks, assertion libraries, helper libraries, and more. Ollie-UI has some example tests so you can see how they're setup and used.

Test Decisions Overview
Comprehensively covering JavaScript testing is to large to tackle here, so know that Ollie-UI focuses on the style of testing that's most commonly configured in JavaScript development environments, which is unit testing.

Unit testing focuses on testing a single function or module in an automated fashion. Unit tests often assert that a certain function returns an expected value when past certain parameters. Unit tests mock out external dependencies like APIs, database calls, and file system interactions, so the results are fast and deterministic.

Two other styles that are worth looking into that we won't cover in Ollie-UI are integration testing, which focuses on testing the interactions between multiple modules and automated UI testing, which tests the application by automating clicks and key strokes within the actual UI and asserting that it interacts in expected ways.

Tools like Selenium, which automate browser interactions are popular in this space. There are various other testing approaches as well, but in Ollie-UI, the focus is on automated unit testing.

There are no less than six important decisions you need to consider when setting up automated unit testing in JavaScript. You have to choose a framework, an assertion library, helper libraries, you have to decide what environment that you want to run your tests in, you need to decide where to place your test files, and finally, decide when to run your tests. Let's review how Ollie-UI covers these six key items.
