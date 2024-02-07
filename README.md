# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

**If you want to use Postgres # Note that this will expect a postgres user with the same username # as your app, you may need to edit config/database.yml to match the # user you created earlier**

1) rails new myapp -d postgresql

**Move into the application directory**

2) cd myapp

**If you setup MySQL or Postgres with a username/password, modify the # config/database.yml file to contain the username/password that you specified** 

**Create the database**

default: &default
  adapter: postgresql
  encoding: unicode
  database: your_database_name
  username: postgres
  password: 12345678
  host: localhost
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>

development:
  <<: *default
  database: user_two_facter_development

**Create the database**

3) rake db:create

**Your Gemfile should now include something like**

4) # Gemfile
gem "devise", "~> 4.8"

5) bundle install

**Then— just like on the Devise readme — we generate the Devise config.**

6) rails g devise:install


# config/environments/development.rb, near the other action_mailer config. ~line 40 in an unaltered config file.

7) config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }

# app/views/layouts/application.html.erb, above the <%= yield %>

8) <% if notice %>
  <p class="alert alert-success"><%= notice %></p>
	<% end %>
	<% if alert %>
  <p class="alert alert-danger"><%= alert %></p>
	<% end %>

**In the following command you will replace MODEL with the class name used for the application’s users (it’s frequently User but could also be Admin). This will create a model (if one does not exist) and configure it with the default Devise modules.**

9) rails generate devise MODEL

10) rails db:migrate


**Devise will create some helpers to use inside your controllers and views. To set up a controller with user authentication, just add this before_action**

11) before_action :authenticate_user!

**To verify if a user is signed in**

12) user_signed_in? 
