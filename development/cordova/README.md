# Development - Cordova

Note: these instructions assume you are building an Angular 1.4 based
application.

To begin a Cordova 5 project, start with a `package.json` file. It is best
practice to install dependencies within a project rather than globally, which is
why you shouldn't follow the [Cordova instructions](http://cordova.apache.org/docs/en/latest/guide/cli/index.html)
to the letter.

```
$ echo "{}" > package.json
$ npm install --save angular@1.4.7 angular-resource@1.4.7 angular-route@1.4.7 \
> cordova@5.4.1 moment@2.10.3
$ npm install --save-dev angular-mocks@1.4.7 appium@1.4.3 chai@3.0.0 \
> chai-as-promised@5.1.0 eslint@0.23.0 mocha@2.2.5 sinon@1.15.3 testem@0.8.3 \
> wd@0.3.12
```

Create the Cordova application. Cordova doesn't like you to install into an
existing directory, so this process gets around that.

```
$ ./node_modules/.bin/cordova create tmp edu.northwestern.cbits.project_name AppDisplayTitle
Creating a new cordova project.
$ mv tmp/* .; rmdir tmp
$
```

[View this example](../../examples/cordova) to get an idea of how to structure
the Angular app within Cordova.

## Plugins

As with other forms of dependency management, it is best practice to specify the
semantic version (or approximate version) that the application has been built
with to aid others in building it.

One way of locking down versions is to store them in the `config.xml` file.
Cordova CLI provides an easy way to do this. For example, if you want to install
and lock to the latest version of `cordova-plugin-device`, you would use the
command:

```
$ ./node_modules/.bin/cordova plugin add cordova-plugin-device --save --shrinkwrap
Fetching plugin "cordova-plugin-device@~1.1.0" via npm
Installing "cordova-plugin-device" for android
Saved plugin info for "cordova-plugin-device" to config.xml
```

It will install the plugin and add an extra line of configuration to the end of
the `config.xml` file:

```
<plugin name="cordova-plugin-device" spec="~1.1.0" />
```

## Angular 1.x

The standard approach to bootstrapping your Angular 1.x application is
automatically.

```html
<body ng-app="MyAngularAppModule">
```

**Don't do this in Cordova!** You should always use the
[manual bootstrap](https://docs.angularjs.org/api/ng/function/angular.bootstrap)
method.

## HockeyApp

[HockeyApp](https://rink.hockeyapp.net) can be configured to report crashes
(unhandled native exceptions). A couple of steps are necessary.

### Add the HockeyAppSDK as a dependency to the build process

Edit the `build.gradle` file to include the following entry under `dependencies`

```
dependencies {
    ...
    compile 'net.hockeyapp.android:HockeySDK:3.7.0'
}
```

### Modify the MainActivity.java file

```
...
import net.hockeyapp.android.CrashManager;
...
public class MainActivity extends CordovaActivity
{
    private static String APP_ID = "app-id-provided-by-HockeyApp";

    ...

    @Override
    protected void onResume() {
        super.onResume();
        checkForCrashes();
    }

    private void checkForCrashes() {
        CrashManager.register(this, APP_ID);
    }
}
```
