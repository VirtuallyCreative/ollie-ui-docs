---
title: Organizing by Feature
weight: 3
template: docs
---

On larger, more complex projects past a Single Page Application, consider organizing by feature instead of by file type.
There are two popular ways to organize your code: by **file type** or by **feature**.

## File Type
When you organize by file type, all files that serve the same purpose are placed together. This is a popular approach when working with MVC frameworks, which commonly expect you to use model, view, and controller folders to organize your application. However, the downside of this approach, is you end up having to bounce around the file system to open and work with related files.

## Feature
Organizing by feature puts all the files of the model, view, controller or whatever's needed into the feature's folder so you can go directly to the feature that you're working with and all the related files are sitting inside.