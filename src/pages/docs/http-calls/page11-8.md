---
title: Serve Mock Data via JSON Server
weight: 8
template: docs
---

Now that we have the mock data we need, let's start up JSON Server and tell it to use our mock data, now the great thing about JSON server is it will parse our JSON file and make a mock API for each top level object that it finds.

Ollie-UI uses the `db.json` file that is generated and makes the api available on **port 3001**.

**Make sure to pick a different port if 3001 isn't available on your machine, but I'm deliberately choosing a different port than port 3000 which we're using to host our app.**

mock-json-datafiles.png

Use `npm run start-mock-api`. When you do, we can see the list of resources that JSON Server is exposing, in this case it found our top level object, `users`, but if we added more top level objects it would create an end point for each one, slick.

Now let's take this URL and go back to browser (http://localhost:3001). We'll open up a new tab and paste it in and we can see an array of `users` being returned as expected, so this is the mock data that's sitting in `db.json` but now it's getting served up over HTTP on a mock API.

Ollie-UI mocks data to change every time that you run the app, this way it's constantly viewing different potential edge cases in the system.

![Items](/images/items.png)

Randomized data helps simulate the real world and it captures issues in development such as edge cases, empty lists, long lists, long values, it also provides data for testing, filtering, sorting and so on.

Every time that Ollie-UI starts the app it will generate new mock data and start up the mock api that serves the data, and the interesting thing about JSON Server is if we manipulate the data by making calls to edit or delete records it will actually manipulate the data file behind the scenes, this means you can even use this for integration tests or reload the page and see your changes reflected, it does a great job of mimicking a real api with an actual database behind the scenes.

Of course to see this in action we need to update the application to hit the new mock api instead of that Express API call that is avaiable, so let's assume that the Express server that we set up here is for our real production API and that the mock API that we set up is what we want to use during development.

```javascript
export default function getBaseUrl() {
  return getQueryStringParameterByName('useMockApi') ? 'http://localhost:3001/' : 'https://ollie-api.herokuapp.com/';
}
```

**Quick note**, since we're starting Express and the mock Api at the same time, the app may fail on the first load if it tries to call the mock API before it's up. If so just hit `F5` to refresh.