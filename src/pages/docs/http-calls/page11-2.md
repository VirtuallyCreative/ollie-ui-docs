---
title: Fetch
weight: 2
template: docs
---

Ollie-UI uses the Fetch method along with the associated polyfill (from GitHub). It also relies on `Express` for setting up the web-server and providing a REST API.

For simplicity, Ollie-UI serves the API using the same Express instance that's serving our app during development.

```javascript
import express  from 'express'

//...

const port = 3000
const app = express()

// ...

app.get('/users', function(req, res) {
  // Hard coded for simplicity. Pretend this is a real endpoint...
  res.json([
    {"id":1,"firstName":"Al","lastName":"Romano","email":"viperousmango@gmail.com"},
    {"id":2,"firstName":"Alex","lastName":"Romano","email":"alexander.romano@live.com"},
    {"id":3,"firstName":"Alexander","lastName":"Romano","email":"alexander@virtuallycreative.ca"}
  ])
})
// ...
```

This is an example of a simple endpoint that returns user data. As you can see when we hit slash users, it should return a hardcoded array of a few records. Of course, in a real app, this would hit a database and perhaps be served by a different machine on a different web server, but, for development, some simple entries are hardcoded here instead of setting up a real database or separate API.

Now Ollie-UI can call the API using Fetch and display the results on the page.

```javascript
import 'whatwg-fetch';
import getBaseUrl from './baseUrl';
// ...
const baseUrl = getBaseUrl();

export function getUsers() {
  return get('users');
}

export function deleteUser(id) {
  return del(`users/${id}`);
}

export function addUser(id) {
    return add(`users/${id}`);
}

function get(url) {
  return fetch(baseUrl + url).then(onSuccess, onError);
}

// Can't call func delete since reserved word.
function del(url) {
  const request = new Request(baseUrl + url, {
    method: 'DELETE'
  });
  return fetch(request).then(onSuccess, onError);
}

// Add user called
function add(url) {
    const request = new Request(baseUrl + url, {
        method: 'CREATE'
    });
    return fetch(request).then(onSuccess, onError);
}

function onSuccess(response) {
  return response.json();
}

function onError(error) {
  console.log(error); // eslint-disable-line no-console
  // rollbar.critical("API Issue: ", error); // Handle Errors with preferred service
}
```

We can see that at the top I'm importing what working group fetch, so this polyfill will ensure that this code runs in browsers that don't yet have Fetch support natively, and as you can see I'm only exporting one public function, get users, all the other functions below are private.

The actual call that's using Fetch occurs here in the `get` function. Over this small amount of boiler plate setup, adding other get requests will require very little code because we only need to provide the URL. Fetch, along with promise resolution and error handling are an abstracted away behind this private `get` function.

This is a simple example only supporting `get` and `delete` but you might want to add functions for handling `put`, `post`, etc. The beauty of centralizing our calls here is we have one place to consistently handle all of our Ajax calls. If one fails, we have centralized error handling and if we wanted to show a preloader, we have one spot to keep track of any calls in progress. And if our base URL changes in different environments, we have a single place to configure.

With the mock API set up to use Fetch, let's call it from the `index.html` file.

```html
<!-- API Driven Table -->
  <div class="card">
      <header>
          <h1>Users</h1>
      </header>
      <p>A nisi ullam impedit molestiae, sapiente id, ... Quae, cupiditate?</p>
      <table>
          <thead>
              <tr>
                  <th>&nbsp;</th>
                  <th>&nbsp;</th>
                  <th>Id</th>
                  <th>First Name</th>
                  <th>Last Name</th>
                  <th>Email</th>
              </tr>
          </thead>
          <tbody id="userTbl">
            <!-- Dynamically Added via JSON Data -->
            <!-- Controlled inside index.js -->
          </tbody>
      </table>
  </div>
```

We created a table inside the `src/index.html` file, with a simple structure with the same headers from our mock data (and a blank column at the beginning, which we touch on later...). You can see that we have headers for ID, first name, last name and email, because this is the data structure that we're expecting to receive from our API call.

Table body tag deliberately has an ID here of users because we reference this.

```javascript
// index.js

// Import JS
import {
    getUsers,
    deleteUser,
    addUser
} from '../api/userAPI';
// Dynamically Generate Table data from API with no JS framework


// Populate table of users vai mock API call - do not put slash in path
getUsers('users').then(result => {
    // Start with Empty Obj
    let usersBody = "";
    // Loop through Data and display using Table
    result.forEach(user => {
        usersBody += `<tr>
    <td><a href="#" data-id="${user.id}" class="deleteUser">Delete</a></td>
    <td><a href="#" data-id="${user.id}" class="addUser">Add</a></td>
    <td>${user.id}</td>
    <td>${user.firstName}</td>
    <td>${user.lastName}</td>
    <td>${user.email}</td>
    </tr>`
    });
    // Find Table on Page
    var userTbl = global.document.getElementById('userTbl');
    // Replace blank tablebody with one using Data above
    userTbl.innerHTML = usersBody;
```

First, let's add a reference to the API call that we need, which is getUsers, then we make the call to getUsers and I use the `then` function on the promise to handle the result that we receive from our API call.

We then loop through the list of users returned and returned a string of HTML which I then place within the inner HTML of the users table body which we created in `index.html`. So this code will end up populating our HTML table.

Of course, in more robust applications this would be handled using React, Angular or some type of framework, but Ollie-UI uses plain vanilla JavaScript here to avoid adding the complexity of a framework since that's not the focus of this starter-kit.

Now if we go over to the browser and load our application we can see that our data is coming back, so now we can see that request going through, this is the request to users on our API, we get a 200 OK and the response is the JSON that we're returning from `Express`, and now we know that our call is going through using Fetch as we expected.