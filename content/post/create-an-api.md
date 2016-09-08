+++
date = "2016-09-08T16:43:01-04:00"
draft = false
title = "Create an API"

+++

* Create brand new app `rails new name-of-api -T -d postgresql`
* `rake db:create`
* `rails g model Person first_name last_name email phone`
* `rake db:migrate`
* `rails g controller api/v1/people`
* Add [Faker gem](https://github.com/stympy/faker)
* `bundle`
* Create a seed file

    ```ruby
    100.times do
      Person.create(:prefix => Faker::Name.prefix,
                    :first_name => Faker::Name.first_name,
                    :middle_name => Faker::Name.first_name,
                    :last_name => Faker::Name.last_name,
                    :suffix => Faker::Name.suffix,
                    :email => Faker::Internet.email,
                    :phone => Faker::PhoneNumber.phone_number)
    end
    ```

* `rake db:seed`
* in `routes.rb` file, add RESTful routes for people
* Create an `index` action in your controller
* Create an `index.json.jbuilder` file in your corresponding views
* Follow [jbuilder documentation](https://github.com/rails/jbuilder) in your view
* Start your server and view your JSON!
* Add any other RESTful actions that are needed for your API
