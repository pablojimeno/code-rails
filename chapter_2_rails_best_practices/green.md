# GREEN
There is an example of the WelcomeController in the official [Ruby on Rails Getting Started Guide](http://guides.rubyonrails.org/getting_started.html). Read (but do not work along) up through Section 4.

### Create a WelcomeController to handle static pages

1. Run `rails`, then read the output. This is a list of available CLI commands that rails offers

- Run `rails generate`, then read all the generators that are available in your rails project

- Run `rails generate controller`, then read the docs on the Rails controller generator

- Use that info to create a WelcomeController with an index view

- Look carefully at each file that is generated.

- Delete any unwanted files before committing your changes.

### Basic Rails Routing

A route is how your Rails app maps URLs to a Rails controller.

 >The Rails router recognizes URLs and dispatches them to a controller's action
 http://guides.rubyonrails.org/routing.html

You need to set the "root" route. (Don't you just love saying that, no matter what accent you have?)

Check out and read the comments in `config/routes.rb`.

For example, if you wanted to create a default route to a controller called "pigs" and an action called "fly" you would type:

    root 'pigs#fly'

What result would you expect from this root route?

    root 'sessions#new'

You need to create a root route to your Welcome controller and the home or index action. Do it now!
