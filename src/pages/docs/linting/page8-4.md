---
title: ESLint Config - Warnings & Errors
weight: 4
template: docs
---

Which of your rules should merely produce warnings and which rules are a big enough deal to justify throwing errors
instead?

#### Let's consider the implications of warnings versus errors.

With a warning, it doesn't break the build so you can continue with development without fixing the issue. In contrast,
errors actually break the build which can be helpful when the linter finds a more critical issue that should catch your
attention immediately and keep you from moving forward. But, since warnings don't stop development they can ultimately
be ignored. This is handy in the moment when you're focused on implementing a feature and don't want to stop your flow
to fix a minor issue But, it also means that warnings can potentially be committed because they may not break the build.
Errors, in contrast, are a clear wall to moving forward. They can't be ignored.

Due to these trade-offs, I've seen some shops only use warnings because they favor moving as fast as possible and I've
seen other shops use only errors because they favor stopping any work that isn't good enough to commit at that moment.

#### Ollie-UI is setup using both.

Warnings are good for minor stylistic issues and errors are useful for items that are likely to produce bugs. The bottom
line is, it's important that your development team agrees that warnings are not acceptable. If you commit code that
produces warnings then quickly, your linting output will get so noisy that it's useless and it will mask other helpful
output like test results that also display on the same command line.

If you choose errors then you don't have to worry about people ignoring linting issues. They will be forced to comply
because the application won't build.

Ollie-UI lets you toggle these in the settings so, I recommend choosing carefully based on context. You'll likely decide
that only some rules weren't throwing an error versus a warning.