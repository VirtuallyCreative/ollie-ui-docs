---
title: DOM Tests
weight: 5
template: docs
---

Unit testing is important when creating complex business logic, but how about UI or Interaction testing?

For UI/Interaction testing we use JSDOM, here is a simple example of selecting something in a DOM in memory and checking - in this case, the copy of an H1 on a page.

```javascript
// Require Chai
let { expect } = require('chai'),
    jsdom = require('jsdom'),
    path = require('path'),
    fs = require('fs');


// describe('Our first test', () => {
//   it('should pass', () => {
//     expect(true).to.equal(true);
//   });
// });

describe('index.html', () => {
    it('should have h1 that says Users', () => {
        const index = fs.readFileSync(path.resolve(__dirname, '../src/index.ejs')).toString('utf8');
        const { JSDOM } = jsdom;
        const dom = new JSDOM(index);
        const h1 = dom.window.document.getElementsByTagName("h1")[0];
        expect(h1.innerHTML).to.equal("Users");
        dom.window.close();
    })
})
```

We describe this one as `index.html` because that is going to be the file that we're wanting to test in this case.
Inside we're going to say that it should say HopeJS Framework.

Remember that we have a simple page sitting inside of here, so we're just going to write a test that confirms that markup is there. So first, let's get a reference to our `index.html` file and hold it in memory. To do that I'm going to say `const index = fs.readFileSync` and then put in a reference to our `index.html` file. Also specify that it is in `utf-8`.

So now we have the contents of our `index.html` file held in memory within a constant called index. So we're ready to now use JSDOM. So let's say `jsdom.env`, and this is our way of defining the JSDOM environment. And we will pass it, our `index.html` file, because this constant represents the content of `index.html`.

If you want JavaScript to run as part of your JSDOM environment, you can pass an array of JavaScript files as the second parameter here. But note that any of those files utilize fetch, you need to use isomorphic-fetch instead because fetch is a browser feature, so it won't be available by default in the Node environment.

We don't need any JavaScript for this particular test, so I'll just omit the second parameter.

The second parameter for this is a callback function, which is run after JSDOM is completed, pulling `index.html` into memory making a virtual DOM in memory. And it takes two parameters, an `err` and a `window` argument. The `window` here represents the window in the browser, just like you could say `window.` when you're in the browser, now you can do so right here in Node because we have a virtual DOM in memory.

So we're going to write a test that confirms this text is there. To do so, we want to get a reference to that `h1`. We define a constant called `h1` and then say `window.document.getElementsByTagName()` and the tag name that we're looking for is `h1`.

Now this returns an array-like object so I'm just going to say give me the first `h1` on the page because we know that our h1 is the first one on the page. So we now have a reference to the `h1` on the page, we're ready to write our assertion. We say we expect the innerHTML of `h1` to equal its `value`, which is Users.

Finally, we'll go ahead and close the window just to free up the memory that was taken when we created our in-memory DOM.

So we'll hit save and now we should be ready to come down here and say `npm test`. Or if you want to save some typing, `npm t` does the same thing.

Our test should be passing.

To prove that this is working, go ahead and change the text of the `h1`, hit save, and then rerun our test. It should fail.

When you're doing an asynchronous test, one that involves having a call back here, you need to add this `done` parameter so Mocha knows that it's now safe to evaluate whether your `expect` is `true` or `false`.