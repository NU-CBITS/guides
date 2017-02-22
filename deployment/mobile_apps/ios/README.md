# Deployment - Mobile Apps - iOS

**NOTE**: This assumes you are using Ionic 2 but should translate pretty well
for any Cordova project. It also assumes you have Xcode set up appropriately
and that you have the login credentials for an Apple ID.

**ALSO NOTE**: This was written on my second build. It is mostly the same as my
first build but there may be some differences. Do not take this as gospel and
check for errors, etc at each step.

I dropped and add the platform each time. You may not need to but I wasn't
messing with it.

```
ionic platform rm ios
ionic platform add ios
STAGE=staging ionic build ios
```

(*NOTE*: The set up for stages may be different for your project and you may
prefer to use the --prod flag)

The last step will likely fail and you will see the following error. (*NOTE*: I
am pretty sure this can be gotten around by using a `build.json` but I'm not
sure how far that will get you)

```
=== BUILD TARGET CAR-OLT OF PROJECT CAR-OLT WITH CONFIGURATION Debug ===


Check dependencies

Signing for "CAR-OLT" requires a development team. Select a development team in
the project editor.

Code signing is required for product type 'Application' in SDK 'iOS 10.2'



** ARCHIVE FAILED **


The following build commands failed:

  Check dependencies
(1 failure)

Error: Error code 65 for command: xcodebuild with args: -xcconfig,/Users/Chris/Work/carolt_app/platforms/ios/cordova/build-debug.xcconfig,-workspace,CAR-OLT.xcworkspace,-scheme,CAR-OLT,-configuration,Debug,-destination,generic/platform=iOS,-archivePath,CAR-OLT.xcarchive,archive,CONFIGURATION_BUILD_DIR=/Users/Chris/Work/carolt_app/platforms/ios/build/device,SHARED_PRECOMPS_DIR=/Users/Chris/Work/carolt_app/platforms/ios/build/sharedpch
```

1. Open Xcode
1. Open your project. It should be in `/path/to/ionic/project/platforms/ios/`
   and end with the file extension `.xcodeproj`
1. In upper left, set device to 'Generic iOS Device',
1. Under *Xcode > Preferences > Accounts*, add or select the Apple ID used for
   provisioning and signing.
   Select View Details, download or confirm downloaded provisioning profile
1. Select Done
1. Close Preferences
1. Go to <https://developer.apple.com/account/ios/certificate>.
  * Check to make sure a cert is there for your computer
  * Under *Devices*, add devices for testing
  * Under *Provisioning Profiles > Development*, create a new provisioning profile
  * Under *Provisioning Profiles > Distribution*, create a new provisioning profile

1. Go back to Xcode and select project in left tool bar

  (*NOTE*: The next set of directions are derived from
  <http://stackoverflow.com/a/39498874/6731497>. These I repeated just about
  every time I rebuilt the app and either ran it on the device/simulator or
  archived it for distribution. Some steps may be unnecessary but I am unsure
  which.)

1. Under *General > Signing > Team* select the Apple ID used for provisioning
   and signing.
1. In main toolbar at top, select *Product > Archive*. This will likely fail.
   If it doesn't, lucky you, skip to item 18. Otherwise you should see this:

   ```
   CAR-OLT has conflicting provisioning settings. CAR-OLT is automatically
   signed for development, but a conflicting code signing identity iPhone
   Distribution has been manually specified. Set the code signing identity value
   to "iPhone Developer" in the build settings editor, or switch to manual
   signing in the project editor.
   Code signing is required for product type 'Application' in SDK 'iOS 10.2'
   ```

1. Select project in left tool bar
1. Under *General > Signing*, deselect 'Automatically manage signing'
1. Under *Signing (Debug)*, select the development provisioning profile you
   created earlier
1. Under *Signing (Release)*, select the distribution provisioning profile you
   created earlier
1. Go to *Build Settings > Signing* and confirm *Development Team* is the Apple
   ID used above and *Provisioning Profiles* are correct
1. Quit Xcode
1. Reopen Xcode
1. Under *General > Signing*, select 'Automatically manage signing'

  (*NOTE*: It is possible that the correct sequence for items 8 through 17 is to
  only implement 11 through 14 [skipping 8 through 10 and 15 through 17].
  However, this is how got things working so I am not sure if that will do it.)

1. In the main toolbar, select *Product > Archive*.
1. Select 'Export'
1. Select 'Save for Ad Hoc Deployment' and select 'Next'
1. Select the Apple ID used above and select 'Next'. (*NOTE*: first time around
   I had an error here and needed to select 'Reset' and try again.)
1. Select 'Next'

This should add a folder to your project with the `.ipa` in it.
