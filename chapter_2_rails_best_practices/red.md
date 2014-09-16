# RED
- Write a feature spec for your user story above
    - You'll need a new Rails 4 app. Let's call this Portfolio.
    - Hints:
      - <span style="color: white">We are not using the default Test::Unit framework, so you will want to use the handy --skip-test-unit flag.</span>
      - <span style="color: white">rails new portfolio --skip-test-unit</span>


- Once you've generated the app, clean up the Gemfile according to best practices described in the earlier section.
- We want you to use minispec and capybara to BDD this. You'll have to set this up within your Rails project. Here are some documentation resources:
    - Read https://github.com/blowmage/minitest-rails
    - Read https://github.com/blowmage/minitest-rails-capybara
    - Don't blindly copy/paste every command from those docs. That will mess you up.
    - Rather: understand what the commands do.
    - Decide which you need, which you don't, and which you may need to modify.
    - RETYPE! Copy/paste is the enemy of learning.
- Instead of configuring this in a file called `minitest_helper.rb`, use the standard test helper file: `test_helper.rb` in the test/ directory
- Really Stuck? Ask a classmate, ask a TA or Instructor, or watch a silent video of Ivan do it (imperfectly) with an older version of Rails and MiniTest: http://www.youtube.com/watch?v=0pl-h-CHWEA

- Now create a test (remember what the docs said about how to create a new feature test?) in the `test/features/` directory (make the directory if you don't have it) that visits the root of your Rails app to ensure the Welcome index view is showing.
    - Ensure your specs runs as the default task when you run `rake`
    - It should fail. That's ok! If you see an `error`, ensure everything is set up correctly.

Now you are ready to get the test passing.
