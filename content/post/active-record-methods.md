+++
date = "2016-08-02T17:24:48-04:00"
draft = false
title = "Active Record Methods"

+++

Say you created a new model in your Rails app called “Recipe”. This is what you would type into Rails Console to edit the data table associated with the model.

```bash
recipe = Recipe.new(attribute: “input”, attribute: “input”)
recipe.save
# The first command creates a new instance of a Recipe
# The second command saves the recipe data to your database
# remember that 'recipe' is only a variable. This can be called anything

recipe = Recipe.create(attribute: “input”, attribute: “input”)
# This is a shortcut for the above two commands, it creates a new instance AND saves it to the database.

recipes = Recipe.all
# This shows all the data table entries (IN RAILS CONSOLE, if you wanted to show this information, on a view page for example, you would have to loop through this array of hashes)

recipe = Recipe.first
# This shows the first data table entry

recipe = Recipe.last
#This shows the last data table entry

recipe = Recipe.find_by(attribute: “specific value”)
# This allows you to find a data entry by a specific attribute’s value.
# EX: Recipe.find_by(chef: “Mark’s Dad”) will find the first recipe whose chef is “Mark’s Dad”

recipe = Recipe.first
recipe.attribute = “input”
recipe.save
#This allows you update an entry in your data table. Remember, you must choose which recipe you want to update first before you can use this method. In this example, we’re choosing to update the first recipe in the data table.

recipe = Recipe.first
recipe.update(attribute: “input”)
# This is a shortcut for the above commands, it changes the instance attributes AND saves it to the database.

recipe = Recipe.first
recipe.destroy
# This allows you destroy an entry in your data table. Remember, you must choose which recipe you want to destroy first before you can use this method. In this example, we’re choosing to destroy the first recipe in the data table.
```
