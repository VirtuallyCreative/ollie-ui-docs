---
title: Presets
weight: 6
template: docs
---

ESLint comes with a preset that implements a logical set of defaults that can save you a lot of time. It decides what is
a warning and error for you and enables the rules that it thinks make the most sense for most people.

HopeJS uses ESLint's standard rules as a good shortcut to get started, then I tend to tweak a few of the settings based
on our team's feedback and the project requirements.

This is a nice compromise because it avoids the work of starting from scratch, but it still offers complete power in
tweaking the settings as we see fit.

We could go a step farther and use an existing set of rules like airbnbs, XO, or standard JS. Assuming that you don't
mind the decisions that they've made, this is a great way to avoid spending a lot of time arguing about all the
decisions that I just discussed previously.

It's also worth noting that standard JS isn't actually a standard. In fact, ironically, many of the rules that it
enforces like disallowing semi-colons and only allowing single quotes for stings, are actually quite unpopular in the
JavaScript community. All of these options use ESLint but they enforce strong opinions so you don't have to make any
decisions configuring rules. In fact, with standard JS, you can't change any rules at all but assuming that you're
willing to accept the strong opinions in these presets.