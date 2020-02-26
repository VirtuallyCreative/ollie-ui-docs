---
title: Centralizing Requests
weight: 1
template: docs
---

Ollie-UI takes a Centralized approach to HTTP calls by handling them all in a single spot to centralize key concerns.

First, it gives you one place to configure all API calls, this way you can configure important configuration like base
URLs, preferred response type and whether to pass credentials in a single spot. You make sure all `get`, `put`, `post` and
`delete` calls are handled consistently when asynchronous calls are in progress, it's important that the user is aware.
This is often accomplished via a moving preloader icon, commonly called a spinner. By centralizing all your calls, you
can keep track of how many asynchronous calls are in progress, this assures a preloader continues to display until all
async calls are complete, centralization also gives you a single place to handle all errors, this ensures that any time
an error occurs, your application can handle it in a standardized way, perhaps you want to display an error dialogue, or
log the error via a separate HTTP request. By centralizing your API calls, a single method can assure that this occurs
for all calls.

Finally, centralizing API calls gives you a single seam for mocking your API. Centralizing calls means you can point to
a mock API instead of a real one by changing a single line of code that points to a different base URL.