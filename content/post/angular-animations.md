+++
date = "2016-09-08T17:44:30-04:00"
draft = true
title = "Angular Animations"

+++

* Copy animate.css from [here](https://raw.githubusercontent.com/daneden/animate.css/master/animate.css)
* Save it in vendor/assets/stylesheets as animate.css
* Require it in asset pipeline (app/assets/stylesheets/application.scss) as follows:
* `*= require animate`
* Download angular-animate.js from [here](https://code.angularjs.org/1.4.3/angular-animate.js)
* Save it in `vendor/assets/javascripts` and require it in asset pipeline
`//= require angular-animate` NOTE: make sure this goes before require app!
* Include the animate module in app.js:
```javascript
angular.module("app", ["ngAnimate"]);
```
* Add this css to your stylesheets:
		https://gist.github.com/jaywengrow/10b5d650c740d1b40188
Choose your own animation from the choices in animate.css. See all choices here: http://daneden.github.io/animate.css
