# Controller

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

