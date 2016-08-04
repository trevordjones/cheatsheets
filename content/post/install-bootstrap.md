+++
date = "2016-08-02T17:26:29-04:00"
draft = false
title = "Install Bootstrap"

+++

1. Add ‘bootstrap-sass’ anywhere in your Gemfile.

2. Inside your terminal (make sure you’re in the folder where your Rails app is), run: bundle

3. Inside `app/assets/stylesheets`, create a new file called `_external.css.scss`

4. Add these lines to that file:
```css
@import "bootstrap-sprockets";
@import "bootstrap";
```
5. Inside `app/assets/javascripts/application.js`, add this line under the line that says `//=require jquery`
```javascript
//= require bootstrap-sprockets
```
6. If your rails server was already running, restart it.
