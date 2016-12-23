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
