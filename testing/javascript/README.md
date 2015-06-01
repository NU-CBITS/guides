# Testing - JavaScript

## Mocha and Chai

[Mocha](https://github.com/mochajs/mocha) is a test framework for server side
(Node.js/io.js) code as well as browser code.
[Chai](https://github.com/chaijs/chai) is an assertion library that allows for
writing tests in various styles. There are numerous plugins such as
[Chai as Promised](https://github.com/domenic/chai-as-promised/), that add
syntactic sugar.

## Sinon

[Sinon](http://sinonjs.org/) is a versatile library for stubbing, mocking and
spying. It can spy on existing functions as well as generate stub and mock
functions. It can mock HTTP responses as well as the current date.

## Blanket.js

[Blanket.js](https://github.com/alex-seville/blanket) is a simple, lightweight
code coverage library that runs in the browser. It can be configured for use
with Test'em and Mocha. You must include
[blanket.min.js](https://raw.github.com/alex-seville/blanket/master/dist/qunit/blanket.min.js)
and
[mocha-blanket.js](https://raw.githubusercontent.com/alex-seville/blanket/master/src/adapters/mocha-blanket.js).

```html
// test.html
<html>
  <head>
    <link rel="stylesheet" href="/testem/mocha.css">
    <script src="/testem/mocha.js"></script>
    <script src="/testem/chai.js"></script>
    <script src="/testem.js"></script>
    <script>mocha.setup('bdd')</script>

    <script src="support/blanket.min.js"></script>
    <script src="support/mocha-blanket.js"></script>

    <script data-cover src="MyClass.js"></script>

    <script src="myTest.js"></script>
  </head>

  <body>
    <div id="mocha"></div>
    <script>
      mocha.run()
    </script>
  </body>
</html>
```

Note the `data-cover` attribute in the script tag. This tells Blanket.js to
instrument and report on that code.

```yaml
# .testem.yml
framework: mocha+chai
launch_in_dev:
  - Chrome
test_page: test.html
```

### Gotchas

Due to the dynamic wrapping of code that Blanket.js does to instrument it, you
will have to disable it to set breakpoints and step through code for debugging
in the browser.

## Test'em

[Test'em](https://github.com/airportyh/testem) is a tool for running tests in
various environments and reporting the results. It can run tests in various
browsers with UIs as well as headless browsers such as PhantomJS. It can also
be configured to run tests in CI environments.
