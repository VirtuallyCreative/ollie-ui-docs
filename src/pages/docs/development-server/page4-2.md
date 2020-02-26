---
title: Sharing Work-In-Progress
weight: 2
template: docs
---

# Sharing work-in-progress

When sharing W.I.P applications Ollie believes in simplicity is best.

So, why not just put the app on a traditional cloud provider like AWS, Azure, Google Cloud, Heroku, Netlify, DigialOcean, etc...?

The answer is, you absolutely could. It's just not baked into Ollie - yet. It's on the [Roadmap](https://github.com/VirtuallyCreative/ollie-ui/projects/2).

Why doesn't Ollie have that out of the box?

**Sharing work-in-progress should be fast - really fast, and free.**

Ollie likes free - so it uses some quick and easy options to get your work-in-progress up fast.
Think of this as *before* going onto any cloud surface that could start charging money.

## ngrok

[ngrok](https://ngrok.com/) allows you to expose a web server running on your local machine to the internet. Just tell ngrok what port your web server is listening on and then any time you want to expose your work to the public web, you start up your app and then type something this: npm run share.

That opens the src directory in your browser ready to share (copy/paste the URL) fast and with no configurations needed and with HTTPS enabled!

It's as simple as that. Quite slick.

With ngrok, anyone with the url can access your app while your it's open. But the advantage of ngrok of course is it's lower
friction to get set up and has a local dashboard to monitor your "web server".

## Surge.sh

Surge assumes that your app is just static `.html`, `.javascript`, and `.css` files. Surge only supports static files. But the upside is extreme simplicity. You don't have to punch a hole in your firewall to expose your work. Instead you can quickly move your static files up to their public web server.

If you want to use Surge as a more permanent host, you can even use your own domain name. So with that approach, Surge becomes an easy way to do automated deployments via the command line - something covered in the Production Deployment section.

## Browsersync

If you choose to use Browsersync for your web server instead, that synchronized browsing experience that it offers will continue to work when you're using localtunnel. So this way even if your mobile devices and your development machine are on separate networks, they can still interact in a synchronized browsing experience.
