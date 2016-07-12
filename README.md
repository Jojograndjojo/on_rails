# Setting up a rail project

## Installation
to install rail with postgresql as a database

```rails new project -d postgresql -T```

start the server:
```bin/rails server```

May need to run ```bin/rake db:create```

```bin/rake db:create RAILS_ENV=test```
## Setting up tests

add the right gems

```ruby
group :test do
  gem 'rspec-rails'
  gem 'capybara'
end
```
run the command
```bin/rails generate rspec:install```

in ```spec/rails_helper.rb```

```require 'capybara/rails'```

## Routing

in ```config/routes```

```get 'objects' => 'objects#index'

resources ```:objects```

## Creating controllers

```bin/rails g controller objects```

##Creating views

```touch app/views/objects/index.htm.haml(or erb)```

## Creating Models

```bin/rails g model object name:string```

```bin/rake db:migrate```

## Displaying objects

in ```controllers/objects_controller.rb```

```ruby
def index
  @restaurants = Restaurant.all
end
```

in ```app/views/objects/index.html.haml```
```html
- if @restaurants.any?
  - @restaurants.each do |restaurant|
    %h2= restaurant.name
- else
  No restaurants yet

%a(href='#') Add a restaurant

```
