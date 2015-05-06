# Testing - Selenium - Selenium IDE

## Purpose

The Selenium-IDE is a Firefox add-on that allows you to record interactions
with the browser that you can later play back. It is best used for quick
testing, such as bug reproduction. See
[Selenium IDE](http://www.seleniumhq.org/projects/ide) for more information.

## Set up

### Download and install the plugin

* Download [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* Open Firefox, download Selenium IDE plugin for Firefox:
  release.seleniumhq.org/selenium-ide/2.9.0/selenium-ide-2.9.0.xpi
  * Install the add-ons and restart the browser.
* I suggest adding [Power Debugger (Selenium IDE)](https://addons.mozilla.org/en-us/firefox/addon/power-debugger-selenium-ide/)
  * this adds a pause on fail button which is extremely useful

### Using the plugin

* Open Firefox
* Click the Selenium icon in the toolbar
  * A window should pop up - this is the IDE

### Features of the IDE

* At the top of the window you should see the "Base URL" input. Here you will
  put the base url for the application / webpage you are testing.
* Below the Base URL input is the toolbar. On the left side is the controls
  for playback. These include (but are not limited to - certain plugins will
  add buttons here), from left to right playback speed toggle, "Play entire
  test suite", "Play current test case", "Pause / Resume", "Step", and "Apply
  rollup rules". On the right side is "Turn test scheduler on/off" and "Click
  to Record"
  * With the playback speed toggle, you can toggle the speed at which you
    want to run the playback
    * **NOTE:** It is usually best to keep the playback pretty slow as fast
      playback may give you some false-negatives
  * If you added Power Debugger (Selenium IDE), you will see the "Pause on
    fail" button next.
    * **NOTE:** If you have multiple tests or test cases that have many
      actions that can fail, you will want to turn this on as the IDE will
      continue past failures until it has reached the end of all test cases.
  * "Play entire test suite" - plays all test cases open
    * **NOTE:** Be careful when running the entire test suite as you may get
      false negatives if test cases are dependent upon each other or were
      recorded independently of each other.
  * "Play current test case" - highly recommended, plays the test case you have
    highlighted
  * "Pause / Resume" - useful in debugging
  * "Step" - can be very useful in debugging after the test has paused,
    basically it just steps through the actions
  * "Apply rollup rules" - allows repetitive sequence of actions to be grouped
    into a single action.
  * "Turn test scheduler on/off"
  * "Click to Record"
* Below the toolbar is the "Test Case" window.
  * This displays all the test cases open. If you select "Play entire test
    suite" it will run through each of these test cases until it reaches the
    end, whether there is a failure or not. Test cases that have **no**
    failures will be highlighted in green after the run, those with **any**
    failures will be highlighted in red.
* Next to the "Test Case" window is the "Table / Source" window.
  * In the "Table" view you will see each action that you recorded. When you
    play it back you will see the IDE run through each action. Actions that
    do no fail will be highlighted in green, those that do fail will be
    highlighted in red.
    * You can update the action by highlighting it and using the drop downs
       / inputs below this window.
      * The "Command" drop down allows you to choose the command or action
        from a list of **all** possible actions.
      * The "Target" is the option(s) for your "Command".
      * The "Value" is the value you are expecting (if you have one for this)
        particular action).
  * The "Source" view shows the source code for the test case. By default this
    is in html.
* At the bottom of the window are some views that you may find helpful.
  * "Log"
    * This shows the log of the current run of the test case/suite. Error
      messages and failure messages can be found here.
  * "Reference"
    * This shows documentation and information specific to an action you have
      highlighted.
  * "UI-Element"
    * Allows you to define a mapping between semantically meaningful names of
      elements and the elements themselves. The mapping is defined using JSON.
      * For more information, see UI-Element Documentation in the Help Menu of
        the IDE.
  * "Rollup"
    * Rules for rollup - grouping repetitive actions into a single action
      * For more information, see UI-Element Documentation in the Help Menu of
        the IDE.

* Some other useful features that are not immediately apparent
  * "Export Test Case As"
    * under File > Export Test Case As... you export a test case in your
      favorite language
    * **NOTE:** Do not confuse this with "Export Test Suite As..." which will
      only export the script for running the test suite - all your test cases
      will be referred to by their filenames