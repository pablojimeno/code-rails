# Chapter 6: Rails Authentication

Are your users authentic?

Nearly every web app needs some kind of authentication system, to ensure that users are who they say they are. Usually this is email/password-based. If the user who is signing in has access to the email and password of a user in the system, we can reasonably assume that user is authentically who they say they are.

  For a user to get in to the system in the first place, we need a way for them to register with our app, a sign-in page. Once they are registered, they can come and go via sign-in and sign-out routes that control create and destroy a "session", respectively. We don't need to store session info in the database, so it only needs the VC of MVC.

  Let's sort all this out by building out a very basic authentication system from scratch, then using the popular and production-ready gem Devise for our portfolio.


- Create authentication in a fresh Rails app from scratch. Do this first.
  - Revised version (pro) : http://railscasts.com/episodes/250-authentication-from-scratch-revised?view=asciicast
  - That uses Rails v3.2.1, so you have options
    - Install and use that version of Rails, try to match all versions exactly (refer to github repo)
    - Recommended: Use the latest Rails 3 version, which has some minor differences
      - Use underscores to create the app with your desired version
        "rails _3.2.16_ new auth"
      - Rails 3.2.11+ will require and add the attr_accessible line for you when a model is generated, so pay attention to what's happening there.
      - If you need it, there is an example repo of this, done with Rails 3.2.14 on the Code Fellows GitHub account. Do not directly duplicate/clone/copy/paste that repo.
- Now, let's contrast that approach with Devise. To get a general idea of how Devise works:
  - Watch or Read: http://railscasts.com/episodes/209-introducing-devise?view=asciicast
  - Do not follow along, this is outdated. The general concepts still apply.
