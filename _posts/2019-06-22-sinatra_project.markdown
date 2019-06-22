---
layout: post
title:      "Sinatra Project"
date:       2019-06-22 04:58:02 -0400
permalink:  sinatra_project
---

## What is Sinatra?
Sinatra is a lightweight Rack-based Domain Specific Language that can get you started in web application development. Building an application in Sinatra will prepare you for building and learning a larger framwork like Rails. Following standard conventions, patterns, and using specifc gems assisted building and designing my application.

## Disc Golf Collection
I built an application that will allow a user to create a new account, log into and log out of account. Users can view all discs within the application created by all other users. However, the user is able to create, view (read), update, and delete discs within their own collection. 

## Corneal and MVC (Model View Controller)

Corneal is a gem that generates a Sinatra template with a file structure that will help implement separation of concerns. Instead of creating the application in one big file, we are able to separate and group files to have specific jobs. This makes code more maintainable and objects are not tightly coupled. 

Model View Controller:


* Model - this is the 'logic' of a web application where data is manipulated / saved
* View -  this is the 'front-end' / user-facing part of the application that the user interacts with directly
* Controller - this is the layer between the Models and Views relaying data from the brower to the application and vice versa

```
	├── Gemfile
	├── README.md
	├── app
	│   ├── controllers
	│   │   └── application_controller.rb
	│   ├── models
	│   │   └── model.rb
	│   └── views
	│       └── index.erb
	├── config
	│   └── environment.rb
	├── config.ru
	├── public
	│   └── stylesheets
    └── spec
	├── controllers
	├── features
	├── models
	└── spec_helper.rb

```
## ActiveRecord / ORM
ActiveRecord is an Object Relational Mapping that associates your database with your application. This allows you to map ruby classes with database tables and the instances of those classes with the rows of the table. You can also use ActiveRecord macros to set up object relationships. My application uses the *has_many* and *belongs_to* relationships. 

```
class Disc < ActiveRecord::Base 
    validates :name, :color, :weight, presence: true
    belongs_to :user 
end 
```
## CRUD and RESTful Routes
CRUD stands for: Create, Read, Update, and Delete. They are the verbs we use to operate on data in a database providing the four basic function of persistent storage, like creating a new user, reading (or viewing) user data, updating user data, and deleing user data. A RESTful route provides the a mapping between HTTP verbs to controller CRUD actions 

* HTTP -> URL -> Action
* GET -> /examples -> index
* GET -> /examples/new -> new
* GET -> /examples/1 -> show
* GET -> /examples/1/edit -> edit
* POST -> /examples -> create
* PUT or PATCH -> /examples/1 -> update
* DELETE -> /examples/1 -> destroy

```
 get '/discs/new' do 
        if logged_in?
            erb :'/discs/create_disc'
        else 
            redirect 'login'
        end 
    end 
```

Using these tools and a lot of help from the Flatiron community I was able to build my first web application!

Please check out [repository](https://github.com/FlipTech9/discgolf_sinatra_crud) to learn more.

