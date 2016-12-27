# Controller

You can have multiple controllers on your site. Each of the controller can be responsible for different parts of page. Usually each controller is kept in separate file - in this way we can easier keep order in our project. [Link](https://www.codecademy.com/en/courses/javascript-advanced-en-2hJ3J/1/1#)

```js
<article ng-controller="contentCtrl">
    <h1>{{title}}</h1>
    <hr />
    <p>{{paragraph}}</p>
    <small>by {{author}}</small>
</article>
```

```js
angular.module('exampleApp')
    .controller('contentCtrl', function ($scope) {
        $scope.title = "Lorem Ipsum";
        $scope.paragraph = "Completely myocardinate process-centric "
        + "total linkage whereas installed base e-tailers. "
        + "Proactively extend collaborative intellectual capital "
        + "vis-a-vis unique expertise. Dynamically.";
        $scope.author = "Anna Nowak";
    });
```

## Service injection

In AngularJs all relation between different pieces of code are set up using [dependency injection](http://docs.angularjs.org/guide/di). In angular you can inject services by adding them as arguments to the controller function.

For example:  
`functionsimpleCtrl($scope) {/../}` defines controller that have $scope injected into it; while `functioncomplexCtrl($scope,$http,User) {/../}` have $scope, $http and custom service named User injected.

## Routing

Usually sites have sub-pages - front page; category pages; article pages etc. With angular.js we usually implement it with

**routes**. [Link](https://www.codecademy.com/en/courses/javascript-advanced-en-2hJ3J/1/3)

To get module code we load angular-route.js file. Module is injected into our application in app.js by adding it's name ngRoute in the first line: `angular.module('routingApp', ['ngRoute'])`.

### $routeProvider

Routes are configured using[$routeProvider](https://docs.angularjs.org/api/ngRoute/provider/$routeProvider). This is special service that can be injected duringconfigphase of an application. You can take a look how it was implemented inapp.jsfile.

`$routeProvider`is an object with two methods:

* when
  - which allow us to define a route
* otherwise
  - which allow us to define default behavior.

### Api

`$routeProvider.when`takes two arguments:

* path
  - string describing what is covered by this instruction
* route
  - special object describing what should be done when route is accessed. Fields of this object means: \*\*
  controller
  - function that should be used as controller for a content of a view \*\*
  templateUrl
  - relative location of a view \*\*
  redirectTo
  - path where use should be redirected.

`$routeProvider.otherwise`takes just one argumentrouteobject the same as above

```js
angular.module('routingApp', ['ngRoute'])
    // Setting configuration for application
    .config(function ($routeProvider) {
        $routeProvider
        .when('/hello', {
            controller: helloCtrl,
            templateUrl: 'hello.html'
        })
        .when('/about', {
            controller: aboutCtrl,
            templateUrl: 'about.html'
        })
        .otherwise({
            redirectTo: '/hello'
        });
    })
```

```
<a href="#/hello">Hello</a>
<a href="#/about">About</a>
```

[Link](https://www.codecademy.com/en/courses/javascript-advanced-en-2hJ3J/1/4) for dynamic pages \(non-static\)



## **Binding Events To Controller**

We can bind view events with functions defined in controller. That allows us to keep all data and logic regarding site section in one place.

* ng-click
* ng-change
* ng-mouseenter

`ng-change="changeCallback()"`

```
function UsersCtrl($scope) {
    $scope.info = "The button haven't been clicked yet";
    $scope.click = function () {
         $scope.info = "You've cliked the button!"
    };
}
```

```
<div ng-controller="UsersCtrl">
    <p>{{info}}</p>
    <button ng-click="click()">Click me!</button>
</div>
```

![](/assets/dec.-23-2016 21-37-28.gif)

