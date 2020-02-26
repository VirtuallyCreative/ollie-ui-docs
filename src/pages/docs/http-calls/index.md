---
title: HTTP Approaches
excerpt: >-
  Learn why Ollie-UI picked Express.js as the go-to framework
  to help rapidly develop our HTTP approach.
template: docs
---

Most modern javascript applications deal with making or managing HTTP calls. Ollie-UI is no different providing several tools out of the box to help with API development,

- Mock API Calls
- Generate Fake Data from Schema for Testing
- Graceful error handling


## HTTP Call Approaches
There are at least half a dozen popular ways to handle HTTP calls in JavaScript.

The library options depend on where you're running your app. Node provides a built-in package called `http`, it's a low-level library that provides basic functionality for making HTTP requests. Now, `request` is a popular higher-level library that makes it simpler to make these calls in Node. It provides a streamlined API that many prefer.

If you're running JavaScript for the browser, you have a different set of options. You can, of course, use plain old XML http requests, also known as XHR for short. This is the native and original way to get the job done, and it's hard to believe, but the birth of XMLHttpRequest was over 21 years ago in 1999 and it's been broadly supported in browsers for well over a decade.

The main gripe with a plain XMLHttpRequest is you're doing all the heavy lifting yourself, you have to manually check the ready state, use a verbose API to set the request header and attach to the on readyState change and error events to get the job done. As you can see it's a lot of plumbing.

Most people prefer alternatives that offer a cleaner API. For a long while, people have often reached for jQuery to get this job done. jQuery's `$.ajax` object has been the workhorse of the web for many years.

Some more full-featured frameworks like Angular include their own HTTP service, so you don't have to make this decision at all if using them out of the box. But assuming your framework doesn't natively handle HTTP, another increasingly popular option is Fetch, which is a standard proposed by the Web Hypertext Application Technology Working Group. Now, Fetch offers a streamlined API that elegantly handles HTTP calls, however, some browsers lack native support, so you'll want to use a polyfill with this option. You can find polyfills for both the regular version of Fetch or the isomorphic version of Fetch which we're going to talk about in a moment, but it's also worth noting that Fetch is currently a streamlined API, so it doesn't offer all the features of raw XML HTTP requests, or the other libraries that extract XML HTTP requests away that we'll talk about in a moment. So for instance, you can't cancel a Fetch at this time, but this limitation is being actively worked, so although Fetch support is currently being added to popular browsers, it's feature set is expected to grow over time. Here's an example of using Fetch, as you can see, you create a request object and pass that to Fetch. And since Fetch uses process to handle results, you provide a success and error handler to the then function.

Full-featured libraries like Axios and SuperAgent that we'll talk about in a moment are great, but the new native Fetch API is likely to provide all the power that you need. So finally, some packages work on both the client and the server, isomorphic-fetch is an NPM package that provides a Fetch-like API that runs on a server via Node and in the browser, that's why it's called isomorphic-fetch, more recently the term universal JavaScript has become popular to describe JavaScript that runs on both the client and the server. You can also choose to use XHR which is a package available on NPM, XHR provides a subset of the request library that we talked about over under the Node column, but the subset of features that it supports run on both Node and the browser. Now if you're looking for full featured options, SuperAgent and Axios are popular libraries that run on both NodeJS and the browser, both are elegant and popular, but I personally prefer Axios because it offers a clean promise-based API. Here's an example of a call using Axios. This code is simple, easy to read and nicely declarative. I enjoy the promised based API. James K. Nelson describes Axios as the XMLHttpRequest library which takes all the good parts from Angular's $http and throws out everything else, but SuperAgent is quite popular as well, it even has it's own plug in an ecosystem. Now, that's a lot of options, so let's sum this up. If you're working only on Node, you'll probably want to use requests unless you have a good reason to avoid taking on another dependency. If you're in the browser, then Fetch with a polyfill is the most future proof approach since you won't need a polyfill once all browsers finish adding support. However this also assumes that you can live with the limitations of Fetch.
