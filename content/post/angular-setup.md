+++
date = "2016-09-07T12:44:51-04:00"
draft = false
title = "Angular Setup"

+++

### Setup Angular in your Rails App
1. Go to [https://angularjs.org](https://angularjs.org) and download the compressed angular.js file.
2. Copy that file into `vendor/assets/javascripts` folder.
3. Add `//= require angular` to the asset pipeline (i.e. `app/assets/javascripts/application.js`) on the line before `//= require_tree .`.
4. Get rid of the turbolinks line in that file, which can cause problems down the road.
5. Create a new file inside `app/assets/javascripts` called `app.js`.
6. Add the following:

	```javascript
	(function() {
	  "use strict";

	  angular.module("app", []);

	})();
	```

7. Back to `app/assets/javascripts/application.js`. Below `require angular` add `//= require app`. It must be below Angular.
8. Add to your html where you want to inject Angular
```html
<div ng-app="app">
  {{ 1 + 1 }}
</div>
```
9. Go to that page in the browser and see that the number 2 appears. If so, Angular is properly installed!


## Setup an Angular Controller
1. In `app/assets/javascripts/controllers` add a controller file called `test_ctrl.js`.
2. Add the following:

	```javascript
	(function () {
	  "use strict";

	  angular.module("app").controller("testCtrl", function($scope) {
	    $scope.message = "Hello!";
	  });
	})();
	```
3. Then inside your html file where you included the Angular app:

	```html
	<div ng-app="app">
	  <div ng-controller="stuffCtrl">
	    <p>{{ message }}</p>
	  </div>
	</div>
	```
4. Check in your browser that you have the "Hello!" message appearing.
