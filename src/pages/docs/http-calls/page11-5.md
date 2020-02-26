---
title: Mock HTTP Approach
weight: 5
template: docs
---

If you're writing unit tests then [Nock](https://github.com/nock/nock) is a handy way to mock HTTP calls on your tests. You tell Nock the specific URL that you want to mock, and what it should return. Nock will hijack any HTTP request to the URL that you specified and return what you specified instead. This way, your tests become deterministic and no longer make actual HTTP calls and is great for rapid prototyping.

But, if you're wanting to do day to day development against a mock API, you'll want something more, if you've already centralized all your API calls within your application then you can use this centralization to your advantage by pointing to a static file of JSON encoded data rather than making the actual HTTP call.

Or, you can of course create a web server that mocks out a real API. Thankfully there are libraries that make this easy such as [api-mock](https://www.npmjs.com/package/api-mock) and [JSON server](https://www.npmjs.com/package/json-server).

Under the hood, HopeJS uses JSON server, with JSON server you create a fake database using static JSON, then when you start up your JSON server it creates a web service that works with your static JSON behind the scenes, so when you delete, add or edit records, it actually updates the file. So this provides a full simulation of a real working API but against local mock data that's just sitting in a static file, this is really useful because the app feels fully responsive and you don't have to go through the work of standing up a local database and web server by hand. What if you want to use dynamic data instead of the same hard coded data? Well that's where JSON Schema faker comes in handy. JSON Schema faker generates fake data for you. You specify the data type you like, such as a string, number or boolean, and it will generate random data which you can write to a file. And you can specify various settings that determine how it generates the data such as ranges for numbers or useful generators that create realistic names and emails.

In summary, if there's already a solid service layer available then I suggest putting it to use. But if a separate team is building a service layer and you haven't build it yet, I suggest trying a mock API so that you can move quickly without being reliant on a real API backend. The lessons you learn with your mock API can often help guide your API design.