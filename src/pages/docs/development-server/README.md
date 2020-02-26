# Development Web Server

Ollie uses [Express](http://expressjs.com) as the choice to handle everything server related. It's a bit more middleweight. Unlike [http-server](https://www.npmjs.com/package/http-server) and [live-server](https://www.npmjs.com/package/live-server), it's not just for static files. You can serve up complex APIs via node using Express as well which is important for Ollie's mock data features.

The advantage to choosing Express is you can use it in production as well. So if you choose Express for your dev server, you have the advantage
of running the same web server in all places. This allows you to create a common configuration and use it in all environments.

If you're building APIs in node, then this is a big win that makes using Express as your development server an easy choice.

If you have an existing API layer using non JavaScript technologies like Ruby, Python,. NET or Java, then Express is likely overkill for your development web server but could give you a development-friendly way to mock JSON data from your real server.
