---
title: Manipulate Data via JSON Server
weight: 9
template: docs
---

To prove that we can save changes to our mock data, there is an example API call in `api/userApi.js` that exports a public function `deleteUser()`.

```javascript
export function deleteUser(id) {
  return del(`users/${id}`);
}

// Can't call func delete since reserved word.
function del(url) {
  const request = new Request(baseUrl + url, {
    method: 'DELETE'
  });
  return fetch(request).then(onSuccess, onError);
}
```

As you can see it looks at users and then passes ID that it receives. And you can see that it is delegating to a separate function called `del()`. This might seem rather redundant but this is the same pattern that we followed when we were setting up `get` and `getUsers`.

This private `del()` function gives us a centralized spot to handle all our delete calls, so if we add other deletion functions related to users, each public function call is nice and short, and I had to call this `del` because `delete` is a key word in JavaScript.

After we make our call to delete users, we're currently populating the table, and what we now want to do is get a reference to all of the delete links on a page, and to do that we're going to look for anything with a class name of delete user as all the delete links have that class. This provides an array-like structure that is iteratable, so I'll use `array.from()` to be able to iterate through the list of delete links and then attach a click handler to each one.

```javascript
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

    // Setup Delete User
    const deleteLinks = global.document.getElementsByClassName("deleteUser")

    // Must use array.from to create a real array from a DOM collection
    // getElementbyClassname only returns an "array like" object
    Array.from(deleteLinks, link => {
        //Attach click handler to each link in the list
        link.onclick = function (event) {
            const element = event.target
            event.preventDefault() // stops any change to the URL
            deleteUser(element.attributes["data-id"].value)
            const row = element.parentNode.parentNode;
            row.parentNode.removeChild(row) //removes the clicked row from DOM
        }
    })
```

We prevent defaults so that the click doesn't actually produce any change to the URL, then call `deleteUser()` and then remove the row that we just clicked from the DOM. This could all be handling using a JS framework like React, Angular, other popular frameworks, but opted to use plain vanilla JavaScript here to avoid adding confusion.

Using the Inspector, watch the network traffic and see the delete call go through to delete the different users. if I click on one of these and look at the headers, we can see we get a 204 no content, we can see that the delete is going through as our request method as expected, and here's the cool part, if I hit Refresh right now, only one record is here because when I click delete on those two, it really did write to db. json, if we come back over here, we can see now our db. json only has one record when before it had three. We can also see that JSON Server is continuing to log all the different calls that are being made to our mock API. This is really handy when you're debugging calls along the way, and the great thing is this data will persist until we restart the app and new random data is generated.

**Quick note, you may have to hit CTRL+C multiple times to kill the running process, since now we're running multiple processes on the same command line. You'll notice that JSON Server throws an error when you kill it this way but there's no impact so you can ignore it. If you prefer, you can kill the terminal and open a new instance.**