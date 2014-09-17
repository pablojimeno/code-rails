# Chapter 3: Rails Resources


  - RED
    - As an employer, I want to see a custom blog so that I know this developer has good communication skills, is an expert in their field, and demonstrates technical expertise
      - Describe the behavior with a spec
        - Hint: Use a generator to create the test:
          - rails generate minitest:feature VisitingThePostIndex
        - Hint: Give your feature a name matching the file
          - feature "Visiting the Post Index" do ...
        - Hint: Write your scenario to describe the context
          - scenario "with existing posts, show list" do ...
        - Hint: Think through what the flow is like for the users.
          - A post will be created
          - Someone will visit the post listing (at /posts/)
          - The post that was created should be visible there.
        - Path:
          - Before writing the spec, add comments for the Given-When-Then:
            "require "test_helper"

            feature "Visiting the Post Index" do
              scenario "with existing posts" do
                # Given existing posts

                # When I visit /posts

                # Then the existing posts should be loaded

              end
            end
            "
          - Hint: Start by creating a post directly in the database, so the index page has something to show
            - Post.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")
          - Hint: Use the Rails "path helper" to get to the right URL
            "rake routes"
            - visit posts_path
          - View "Completed" for a complete specification
          - [COMPLETE] Fill in the GWT with capybara commands and assertions:
            "require "test_helper"

            feature "Visiting the Post Index" do
              scenario "with existing posts" do
                # Given existing posts
                Post.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")

                # When I visit /posts
                visit posts_path

                # Then the existing posts should be loaded
                page.text.must_include "Becoming a Code Fellow"
              end
            end"
    - As the site owner, I want to write a post so that I can show my expertise
      - Describe the behavior with a spec
        - Hint: Use a generator to create the test:
          - rails generate minitest:feature CreatingAPost
        - Hint: Give your feature a name matching the file
          - feature "Creating a Post" do ...
        - Hint: Write your scenario to describe the context
          -  scenario "submit form data to create a new post" do ...
        - Hint: Think through what the flow is like for the users.
          - The post author goes to a blank Post form
          - The form is filled in with the attributes of the new Post (title, body)
          - The form is submitted
          - The newly created post should be shown to the author with a confirmation message
        - Path:
          - Before writing the spec, add comments for the GWT:
            "require "test_helper"

            feature "Creating a post" do
              scenario "submit form data to create a new post" do
                # Given a completed new post form

                # When I submit the form

                # Then a new post should be created and displayed

              end
            end
            "
          - Hint: Use the Rails path helper to get to the right URL
            - visit new_posts_path
          - View "Completed" for a complete specification
          - [COMPLETE] Fill in the GWT with capybara commands and assertions:
            "require "test_helper"

            feature "Creating a post" do
              scenario "submit form data to create a new post" do
                # Given a completed new post form
                visit new_post_path
                fill_in "Title", with: "Code Rails"
                fill_in "Body", with: "This is how I learned to make Rails apps."

                # When I submit the form
                click_on "Create Post"

                # Then a new post should be created and displayed
                page.text.must_include "Post was successfully created"
                page.text.must_include "how I learned to make Rails apps"
              end
            end
            "
    - As the site owner, I want to edit a post so that I can correct typos
      - Describe the behavior with a spec
        - Hint: Use a generator to create the test:
          - rails generate minitest:feature EditingAPost
        - Hint: Give your feature a name matching the file
          - feature "Editing a Post" do ...
        - Hint: Write your scenario to describe the context
          -  scenario "submit updates to an existing post" do ...
        - Hint: Think through what the flow is like for the users.
          - The post author goes to an existing Post detail ("show") page
          - That page should have a link to "Edit" that the author can click
          - A form is filled in with the changed attributes
          - The form is submitted
          - The newly updated post should be shown to the author with a confirmation message
        - Path:
          - Before writing the spec, add comments for the GWT:
            "require "test_helper"

            feature "editing a post" do
              scenario "submit updates to an existing post" do
                # Given an existing post

                # When I click edit and submit changed data

                # Then the post is updated

              end
            end
            "
          - Hint: Create a new post, and store it in a local variable
            - post = Post.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")
          - Hint: Use the Rails path helper to get to the right URL
            - visit post_path(post)
          - View "Completed" for a complete specification @brookr
          - [COMPLETE] Fill in the GWT with capybara commands and assertions:
            "require "test_helper"

            feature "Editing a Post" do
              scenario "submit updates to an existing post" do
                # Given an existing post
                post = Post.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")
                visit post_path(post)

                # When I click edit and submit changed data
                click_on "Edit"
                fill_in "Title", with: "Becoming a Web Developer"
                click_on "Update Post"

                # Then the post is updated
                page.text.must_include "Post was successfully updated"
                page.text.must_include "Web Developer"
              end
            end
            "
    - As the site owner, I want to delete a post so that I can remove drunken rants
      - Describe the behavior with a spec
        - Hint: Use a generator to create the test:
          - rails generate minitest:feature DeletingAPost
        - Hint: Give your feature a name matching the file
          - feature "Deleting a Post" do ...
        - Hint: Write your scenario to describe the context
          -  scenario "post is deleted with a click" do ...
        - Hint: Think through what the flow is like for the users.
          - The post author goes the Post index page
          - That page should have a link to "Destroy" each post, that the author can click
          - The index page should no longer have that post
        - Path:
          - Before writing the spec, add comments for the GWT:
            "require "test_helper"

            feature "Deleting a Post" do
              scenario "post is deleted with a click" do
                # Given an existing post

                # When the delete link is clicked

                # Then the post is deleted

              end
            end
            "
          - Hint: Create a new post, and store it in a local variable
            - post = Post.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")
          - Hint: Use the Capybara selectors to find the right Destroy link: https://github.com/jnicklas/capybara#finding
            - page.find("tr:last").click_on "Destroy"
          - View "Completed" for a complete specification @brookr
          - [COMPLETE] Fill in the GWT with capybara commands and assertions:
            "require "test_helper"

            feature "Deleting a Post" do
              scenario "post is deleted with a click" do
                # Given an existing post
                Post.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")
                visit posts_path

                # When the delete link is clicked
                click_on "Destroy"

                # Then the post is deleted
                page.wont_have_content "Becoming a Code Fellow"
              end
            end"
    - Run all those specs with `rake` and WHOA, look at all those errors!
  - GREEN
    - Generate a Post scaffold
      - Run and read: `rails generate scaffold`
      - Try it with the --pretend option to see what it will do
      - Try it with the --no-test-framework option to see the difference (a lot less just put in your /test/ folder!)
      - When you have to command to your liking, remove --pretend and run it for real
        - View "Completed" for the full command
          - [COMPLETE] rails generate scaffold post title body:text --no-test-framework
  - REFACTOR
    - Hmm, creating Posts directly in our tests wasn't very DRY. Is there a better way?
      - Read: A Guide to Testing Rails Applications, section 2: Fixtures: http://guides.rubyonrails.org/testing.html#the-low-down-on-fixtures (JUST read section 2)
      - #rails4 Optional reading: For a lot more on fixtures: http://edgeapi.rubyonrails.org/classes/ActiveRecord/FixtureSet.html
      - Create a directory: /test/fixtures/
      - Add a file: posts.yml
      - Add sample data!
        - Hint: follow the pattern of using a name, followed by key, value pairs
          - For example:
            "cr:
              title: Code Rails
              body: This is how I learned web development!

            http:
              title: Intro to HTTP
              body: It's all about the request-response cycle!
            "
      - Fixtures are instantiated by default, so you can remove .create statements
      - Replace your existing objects, where appropriate. You can use the fixture to get attributes to use in your tests.
        - For example:
          "require "test_helper"

          feature "Creating a post" do
            scenario "submit form data to create a new post" do
              # Given a completed new post form
              visit new_post_path
              fill_in "Title", with: posts(:cr).title
              fill_in "Body", with: posts(:cr).body

              # When I submit the form
              click_on "Create Post"

              # Then a new post should be created and displayed
              page.text.must_include "Post was successfully created"
              page.text.must_include posts(:cr).title
            end
          end
          "
      - Does the order of your fixtures matter for the deletion spec?
      - What's the advantage of using fixtures instead of .create statements? Can you think of 3 benefits?
  - #assignment : Submit link to github commits, comment with Questions & Observations & sources/collaborators
