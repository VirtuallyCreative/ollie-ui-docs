---
title: Introducting Ollie-UI
subtitle: Oh great, another JavaScript framework...?
date: 2020-05-27T04:00:00.000Z
thumb_img_path: /images/surge.sh-example.png
content_img_path: /images/ollie-ui-big.png
excerpt: Ollie-UI is a starter-kit to help you rapidly develop prototype single
  page applications or APIs.
template: post
---
**Ollie-UI** is a culmination of several years of self-taught front-end development and 100's of hours of JavaScript, Web Development, DevOps courses and tutorials merged into a starter-kit that I've used for 5+ in-production projects. 

With so many decisions a front-end developer has to make I figured I'd stop being inconstant, forgetting this setup item or that, on various projects and combine it all together into something that scaffolds almost any new project I work on.

It's some dependency-heavy scaffolding on top of [Express.js](http://expressjs.com) to provide a quick, easy mock API to prototype against.

```javascript
// ...
const port = 3000
// ...
app.get('/', function mainHandler(req, res) {
    res.sendFile(path.join(__dirname, '../src/index.ejs'))
})
// ...
app.listen(port, function(err) {
    if (err) {
        console.log(err) // eslint-disable-line no-console

        // Rollbar.com Error Tracking, uncomment to enable
        // rollbar.critical("Critical Error Caught: ", err)
    } else {
        open('http://localhost:' + port)
    }
})
```

Some of the things out of the box are, 

* **Webpack Devel­op­ment / Pro­duc­tion**  —  Sep­a­rate dev and prod con­figs & builds. Local devel­op­ment means fast builds via the in-mem­o­ry web­pack-dev-serv­er, and for pro­duc­tion builds every pos­si­ble opti­miza­tion needs to be utilized, making for slower builds at the gain of better optimizations.
* **Hot Mod­ule Replace­ment**  —  as changes are made to JavaScript, CSS, or tem­plates, the web­page seam­less­ly refreshes.
* **Dynam­ic Code Split­ting**  —  Webpack sorts out how to chunk JavaScript in a con­fig file, auto-magically.
* **Async Dynam­ic Mod­ule Load­ing** - Load only the code/​resources need­ed, when they are need­ed, with­out ren­der blocking.
* **Mod­ern to Lega­cy JS Bun­dles** —  Deploy mod­ern ES2019+ JavaScript mod­ules while grace­ful­ly pro­vid­ing a fall­back lega­cy bun­dle for lega­cy browsers (with all of the tran­spiled code and polyfills).
* **Cache Bust­ing via manifest.json** - Sets long expiry data for our sta­t­ic assets, while also ensur­ing that they are auto­mat­i­cal­ly cache bust­ed if they change.
* **Crit­i­cal CSS**  —  This is some­thing that makes ini­tial page loads sig­nif­i­cant­ly faster by only delivering the styles needed first.
* **Work­box Ser­vice Work­er**  —  Lever­age Google’s Work­box project to gen­er­ate a Ser­vice Work­er for us that will know about all of our project’s assets.
* **PostC­SS** —  The ​“Babel of CSS”, lets you SASS like a boss.
* **Image Opti­miza­tion**  —  Opti­mize them via auto­mat­ed tools like mozjpeg, optipng, svgo, etc for next step...
* **Auto­mat­ic .webp Cre­ation**  —  Chrome, Edge, and Fire­fox all are sup­port­ing .webp, and can signifigantly boost performance.

**HTTP & API** 

Ollie uses a Express, with a centralized API approach which configures all calls, handles pre-loader logic and also errors.