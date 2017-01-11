# Modules

Modules are used to fully encapsulate all the angular code of your application into one entry point. **Also discrete parts** of your application can be separated into distinct parts which can be loaded and executed in different order.

```js
<!--- Set this as the HTML tag in your application -->
<html data-ng-app="YOUR_APP_NAME">
```

Next, include a new javascript file into your website and set this code:

```js
var App = angular.module('YOUR_APP_NAME', ['ngResource']);
```

This will create a global module for your app where you can create routes, models, filters and directives. The **App **variable is accessible throughout your application and the **\['ngResource'\] **definition array defines all the other modules and dependencies that must be loaded prior to this module being activated.



