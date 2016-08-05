+++
date = "2016-08-02T17:25:20-04:00"
draft = false
title = "Authentication"

+++

## Part 1: Signup (create a new user)
1. Create a User model in the terminal
```bash
$ rails g model User name email password_digest
```

2. Add user routes to `config/routes.rb`
```ruby
get '/signup' => 'users#new'
post '/users' => 'users#create'
```

3. Create a `users_controller`
```bash
$ rails g controller Users
```

4. Add a `create` and `new` actions in the controller
```ruby
    # app/controllers/users_controller.rb
    class UsersController < ApplicationController
      def new
        render 'new.html.erb'
      end

      def create
        user = User.new(
          name: params[:name],
          email: params[:email],
          password: params[:password],
          password_confirmation: params[:password_confirmation]
        )
        if user.save
          session[:user_id] = user.id
          flash[:success] = 'Successfully created account!'
          redirect_to '/'
        else
          flash[:warning] = 'Invalid email or password!'
          redirect_to '/signup'
        end
      end
    end
```

5. Add a new view in the app/views/users folder:
```html
  <!-- app/views/users/new.html.erb -->
  <h1>Signup</h1>
  <%= form_tag('/users', method: 'post') do %>
      <div>
        <%= label_tag(:name) %>
        <%= text_field_tag(:name) %>
      </div>
      <div>
        <%= label_tag(:email) %>
        <%= text_field_tag(:email) %>
      </div>
      <div>
        <%= label_tag(:password) %>
        <%= password_field_tag(:password) %>
      </div>
      <div>
        <%= label_tag(:password_confirmation) %>
        <%= password_field_tag(:password_confirmation) %>
      </div>
      <%= submit_tag("Submit") %>
  <% end %>
```

6. Uncomment the `bcrypt` gem in the Gemfile:
```ruby
gem 'bcrypt', '~> version'
```

7. Add the method `has_secure_password` to the User model
```ruby
    # app/models/user.rb
    class User < ActiveRecord::Base
      has_secure_password
    end
```

8. Run `bundle install` and restart the server
```bash
$ bundle install
$ rails server
```

## Part 2: Logout and login (create a new session)

1. Add session routes to `config/routes.rb`:
```ruby
    # config/routes.rb
    get '/login'
    get '/login' => 'sessions#new'
    post '/login' => 'sessions#create'
    get '/logout' => 'sessions#destroy'
```

2. Create a Rails sessions controller
```bash
$ rails g controller sessions
```

3. Add a new, create, and destroy action to the sessions controller:
```ruby
    # app/controllers/sessions_controller
    class SessionsController < ApplicationController
      def new
        render "new.html.erb"
      end

      def create
        user = User.find_by(email: params[:email])
        if user && user.authenticate(params[:password])
          session[:user_id] = user.id
          flash[:success] = "Successfully logged in!"
          redirect_to '/'
        else
          flash[:warning] = "Invalid email or password"
          redirect_to '/login'
        end
      end

      def destroy
        session[:user_id] = nil
        flash[:success] = "You've logged out"
        redirect_to '/login'
      end
    end
```
4. Add a new view in the `app/views/sessions` folder:
```html
    <!-- app/views/sessions/new.html.erb -->
    <h1>Login</h1>
    <%= form_tag('/login', method: 'post') do %>
      <div>
        <%= label_tag(:email) %>
        <%= text_field_tag(:email) %>
      </div>
      <div>
        <%= label_tag(:password) %>
        <%= text_field_tag(:password) %>
      </div>
      <%= submit_tag("Login") %>
    <% end %>
```

## Part 3: Authentication Helpers
1. Add helper methods in `app/controllers/application_controller.rb`  
```ruby
    # app/controllers/application_controller.rb
    class ApplicationController < ActionController::Base
      # Prevent CSRF attacks by raising an exception.
      # For APIs, you may want to use :null_session instead.
      protect_from_forgery with: :exception

      def current_user
        @current_user ||= User.find_by(id: session[:user_id]) if session[:user_id]
      end
      helper_method :current_user

      def authenticate_user!
        redirect_to '/login' unless current_user
      end
    end
```
