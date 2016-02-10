# Tools - HockeyApp

[HockeyApp](http://hockeyapp.net) is a web service used to distribute beta versions,
collect live crash reports, get feedback from real users and analyze test coverage
for mobile applications.

## Exception documentation process

In order to capture and use all of the information gained from the HockeyApp crash
reports, follow these steps upon notification:

1. Create a Pivotal bug story for the issue.
1. Add details to the bug story with a summary, context, and a URL to the HockeyApp
   crash group.
1. Finally annotate the HockeyApp crash group with a link to the Pivotal bug.
1. After the bug is fixed, the fix is destributed and the Pivotal story
   is delivered, mark the HockeyApp crash group as complete.
