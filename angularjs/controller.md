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

