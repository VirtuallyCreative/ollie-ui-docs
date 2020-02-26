---
title: Sharing Work-In-Progress
weight: 2
template: docs
---

# Sharing work-in-progress

When sharing W.I.P applications Ollie strives to be simple.

So, why not just put the app on a traditional cloud provider like AWS, Azure, Google Cloud, Heroku, Netlify, DigialOcean, etc...?

The answer is, you absolutely could. It's just not baked into Ollie - yet. It's on the [Roadmap](https://github.com/VirtuallyCreative/ollie-ui/projects/2).

Why doesn't Ollie have that out of the box?

**Sharing work-in-progress should be fast - really fast, and free.**

Ollie likes free - so it uses some quick and easy options to get your work-in-progress up fast.
Think of this as *before* going onto any cloud surface that could start charging money.

## Localtunnel

[Localtunnel](https://www.npmjs.com/package/localtunnel) offers an elegant way to expose your local host via a public url. It punches a hole in your firewall so that your local machine can operate as a web server. The nice thing about localtunnel is how easy it is to get started. You install the localtunnel npm package globally, and then any time you want to expose your work to the public web, you start up your app and then type something like this: `npm run share`.

That opens the `src` directory in your browser ready to share (copy/paste the URL) fast and with no configurations needed.

It's as simple as that. Quite slick.

With localtunnel, anyone with the url can access your app while your localtunnel is open. But the advantage of localtunnel of course is it's lower
friction to get set up.

## Surge.sh

Surge assumes that your app is just static `.html`, `.javascript`, and `.css` files. Surge only supports static files. But the upside is extreme
simplicity. You don't have to punch a hole in your firewall to expose your work. Instead you can quickly move your static files up to their public web server.

If you want to use Surge as a more permanent host, you can even use your own domain name. So with that approach, Surge becomes an easy way to do automated deployments via the command line - something covered in the Production Deployment section.

## Browsersync

If you choose to use Browsersync for your web server instead, that synchronized browsing experience that it offers will continue to work when you're using localtunnel. So this way even if your mobile devices and your development machine are on separate networks, they can still interact in a synchronized browsing experience.
