---
title: Logic to POJOs
weight: 4
template: docs
---

Extract as much logic as possible into plain old JavaScript. If you Google this, some call this "POJOs".

When I say POJO, I mean *Plain Old JavaScript Objects*.
.NET developers use the term POCO to describe the same thing, though, in that case it stands for **Plain Old CLR Object**.

The point is, these files should contain plain logic, that isn't tied to any framework. When structuring your application, strive to place as much logic as possible in plain JavaScript.

For instance, if you're working in React, much of your logic should exist outside of React components. [This article about using 'POJOs for Good'](https://g-liu.com/blog/2015/08/object-oriented-programming-javascript-using-pojos-for-good/) has some great examples and breakdowns on the advantages of working this way and going the little extra mile to break logic down into re-usable chunks.

This makes your logic easy to test, easy to reuse, and helps minimize your ties to the framework that you've selected. This minimizes the impact of switching to a different framework down the road, because, we're in JavaScript... Let's face the facts, we'll probably be doing that.