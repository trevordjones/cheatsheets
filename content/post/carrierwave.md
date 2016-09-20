+++
date = "2016-09-20T10:23:48-04:00"
draft = false
title = "Carrierwave to Upload Images"

+++

* Add gem to Gemfile

    ```ruby
    gem 'carrierwave'
    ```
* Bundle it up
* `rails generate uploader RecipePhoto`
* The above command will create a file in your `app/uploaders` directory. It will contain a class called `RecipePhotoUploader`
* In your terminal, run `rails g migration AddPhotoToRecipe photo`
* Then `rake db:migrate`
* In your model (Recipe in this case), add
```ruby
mount_uploader :photo, RecipePhotoUploader
# this connects the RecipePhotoUploader we generated to the photo column in the recipe model.
```
* Create the form. To get this to work with `form_tag`, use the following format:
```ruby
  <%= form_tag("/recipes/#{@recipe.id}", method: 'patch', enctype: "multipart/form-data") do %>
      <%= label_tag(:photo) %>
      <%= file_field_tag(:photo) %>
      # Whatever else needs to be included
      <%= submit_tag("Save") %>
    <% end %>

    # Important part is the enctype: "multipart/form-data"
```

* In your controller:
```ruby
  def update
      recipe = Recipe.find_by(id: params[:id])
      recipe.update(
        photo: params[:photo]
        # whatever else you want updated
      )
      redirect_to "/recipes/#{@recipe.id}"
  end
```
* You can display the photo in your view with:
```ruby
<%= image_tag(@recipe.photo.url) %>
```
