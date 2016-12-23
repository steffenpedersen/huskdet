# **Directives \(ng-directives\)**

## **ngModel**

The `ngModel` directive binds an input, select, textarea \(or custom form control\) to a property on the scope.

```
<label>Name:</label>
<input ng-model="yourName" type="text" placeholder="Enter a name here">
<h1>Hello {{yourName}}!</h1>
```

![](/assets/dec.-23-2016 21-03-49.gif)

## **ng-repeat**

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

