# Testing - Selenium - Selenium WebDriver

## Purpose

Selenium WebDriver is best used for creating robust automated test suites for
web-based applications. It is a suite of tools to automate web browsers. It has
the ability to run in many browsers and operating systems and can be controlled
by many programming languages and testing frameworks. See
[Selenium WebDriver](http://www.seleniumhq.org/projects/webdriver) for more
information.

## Set up

A great place to start with Selenium is their documentation
[Selenium WebDriver Documentation](http://docs.seleniumhq.org/docs/03_webdriver.jsp).

Another good resource for Selenium Dave Haeffner's
[Elemental Selenium](http://elementalselenium.com) which is a weekly email of
Selenium tips. All of these tips are archived on the site so you do not
necessarily need to sign up for the emails. He also has a Bootcamp that you can
sign up for on this site.

### Ruby

Installing selenium in your Ruby environment is as easy as running

```
gem install selenium-webdriver
```

#### An example with Capybara

You can write your test suite using Capybara with RSpec and use Selenium as the
driver. I am running Ruby version 2.2.0. In this example, I am using the default
browser for selenium which is Firefox. You will need to have Firefox downloaded
prior to running this.

**NOTE:** Be careful of the version of Firefox you are running. I have found
that updating my Firefox has broken my tests (in fact, they just don't run at
all). Selenium versions support the latest Firefox release, the previous
release, the latest ESR release and the previous ESR release **at the time of
the release of that version of Selenium**. I run Selenium version 2.44.0 which
was released in November 2014. The version of Firefox at that time was 33.0,
therefore that is the version of Firefox I have installed and I have turned off
updates for Firefox. For Firefox releases go
[here](https://ftp.mozilla.org/pub/mozilla.org/firefox/releases/)
and for Selenium releases go
[here](https://rubygems.org/gems/selenium-webdriver/versions).

First set up your gems in your Gemfile.

```ruby
gem 'rspec', '3.1.0'
gem 'capybara', '2.4.4'
gem 'selenium-webdriver', '2.44.0'
```

Then set your requirements and configure RSpec and Capybara in your
`spec_helper.rb`.

```ruby
require 'rspec'
require 'capybara'
require 'capybara/rspec'
require 'selenium-webdriver'
```

```ruby
Capybara.default_driver = :selenium
```

Then just write your Capybara tests as normal.

```ruby
require spec_helper

describe 'A visitor to the site,', type: :feature do
  before do
    visit '/participants/sign_in'
  end

  it 'is an active participant, signs in' do
    within('#new_participant')
      fill_in 'participant_email', with: 'participant@example.com'
      fill_in 'participant_password', with: 'password'
    end
    click_on 'Sign in'
    expect(page).to have_content 'Signed in successfully.'
  end
end
```