# Testing - RSpec

Thanks to the
[ReachLocal rspec-style-guide](https://github.com/reachlocal/rspec-style-guide)
and [HowAboutWe rspec-style-guide](https://github.com/howaboutwe/rspec-style-guide)
 for inspiration.

The intent of this guide is to improve the composition of RSpec examples
within our group so that we have clean, maintainable code that is consistent
not only within our group but also consistent with recommended practices outside
of our group. Some of this guide will be based on an ideal that should be
striven for even if it is not always obtained.

## This guide will change

As new things change within the RSpec world as well as new examples for rules
come up, this document will change to reflect these. If you have anything to
add, please do not hesitate to submit a pull-request.

## RSpec Style Guide

### Line returns

Do not leave a line return after `describe`, `context`, or `feature`.

Leave a line return after `let`, `subject`, and `before` / `after` blocks.

Group `let` and `subject` blocks and separate them from `before` / `after`
blocks.

Leave a line return around `it` blocks.

### Use `before` instead of `before(:each)`

There is no need to specify (:each) as it is the default for `before` / `after`
blocks.

### Naming conventions

* Top level: use `describe` with a constant name: `describe User ...`

* 2nd level: use `describe` with a method name: `describe "#awesome?"`

* Inner blocks: use a `context` that starts with "when":

`context "when user is unsubscribed"`

* Example describes the expectation: `it "is false"`

In `describe` blocks use "#" for instance methods and "." for class methods.

`context` should always have an opposite case. A single `context` without a
matching negative case may need to be refactored.

Do not use "should" or "should not" in `it` statements, descriptions represent
actual functionality not what may happen.

### One Expectation

Try to only use one expectation per example, within reason.

### `it` in iterators

Do not write iterators to generate tests.

### Always use Timecop when dealing with time

The rails_helper should contain a `FIXED_TIMEPOINT` and a
`before(:suite)` and `after(:suite)` to set and return that time point.
Any example with time should relate to that fixed time point.

`FIXED_TIMEPOINT = Time.local(2020, 9, 1, 10, 5, 0)`

```ruby
RSpec.configure do |config|
  config.before :suite do
    Timecop.travel FIXED_TIMEPOINT
  end

  config.after :suite do
    Timecop.return
  end
end
```

### Use `let` blocks instead of `before` blocks to create data

`let` blocks get lazily evaluated

### Avoid using incidental state

Bad Example

```ruby
it 'publishes the article' do
  article.publish

  # Creating another shared Article test object above would cause this
  # test to break
  expect(Article.count).to eq(2)
end
```

Good Example

```ruby
it 'publishes the article' do
  expect { article.publish }.to change(Article, :count).by(1)
end
```

### Fixtures for data

### Mocking and Stubbing

### Views

### Controllers

### Models

### Mailers

### Rake Tasks


