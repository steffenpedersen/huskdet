# Filtering

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