- As the site owner, I want to restrict who can access the site so that my friends don't prank me with "poopin'" posts
  - Write this story (or one similar) in your project management app and a BDD devise specs for:
    - Signing Up (Registering a user account)
      - Path
        - RED: write the spec and watch it fail
          - rails g minitest:feature auth/sign_up
            - A good strategy: You'll probably need to write your spec to conform to the Devise defaults. Don't focus on customizing Devise just yet. Adjust your specs as you go to match the flow Devise is expecting. Test along in your browser as needed.
              - [COMPLETE] Example Spec:
                "require "test_helper"

                feature("
                  As a site visitor
                  I want to be able to sign up for an account
                  so that I can perform actions that require me to be logged in.
                ") do
                  scenario "sign up" do
                    # Given a registration form
                    visit "/"
                    click_on "Sign Up"

                    # When I register with valid info
                    fill_in "Email", with: "test@example.com"
                    fill_in "Password", with: "password"
                    fill_in "Password confirmation", with: "password"
                    click_on "Sign up"

                    # Then I should be signed up
                    page.must_have_content "Welcome! You have signed up successfully"
                    page.wont_have_content "There was a problem with your sign up"
                  end
                end
                "
        - GREEN: Work through the errors
          - Error: Unable to find link or button "Sign Up"
            - Add a link to your application layout. Use the path helper: new_user_registration_path
          - Error: Undefined local variable or method `new_user_registration_path'
            - Let's begin by RTFM: The Devise README: https://github.com/plataformatec/devise
            - Carefully follow all the steps, but take note:
              - The "Getting Started" section will have what you need to do to get set up.
              - Read carefully the output of the 'devise:install' generator. There are 5 suggested steps. Read and understand each as best you can, then do as instructed, IF NEEDED. Generating views is recommended.
              - There are more instructions in the "Getting Started" section to follow... Read carefully. Yes, the config file has things you need to change.
              - When you generate your devise model, call it User. Delete the test/model directory this creates. Note a fixture was created for you.
              - As always, visually inspect the migration before you run it.
            - Re-run your test. If needed:
              "rake db:test:prepare # Get schema changes reflected in test environment
              "
            - Check out the changes in routes.rb:
              "git diff config/routes.rb"
            - What other changes did devise make? Read and understand them all.
              "git diff"
          - Error: SQLite3::ConstraintException: column email is not unique
            - Where did that error come from? What does the stack trace tell you?
            - Read the instructions in the new users.yml fixutre file.
            - Give your fixtures more meaningful names, rather than "one" and "two". These are your first users! Bit and Byte? King and Kong?
            - What attribute do they need set?
          - It's passing! Where'd that route come from?
          - See all new available routes with:
            "rake routes"
- RED: Write a Sprint.ly story and a BDD spec for signing out
  - The spec should sign in a user, and then click a "Sign Out" link to destroy the session
- GREEN: Now work to get the test passing. Time to play in the sandbox and tackle this one without the Path. Try hard!
  - Hints:
    - Your app layout should have a 'Sign Out' link if current_user.present? and otherwise should have a 'Sign Up' and a 'Sign In' link. How do you find the proper path helpers?
    - Since the spec needs to sign in first, you need an existing user. Use one of your fixtures.
      - Fixtures can have embedded ruby in <%= erb tags %>
      - You can use that to set a password like this:
        "dude:
          email: dude@example.com
          encrypted_password: <%= User.new.send(:password_digest, 'password') %>
        "
    - What http verb should you use to destroy a user session?
- RED: Write a Sprint.ly story and a BDD spec for signing in with an existing user
- GREEN: If you added the sign-in link already, and have a good fixture, this shouldn't be too bad!
- REFACTOR: How can you clean up and DRY up your tests?
- RED: Write a Sprint.ly story: As a user, I want posts connected to my account so that I can be attributed as author
  - We can specify this by adding two lines to the bottom of our Creating Post spec:
    "    page.has_css? "#author"
        page.text.must_include users(:one).email # Use your fixture name here.
    "
  - We can run just this one spec from our app root with:
    "ruby -Itest test/features/posts/creating_a_post_test.rb "
- GREEN: Let's see what we need to do, to get this going.
  - FAIL: Expected [...page content...] to include "user@example.com". (or similar)
    - Add some HTML to the app/views/posts/show.html.erb, so the post's author will show...
      "<p id="author">
        <b>By:</b>
        <%= @post.author.email %>
      </p>
      "
  - ERROR: Undefined method `author' for #<Post:0x007f923c8a7e80> (or similar)
    - Our post method needs to know who the associated user is, who wrote the post. We can use Rails associations for this.
    - Time to #Read this : http://guides.rubyonrails.org/v3.2.13/association_basics.html
    - What kind of association do we need?
      - Since each user can write many posts, and each post belongs to just one user, we can use has_many and belongs_to. But let's call the writer of a post it's "author". We can tell Rails to use a different name, but still expect a User object. Modify your models.
      - Add to post.rb
        "  belongs_to :author, class_name: "User""
      - Add to user.rb:
        "  has_many :posts, foreign_key: "author_id""
    - Run this spec again:
      "ruby -Itest test/features/posts/creating_a_post_test.rb "
  - ERROR: undefined method `email' for nil:NilClass
    - What is nil in this error message? That error says we tried to send nil the message "email".
    - So, our post knows it should have an author, but it doesn't have one.
    - We want the currently signed in user to be the author.
    - So let's edit our Post create method. Immediately after the new post is successfully saved, add:
      "        current_user.posts << @post"
    - Run the test again, to see a new error we have introduced:
      "ruby -Itest test/features/posts/creating_a_post_test.rb "
  - ERROR: Undefined method `posts' for nil:NilClass
    - What is nil? Where exactly is that error occurring? Read the error output.
      - app/controllers/posts_controller.rb... what line number? What method?
      - The 'posts' method is called on current_user
      - But current_user is nil.
      - Because no one is signed in yet!
      - Only signed-in users should be able to create posts.
      - Let's restrict some PostController actions to signed-in users only, with a helper method from Devise. Add this line just under the PostsController class definition:
        "  before_action :authenticate_user!, except: [:index, :show]"
        - The before_action will run before any actions in the Controller are executed.
        - with the :except option, we can prevent the filter from running when the user requests index & show, since those actions can be publicly accessible.
    - Run the spec again:
      "ruby -Itest test/features/posts/creating_a_post_test.rb "
  - ERROR: Unable to find field "Title"
    - What line is that from???
    - Huh? An earlier part of our test is now failing?
    - Since we need to be signed in before creating a post, capybara isn't even seeing the form.
    - Modify the test to sign in our fixture user before creating the test.
      - Add something like (remember, type it, don't copy/paste):
        "    # Given an authorized user complets a new post form
            visit new_user_session_path
            fill_in "Email", with: users(:one).email
            fill_in "Password", with: "password"
            click_on "Sign in"

            visit new_post_path"
      - Hm, we already had a few lines of code that looked just like that... Chance to refactor in a few minutes!
    - Run the spec just for this file again
  - ERROR: `ActiveModel::MissingAttributeError' can't write unknown attribute `author_id'
    - Right, we need a author_id column in our database to hold the association info.
    - Which table gets this new column?
    - Let's add it with a migration.
      "rails generate migration AddAuthorIdToPosts author_id:integer"
    - Open and read the new migration file. Does it look good? It should add a new column, author_id, to the posts table, that will be a reference to a User record.
    - Run rake db:migrate, and go look at the change in schema.rb.
    - Since we changed our schema, we also need to update our test environment with:
      "rake db:test:prepare"
    - Run the spec again:
      "ruby -Itest test/features/posts/creating_a_post_test.rb "
    - Green, beautiful green!
- REFACTOR: We aren't done yet!
  - Check out what happens when we run "rake"
    - ERROR: undefined method `email' for nil:NilClass
      - The editing spec doesn’t know who the author is.
      - Let's add the author to the fixture, since it's assumed every post has an author. Use the proper user name from your fixtures:
        "cf:
          title: Code Fellows
          body: Means striving for excellence
          author: one

        cr:
          title: Code Rails
          body: This is how I learned web development
          author: one
        "
      - Rails knows we mean a User when we specify the author. Cool, eh?
    - NOW... we have 1 Failure and 1 Error (still) because we are testing actions that require user sign in.
    - We can add our sign-in snipped to the start of each test (edit post and delete post):
      "    visit new_user_session_path
          fill_in "Email", with: users(:one).email
          fill_in "Password", with: "password"
          click_on "Sign in""
    - Or, better yet... Let's move that snippet into test_helper.rb, in a method called "sign_in".
    - Now we can replace the 4 lines elsewhere with a simple call to: sign_in
  - Try it all out in your browser. How's it look there?
  - What else can you clean up or refactor?
