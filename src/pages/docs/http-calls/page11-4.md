---
title: Mock HTTP
weight: 4
template: docs
---

It's often helpful to mock HTTP requests when working with data from outside sources.

## Why?

Well maybe you want to unit test your codes so that your tests run quickly and reliably, or maybe the existing web services in your development or QA environment are slow or expensive to call. Mocking HTTP means that you can receive consistently instantaneous responses. Or, maybe the existing service is unreliable, with a mock API you can keep working even when the services are down. Maybe you haven't even created any web services yet!

If you haven't decided how to design your web services, mocking allows you to rapidly prototype different potential response shapes and see how they work with your app.

For example, perhaps a separate team is creating the services for your app, by mocking the service calls, you can start coding immediately and switch to hitting real web services when they're ready, you just need to agree on the API's proposed design and mock it accordingly.

Finally, maybe you need to work on a plane, on the road or TTC where connectivity is poor. Mocking allows you to continue working while you're offline.