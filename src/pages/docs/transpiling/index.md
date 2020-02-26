---
title: Language & Syntax
excerpt: >-
  Learn a bit of JavaScript history to see why developers have strong
  opinions on versions and what makes syntax sugar so delicious.
template: docs
---

## Writing JS for "everyone"
With the advent of ES6 in 2015, JavaScript finally felt "grown-up" in a big way. And now with annual releases means that we can look forward to more improved JavaScript goodness every year. This is great, but it's also one of the many reasons transpiling has become a needed component to more robust projects.

## JavaScript Versions
I believe that to understand where JavaScript is and where it's headed, it helps to understand its history.

- Version one of JavaScript was born in 1997, created in a few short days by Brendan Eich.
- A year later, ES2 was released.
- A year later, we saw ES3. So far, so good.

But then they tried to tackle a much more aggressive release. No one could come to an agreement so ultimately, ES4 never happened. So JavaScript stagnated for a full decade before ES5 was finally released in 2009, with a number of notable enhancements. And then, the waiting game began again...

It took another six years, but ES6, also known as ES2015, was well worth the wait. Included were arrow functions, const, let, modules, classes, destructuring, generators, and so much more. The other huge piece of news was a commitment to annual releases.

But the ES6 release was so huge that apparently it wore everyone out because ES7 only had two features. The exponent operator and array. prototype. includes.

Now ES8, also known as ES2017, added some long-awaited features, including Async Await, class props, and object spread. Many people are already enjoying these features today by using transpilers that shim in the support. And this is a good segue for us to talk about why Ollie-UI uses Babel, a robust JavaScript transpilier.

## Transpilers
There are literally over 100 languages that compile down to JavaScript today. The two most popular ways to transpile JavaScript today are Babel and TypeScript.

Babel's big obvious selling point is it allows you to enjoy all the new features of JavaScript, even those that are currently experimental in a standards-based way. So Babel has a clear mission. It transpiles the latest version of JavaScript down to ES5 so that you can use all of these new features, but run them everywhere that ES5 is supported.

When you choose Babel, you're writing standardized JavaScript. This means that you can leverage the entire JavaScript ecosystem. That's a big win because it means any editors, libraries, or frameworks that you select are likely to be compatible with your code by default because you're writing completely plain JavaScript. Since TypeScript is a superset of JavaScript, some tools can't handle TypeScript. So with TypeScript, you may not be able to leverage all of the JavaScript ecosystem.

Although TypeScript and Babel both allow you to write standardized JS, Babel has historically been quicker to add support for stage 0 through 4 features, also known as experimental features. This means that you can often try out experimental features more quickly in Babel than with TypeScript. And of course for TypeScript to do its magic, type definition files and type annotations are required. So as you add new libraries, you need to also assure a type definition file is available in your project. If one doesn't exist, you need to create one to enjoy TypeScript's benefits when working with that code. Now I'm a fan of both of these options, but personally, I found that both type safety and autocompletion are quite good when working in ES6 in a modern editor like WebStorm, Visual Studio or Visual Studio Code. Since ES6 imports are statically analyzable, the editor can deterministically index your entire code base and thus provide reliable intellisense support on imports and the functions inside. When this is combined with the power of automated tests, Linting, Babel compilation, and great libraries like React that support declaring property types, I find that I rarely deal with tricky type-related issues at runtime. That long list of goodness that I just described catches the vast majority of issues for me at compile time even though I'm working in Babel instead of TypeScript.
