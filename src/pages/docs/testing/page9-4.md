---
title: Running Tests
weight: 4
template: docs
---

HopeJS utilizes an in-memory DOM to help keep run tests as quickly as possible.

JSDOM is a library that simulates an actual browser by creating a DOM in memory that we can interact with.

You can think of JSDOM as a lighter-weight alternative to PhantomJS because JSDOM doesn't have a full, headless-browser behind the scenes. It's just focused on simulating a DOM in memory. The advantage of this approach is it's fast and quick to set up.

#### Decision five is, where should I put all my tests?

There are two popular schools of thought on organizing your test files. Let's review the merits of each approach.

One popular approach is to centralize all your tests within a folder called `tests` or something similar. So all your tests are completely separate from your source code. Mocha pushes you in this direction because it defaults to looking for tests and the root of your project in a folder called test. Now the primary benefit that I hear people claim about this approach is that it avoids adding noise to your source code directory. But I find this mindset misguided. Tests aren't noise, they're complementary to the files that they're testing. They're important. To me, if they're worth writing, they're worth seeing regularly within my source instead of tucked away in a separate folder. Another common reason that I hear is, I don't want my test files deployed to production. As you'll see in the production build module further in the Docs, this concern is unmerited. We'll only deploy the final bundled HTML, JavaScript, and CSS for the app to the actual production server.

Ultimately, I think much of the reason people are using a separate `test` folder is simply inertia. It's popular to create a separate `test` folder project in many ServerSide technologies for other reasons, but the separation just doesn't make sense on JavaScript apps.

I prefer to place my tests alongside the file under test. Here's why.

Firstly, I find it makes importing easier because the paths are trivial to work with. Since the test and the file under test are on the same path, imports are clean. It's always. `/file` under test. Sure beats managing a lot of `../../..` to reference some source code folder that's in a totally different spot.

Second, it provides clear visibility to our tests. They're not buried in a separate folder. They're right there in our source. So it's quite easy to notice file that lacks a corresponding test file. Again, to me, test file visibility is an asset, not a liability.

Third, placing them together makes it easy to open them both at the same time. If you open a file to write code, you should probably be writing some tests at the same time. So co-locating files that you work on at the same time just makes sense. Co-location also avoids having to maintain two separate directory structures. When you separate tests from your source, you often end up having to create new folders with the same name in two different places.

Finally, it's more convenient when we refactor and move files as well. When tests are centralized, moving the file under tests requires updating the path in a corresponding test file. When tests are placed alongside the file under test, it's easy to simply drag both files to their new location without making a path change. The relative paths remain the same. This is a minor side note, but I was also curious about the naming conventions people are using for naming JavaScript files. As you can see, naming test files with a suffix of `.spec` and `.test` are both very popular conventions.

Ollie-UI uses the `*.test.js` convention.

Okay, one final decision to make regarding testing. When should our tests run?

Well, if we're talking about unit tests, the answer is simple. Unit tests should run every time that you hit save. This rapid feedback loop assures that you're notified immediately of any regressions. And running tests each time you hit save facilitates test-driven development, since you can quickly see your tests go from red to green just by hitting control S.

If you run your tests manually, it creates unnecessary friction. When the test suite is run manually, it's easy to forget to run the test suite after making a change, so make it automatic and reduce friction.

Finally, running tests on save increases the visibility of the tests that do exist. It helps to keep testing at the forefront of your mind, so I believe this is an easy decision. Your unit tests should run automatically when you hit save.

I know what you're thinking, but I can't run my test suite every time I hit save, that'll be way too slow. Well, I should emphasize. I'm talking about unit tests here. Unit tests should run extremely fast. Integration tests are also useful and admittedly slower, so you'll want to run those separately.

But your unit tests should be fast because they shouldn't hit external resources. Now let me back up for a moment and clarify the difference between unit tests and integration tests.

Unit testing is about testing a single small unit of code in isolation.
Integration testing is about testing the integration of multiple items.

So unit testing often involves testing a single function all by itself while integration testing often means firing up a browser and clicking on the real UI using an automation tool like Selenium and often making actual calls to a web API, though you can, of course, write integration tests using just Node and JSDOM, for instance. And since unit tests seek to test a small portion of code in isolation, they run extremely quickly, quick enough that you should be able to run all your unit tests every time that you hit save.

In contrast, integration tests are slower because they often require real external resources like browsers, web APIs, and databases, which take much longer to spin up and respond than native function calls. Now since unit tests run fast, they should be run every time you hit save, and if your unit tests don't run fast enough to rerun every time that you hit save, that's often a sign that they're not really unit tests. But since integration tests typically interact with slow external resources, they're often run on-demand or in QA.

In summary, the answer to when your tests should run comes down to whether you're writing unit tests or integration tests. The majority of tests in Ollie-UI are unit tests, so the config is setup to run tests every time that we hit save.