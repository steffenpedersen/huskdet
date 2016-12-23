# AngularJS 1.x

AngularJS is a JavaScript framework which extends HTML attributes with Directives, and binds data to HTML with Expressions.

service

![](/assets/9903c7c14add3fd0758b7b5b80c24d48101f296f13ce34736799a82c71f61bc2.jpg)

## **Directives \(ng-directives\)**

**ngModel**

The `ngModel` directive binds an input, select, textarea \(or custom form control\) to a property on the scope.

```
<label>Name:</label>
<input ng-model="yourName" type="text" placeholder="Enter a name here">
<h1>Hello {{yourName}}!</h1>
```

![](/assets/dec.-23-2016 21-03-49.gif)

**ng-repeat**

```
function UsersCtrl($scope) {
    $scope.users = [{name: "Jonh", age: 21}, {name: "Alice", age: 29}];
}
```

```
<div ng-controller="UsersCtrl">
    <ul>
        <li ng-repeat="user in users">
            Name: {{user.name}}, {{user.age}} years old.
        </li>
    </ul>
<div>
```

![](/assets/Skærmbillede 2016-12-23 kl. 21.18.05.png)

## Controller

**Binding Events To Controller**

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


## Component



## Filtering

```
function UsersCtrl($scope) {
    $scope.users = [
        { name: "Camila Gilson" },
        { name: "Chloe Creighton" },
        { name: "Zoey White" },
        { name: "Claire Campbell" },
        { name: "Kylie Smith" },
        { name: "Charlotte Gilson" }
    ];
    
    $scope.title = 'User list';
}
```

```
<div ng-controller="UsersCtrl">
    <h1>{{title}}</h1>
    Search: <input ng-model="search">
    <ul>
        <li ng-repeat="user in users | filter: search">
            {{user.name}}
        </li>
    </ul>
</div>
```

![](/assets/dec.-23-2016 21-27-42.gif)

## $scope

$scope is special object designed to allow communication between controller and the view.

```
function ExampleCtrl($scope) {
    $scope.value = "This is the value";
}
```

```
    <div ng-controller="ExampleCtrl">
        <input ng-model="value"><br>
     {{value}}
</div>
<div ng-controller="ExampleCtrl">
    <input ng-model="value"><br>
    {{value}}
</div>
```

![](/assets/Skærmbillede 2016-12-23 kl. 21.19.32.png)

## John Papa: Angular Style Guide



