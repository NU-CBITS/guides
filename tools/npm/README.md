# Tools - npm

[npm](https://www.npmjs.com/) is ostensibly just a package manager for
[node](https://nodejs.org/) and [io.js](https://iojs.org/en/index.html). It is
also a powerful build tool.

## Package installation

There is a lot of documentation that suggests installing packages globablly, but
this is almost never required. Packages **should** be installed locally within
projects whenever possible. This will simplify dependency management. The
package scripts will be installed within the `node_modules/.bin` directory and
can be run from there.

`node_modules` **must** be added to the `.gitignore` file, and dependencies
**must** be included in the `package.json` file.

For example instead of installing Cordova glabally, it can be installed within
a project and used the same way.

```
cd my_project
npm install cordova
./node_modules/.bin/cordova add platform ios
```

## `core-util-is` error

The following error may appear from time to time
when using node v0.12.X and Homebrew:

```
module.js:338
    throw err;
          ^
Error: Cannot find module 'core-util-is'
    at Function.Module._resolveFilename (module.js:336:15)
    at Function.Module._load (module.js:278:25)
    at Module.require (module.js:365:17)
    at require (module.js:384:17)
    at Object.<anonymous> (/usr/local/lib/node_modules/npm/node
        _modules/readable-stream/lib/_stream_readable.js:41:12)
    at Module._compile (module.js:460:26)
    at Object.Module._extensions..js (module.js:478:10)
    at Module.load (module.js:355:32)
    at Function.Module._load (module.js:310:12)
    at Module.require (module.js:365:17)
```

If you recieve this error, first attempt to delete your local copy of the
repo in question and re-clone it. If that does not work,
complete the following steps:

```
brew rm --force node012
```

```
brew install node012
```

```
sudo chown -R <user> /usr/local/lib/node_modules
```

If you are still receiving an error, redo the first two steps.

If running a Cordova hybrid app, make sure to
create a www directory at the top level of the repo:

```
mkdir www
```

Once all seems to be going well, follow the repo specific instructions.


