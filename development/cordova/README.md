# Development - Cordova

Note: these instructions assume you are building an Angular 1.4 based
application.

To begin a Cordova 5.0.0 project, start with a `package.json` file. It is best
practice to install dependencies within a project rather than globally, which is
why you shouldn't follow the [Cordova instructions](http://cordova.apache.org/docs/en/5.0.0/guide_cli_index.md.html#The%20Command-Line%20Interface)
to the letter.

```
$ echo "{}" > package.json
$ npm install --save angular@1.4.0 angular-resource@1.4.0 angular-route@1.4.0 \
> cordova@5.0.0 moment@2.10.2
$ npm install --save-dev angular-mocks@1.4.0 appium@1.4.0 chai@2.1.2 \
> chai-as-promised@5.0.0 eslint@0.19.0 mocha@2.2.1 sinon@1.14.1 testem@0.8.0-0 \
> wd@0.3.11
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
