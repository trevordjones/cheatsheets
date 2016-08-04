+++
date = "2016-08-02T17:26:15-04:00"
draft = false
title = "Migrations"

+++

**To create a database:**  

```bash
rake db:create
# Note: you only need to do this once per app
```

**To create a new table in the database:**
```bash
rails generate model Product name:string description:text 'price:decimal{5,2}'
# DOUBLE CHECK THE GENERATED MIGRATION FILE CODE (in db/migrate folder)
# If there are typos, you can fix them now before doing the next step

rake db:migrate
```
Note: A description of rails database types can be found [here](http://stackoverflow.com/questions/11889048/is-there-documentation-for-the-rails-column-types).

**To make changes to existing database tables:**
```bash
rails generate migration NameDescribingTheChange
```
Add code to the new migration file generated in the db/migrate folder.  
All available commands here: http://api.rubyonrails.org/classes/ActiveRecord/Migration.html  
```ruby
# Add a column
add_column :products, :image, :string

# Rename a column:
rename_column :products, :image, :photo
# In this example, image is the old name, photo is the new name

# Remove a column:
remove_column :products, :photo, :string

# Change a data type:
change_column :products, :quantity, :integer
# In this example, quantity will become an integer

# Using decimals:
add_column :products, :price, :decimal, precision: 5, scale: 2
# Precision is the total number of digits, scale is the number of digits after the decimal
# In this example, 103.42 is a valid price, 3432.21 is invalid (total digits is greater than precision)

# NOTE: postgres is a bit touchy changing strings to decimals, use these two lines in a migration:
change_column :products, :price, "numeric USING CAST(price AS numeric)"
change_column :products, :price, :decimal, precision: 9, scale: 2
```
DOUBLE CHECK YOUR MIGRATION FILE CODE  
If there are typos, you can fix them now before doing the next step
```bash
rake db:migrate
```
**Shortcuts for the above:**   
```bash
# To add a column to a table:
rails generate migration AddImageToProducts image:string

# To remove a column from a table:
rails generate migration RemovePhotoFromProducts photo:string
```
No other shortcuts exist - if you need to rename, change, etc., you’ll need to generate an empty migration file and write the code in as described above

**To generate sample data for database:**  
Write code in the `db/seeds.rb` file (instead of through the rails console)
```bash
rake db:seed
```
Note: If you already have sample data created from rails console or your application, you can use this gem to generate a seed file so others can reproduce it: https://github.com/rroblak/seed_dump
