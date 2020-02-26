---
title: ESLint Config - Experimental
weight: 8
template: docs
---

Another issue you may run into is that ESLint doesn't support many experimental JavaScript features at this time.

Now, ESLint supports all of ES6 and ES7 natively and is expected to continue adding support for standardized features as
JavaScript progresses. It also supports object spread even though that's currently and experimental feature. But what if
you wanted to use other experimental JavaScript features? Well, then, you'll likely want to use babel-eslint instead,
because it also lints stage zero through four features.