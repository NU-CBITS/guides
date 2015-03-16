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

For example instead of installing Cordova glabally, it can be installed within
a project and used the same way.

```
cd my_project
npm install cordova
./node_modules/.bin/cordova add platform ios
```
