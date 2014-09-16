# As an employer, I want your site to have a welcome page so that I can learn about what an awesome Rails developer you are

####Apply best practices: BDD a static front page for your Rails portfolio app.
- RED
    - Write a feature spec for your user story above
        - You'll need a new Rails 4 app. Let's call this Portfolio.
        - Hint: We are not using the default Test::Unit framework, so you will want to use the handy `--skip-test-unit` flag:

    `rails new portfolio --skip-test-unit`

- Once you've generated the app, clean up the Gemfile according to best practices above.
- We want you to use minispec and capybara to BDD this. You'll have to set this up within your Rails project. Here are some documentation resources:
    - Read https://github.com/blowmage/minitest-rails
    - Read https://github.com/blowmage/minitest-rails-capybara
    - Don't blindly copy/paste every command from those docs. That will mess you up.
    - Rather: understand what the commands do.
    - Decide which you need, which you don't, and which you may need to modify.
    - RETYPE! Copy/paste is the enemy of learning.
- Instead of configuring this in a file called `minitest_helper.rb`, use the standard test helper file: `test_helper.rb` in the test/ directory
- Really Stuck? Ask a classmate, ask a TA or Instructor, or watch a video of Ivan do it with an older version of Rails and MiniTest: http://www.youtube.com/watch?v=0pl-h-CHWEA

- Now create a test (remember what the docs said about how to create a new feature test???) in the test/features/ directory (make the directory if you don't have it) that visits the root of your Rails app to ensure the Welcome index view is showing.
    - Ensure your specs runs as the default task when you run `rake`
    - It should fail. That's ok! If you see an error, ensure everything is set up correctly.

- GREEN
    - There is an example of the WelcomeController in the official Ruby on Rails Getting Started Guide. #Read (but do not do-along) up through section 4: http://guides.rubyonrails.org/getting_started.html
    - Create a Welcome controller to handle static pages
    - type `rails` to read the list of available CLI commands that rails offers
    - type `rails generate` to read all the generators that are available in your rails project
    - type `rails generate controller` and read the docs on the Rails controller generator
    - Use that info to create a Welcome controller with an index view
    - Look carefully at each file that is generated. Delete any unwanted files before committing your changes.

- Basic Rails Routing
    - A route is how your app maps URLs to a Rails controller. "The Rails router recognizes URLs and dispatches them to a controller's action" - http://guides.rubyonrails.org/routing.html
    - You need to set the "root" route. (Don't you just love saying that, no matter what your accent is?).
    - Check out and read the comments in config/routes.rb
    - For example, if you wanted to create a default route to a controller called "pigs" and an action called "fly" you would type:
            "root 'pigs#fly'"
    - You need to create a root route to your home controller and the index action

- REFACTOR
    - Customize the HTML template
        - If you want to change the <title> tag of the page, where would you go?
        - Hints: The title tag is something in the page layout, that is set application wide right now.
            - Is it M,V, or C?
    - Add some basic information about you. Why would someone want to hire you? What you add doesn't have to be styled well, but try to structure it with basic HTML.
