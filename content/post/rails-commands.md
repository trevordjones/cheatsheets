+++
date = "2016-08-02T17:26:43-04:00"
draft = false
title = "Rails Commands"

+++

Anything below surrounded in ** is to be replaced with your own custom words!

To create a new rails project

```bash
rails new *name-of-your-app* --database=postgresql

# Don’t forget that to work with your app, you need to be in the correct directory! So, do:
cd *name-of-your-app*

#To create your postgres database:
rake db:create

# To run your rails app (also known as the webserver):
rails server # or rails s

#NOTE: Once your rails server is running, you will no longer be able to run commands from that terminal tab - it is being hogged by the rails server. You must create a new terminal tab (Command + T) and run your terminal commands from there.

#To create a new controller: (the name of your controller must be PLURAL!)
rails generate controller *name-of-your-controllers*
# Example: rails generate controller recipes

#To create a new model: (the name of your model must be SINGULAR!)
rails generate model *ModelName* attribute_1 attribute_2 attribute_3 ..etc…
#Example: rails generate model Recipe title chef prep_time:integer

# After creating each model, you must enter run
rake db:migrate

#To run your rails console:
rails console # or rails c
```
