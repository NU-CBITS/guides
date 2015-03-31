# Testing - Appium

## Purpose

Appium is most useful for running acceptance tests against web and mobile hybrid
applications. These tests can be challenging to write and maintain, and so
should not be used to cover all branches and edge cases.

## Overview

Appium itself is a server that accepts commands from various clients and
translates those commands to drive an application.

## Clients

### JavaScript

The [wd](https://github.com/admc/wd) library implements [a set of WebDriver API
methods](https://github.com/admc/wd/blob/f49065fa8ff91411f70972f149e90b7f97f4cd39/doc/api.md).
These methods are all asynchronous, and can be used with a traditional "pyramid"
callback style or, for example, with a promises implementation such as
[chai-as-promised](https://github.com/domenic/chai-as-promised/).

[mocha](https://github.com/mochajs/mocha) and [chai](https://github.com/chaijs/chai)
can be paired as the test runner and assertion library for use with `wd`.
