---
title: The Road to Production
excerpt: >-
  Ollie-UI has several steps to get the application ready for PROD.
  Learn about each step in the Road to Production.
template: docs
---

Ollie-UI provides an automated production build pipeline using Webpack.

Each aspect of this will be covered in more detail including minification to speed load times, with source maps generated to support debugging in production.

Setup dynamic HTML handling for production specific concerns, and cache busting to ensure that users receive the latest version of our code upon deployment.

Additionally, Ollie-UI features bundle splitting so that users don't have to download the entire application when just part of it changes as well as error logging so that we know when bugs sneak their way into production both from the server side and from the front-end perspective using Rollbar, Matomo and HEAP Analytics all in tandem.