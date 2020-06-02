# Project: Building Facebook clone

* DON'T PANIK if something wrong with your project you can reset chaqnges in branch using next commands
### The reset to undo changes. The clean to remove any untracked files and directories.

            $ git reset --hard HEAD
            $ git clean -fd 

* NOTE before start chreate project using this command (name_of_project it`s example, you should change it on your own name of your project for example: facebook-clone...)

        rails new name_of_project --database=postgresql
       
* NOTE itis very important!!! You should install postgresql in your operating system! Next article should help: [How To Install and Use PostgreSQL on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04)
        
* This article and video can be useful [The Ultimate Intermediate Ruby on Rails Tutorial: Let’s Create an Entire App!](https://www.freecodecamp.org/news/lets-create-an-intermediate-level-ruby-on-rails-application-d7c6e997c63f/) , also this article [Adding Authentication with Devise](https://guides.railsgirls.com/devise) and video: [Testing with RSpec](https://www.youtube.com/watch?v=71eKcNxwxVY)

* NOTE If you forgot during creating your app add next peace of code --database=postgresql please follow next article [Making the Change From SQLite3 to PostgreSQL - Ruby on Rails](https://dev.to/torianne02/making-the-change-from-sqlite3-to-postgresql-ruby-on-rails-2m0p) and add postgresql manually : But main you should add lat version of postgress.

* NOTE if you need to add column to your database please use next command

        rails generate migration add_fieldname_to_tablename fieldname:string. 
        
        
* NOTE Sometimes, even dropping a local development database is not a good idea. There are better ways to delete/destroy a specific migration in your Rails application.

You could use rails d migration command to destroy a particular migration:

rails d migration MigrationName
To undo the changes corresponding to a particular migration, you can use db:migrate:down method like this:

        rake db:migrate:down VERSION=XXX

* version you can find in file schema.rb

after you that command you delete that file donot forgor to run

        rails db:migrate
        
        
### Testing https://leanpub.com/everydayrailsrspec/read_sample

## Features

- [ ] The user logs in the app, only by typing the username (a proper authenticated login is not a mandatory requirement, but it is in the nice-to-have list)

- [ ] The user is presented with a list of houses: apartment, house, room, etc.

- [ ] When a user selects a house, detailed information about the house is presented and the possibility add it to favourites

- [ ] The user can access a list of favourite apartments

* The database should have at least 2 tables — in this example, houses and favourites, i.e., the favourites can be accessed by all users unless you implement a proper user authentication (more on this later). To create ERD(Entity Relationship Diagram) diagram, it`s image of your future database, I used online tool [lucidchart](https://www.lucidchart.com/) to draw that diagram, create folder "docs" and add to folder that image with diagram. Follow this video to understand how it works [Entity Relationship Diagram (ERD) Tutorial - Part 1](https://www.youtube.com/watch?v=QpdhBUYk7Kk&vl=en)
* Watch next video to be familiar with Primary and Foreign Keys [Entity Relationship Diagram (ERD) Tutorial - Part 2](https://www.youtube.com/watch?v=-CuY5ADwn24)

Here is a screenshot with example of such image with diagram:
![screen](#)


## Environment:

* 
I recommended to add next gems:

* gem ['bootstrap-sass', '3.3.7'](https://github.com/twbs/bootstrap-rubygem)
* gem ['bcrypt',         '3.1.12'](https://github.com/codahale/bcrypt-ruby)
* gem ['faker',          '1.7.3'](https://github.com/faker-ruby/faker)
* gem ['will_paginate', '3.1.6'](https://github.com/mislav/will_paginate)
* gem ['bootstrap-will_paginate', '1.0.0'](https://github.com/yrgoldteeth/bootstrap-will_paginate) 
* gem ['rubocop'](https://www.rubocop.org/en/stable/)
* gem ['devise'](https://github.com/plataformatec/devise)
* gem ["font-awesome-rails"]()
* gem ['gravatar_image_tag'](https://github.com/mdeering/gravatar_image_tag)

group :development, :test do
* gem ["rspec-rails"](https://github.com/rspec/rspec-rails) 
* gem ['sqlite3', '1.3.13'](https://github.com/sparklemotion/sqlite3-ruby)
end
        
 
 Than use next command in your terminal
 
      $  bundle install
      $  bundle update

1. Cause we added bootstrap to Gemfile in next step we should create file and add bootstrap to our application

        touch app/assets/stylesheets/custom.scss

Inside this file app/assets/stylesheets/custom.scss add next code

        @import "bootstrap-sprockets"; 
        @import "bootstrap";

2. Cause we added font-awesom in your application.css, include next:

/*
 *= require font-awesome
 */

 Inside this file app/assets/stylesheets/custom.scss add next code

        @import "font-awesome";

On this site https://fontawesome.com/?from=io you can choose any icons you want


## Users, houses, favourits

I this project we Create models with associations and implement all requested features for users and posts. Add authentication with Devise as described in requirements.

rails generate scaffold User first_name:string last_name:string email:string password:string birthday:string gender:string

rails db:migrate