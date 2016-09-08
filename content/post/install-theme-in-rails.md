+++
date = "2016-09-07T17:45:32-04:00"
draft = false
title = "Install Theme in Rails"

+++

### Tips
1. Read their README - many will have one but perhaps not every single one. The README is usually the `index.html` file you see in the theme's parent directory. If you double click on it, it should open up in the browser.
2. Look through what is required for the theme. It will most likely show you what css files are necessary and which are not.
3. Look through the `index.html` file to see their `link` tags for stylesheets. This will also tell you which ones they are using.
4. You will not need to include their bootstrap.css file - use the gem to use Bootstrap.
5. If they are using Font Awesome, you will also not have to include that. Use the `font-awesome-rails` gem instead.
6. Check to see if they have classes/ids on their `<body>` tag. This is true for anything though - make sure class and id names are matching up with what they have.

## Integrate into your App

### CSS
1. Copy over all the css files into `vendor/assets/stylesheets`
2. Create a `manifest.css` file in the same directory and place the following within it.

    ```css
    /*
    *= require_tree .
    */
    ```
This will require all the files in `vendor/assets/stylesheets`.
3. Now inside your `app/assets/stylesheets/application.css` file add `*= require manifest` *before* `require_tree .`.
4. Go to your theme's `index.html` file and copy the top nav elements from it. This file will normally have comments telling you which sections are which, so simply look for the section that outlines your top nav. Paste this into your `application.html.erb` file right below the `<body>` tag and *before* the `yield` method.
5. Also include the footer section from the `index.html` file. Copy and paste it *below* the `yield` method in the `application.html.erb` file but before the closing `</body>` tag.
6. Inside your `application.html.erb` file will be html you want included on every page in your site. This is why we only did the nav and the footer. If there is anything else you want to appear on every page - include it inside this `application.html.erb` file.

### JavaScript
1. You can do much the same thing with JavaScript. Include all their necessary JS files into `vendor/assets/javascripts`.
2. You will not need their jQuery file since it's included with Rails by default (be careful with this though. Your theme may be using a different version of jQuery that has breaking changes with Rails version of jQuery. Be aware of that.)
3. Create the `manifest.js` file and include:

    ```javascript
    // require_tree .
    ```
4. Now inside `app/assets/javascripts/application.js` include `//require manifest`
5. Check your console for JS errors

### JS Tips
Sometimes the JS will be looking for elements that have not been created yet. That is because the code to include JS into your html is towards the top of the page and can run before the rest of the html is rendered. So if it's looking for an id of "main" (which is in your html) and can't find it - it's running before that particular bit of html is created.

To solve this, simply move the `<%= javascript_include_tag 'application', 'data-turbolinks-track': 'reload' %>` to be below the closing `</body>` tag. This will ensure the JS doesn't run before the page is loaded.

Check your console for JS errors. It should tell you where there are problems if any.

### Images
1. Copy images you want to use to your `app/assets/images` directory.
2. When you want to use these inside your html, you can

    ```html
    <%= image_tag('image_name.png') %>
    ```
This will convert to `<img src="/assets/images/image_name.png" alt="">`. This is the preferred way in Rails to include your images.
