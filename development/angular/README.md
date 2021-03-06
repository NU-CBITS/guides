# Development - AngularJS

**Note**: this document is deprecated. It refers to Angular 1.x development. It
needs to be updated for Angular 2.x development. For the time being, refer to
the official
[Angular 2 style guide](https://angular.io/docs/ts/latest/guide/style-guide.html).

All source code **must** be located in the `/src` folder.

All files **must** define a single module, e.g. a service, directive,
controller. All file names **must** be CamelCased according to the module
contained therein.

```
/src
  /Application.js
  /controllers
    /TheController.js
    /OtherController.js
  /services
    /Red.js
    /Yellow.js
    /Blue.js
```

## Application.js

The Application.js file should configure `$routeProvider` route definitions.
When using `$routeProvider` route definitions **must** use the `controllerAs` argument.

## Controllers

JavaScript "classes" and non-Angular-specific code are always preferable
to the alternative. With this in mind, all controllers **must** follow the alias
pattern. E.g. references to controllers in views should follow the `controllerAs`
argument defined in the Application.js file.

Example

```javascript
function TheController() {}

TheController.prototype.method1 = function() { ... };

myModule.controller('TheController', TheController);
```

## Services/Factories

Unless there is a reason that a Service must be used, Factories **should**
always be favored over Services. This removes any temptation to write code that
expects to always receive a particular object instance.

```javascript
var myApp = angular.module('myApp', []);

// factory, PREFERRED
myApp.factory('helloWorldFromFactory', function() {
  return {
    sayHello: function() {
      return "Hello, World!"
    }
  };
});

// service, NOT PREFERRED
myApp.service('helloWorldFromService', function() {
  this.sayHello = function() {
    return "Hello, World!"
  };
});
```
