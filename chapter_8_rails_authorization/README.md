# Chapter 8: Rails Authorization

BDD authorization roles for Portfolio

We're going to add the ability to mark blog posts as "published" (or not). And, we will specify who can publish posts.

To manage this, we will create three roles on your portfolio site:

 - Editors - these are the site admins that can do everything, including marking articles as "published"
 - Authors - these can write posts, but not publish them.
 - Visitors - the default user type, a regular site visitor, they can only view published posts.

Ready to give it a go? Your assignment: Modify your portfolio to have the above behaviors.

  - Write a whole bunch of user stories for all these behaviors. Add these to your PM add:
    - Authors
      - As an author I want to only see my own posts so that I can focus on my work
      - As an author I want to create posts so that I can share great content with the world
      - As an author I want to update posts so that I can fix typos
      - As an author I should not be able to publish posts so that I can give the editor publishing control
        - and I should see a 'not authorized' message if I try to hack it
      - As an author I should not be able to delete posts so that I can give the editor publishing control
    - Editors
      - As an editor I want to see all posts regardless of published status in the blog index so that I can choose which posts to publish
      - As an editor I want to create posts so that I can share great content with the world
      - As an editor I want to update posts so that I can fix typos
      - As an editor I want to publish posts so that I can make posts live on the site
      - As an editor I want to delete posts so that I can remove opium-fueled Jabberwocky
    - Visitors (unauthenticated users)
      - As a site visitor (user) I want to view (read) posts so that I can enjoy quality content
      - As a site visitor I should not be able to delete, update or create posts so that I can't modify a site I don't own
      - As a site visitor I want to only see published posts so that I don't see crap drafts
  - RED: Creating Posts
    - What do we need to do to write tests for those user stories?
    - We need a way to access the site as different roles:
      - Signed in as editor (think: admin)
      - Signed in as author
      - not signed in at all, a site visitor
    - That will provide the "scenarios" for our resource CRUD tests. Today, let's focus just on Posts.
    - We want to specify that we can sign in as an author to create a post, that is not yet published. Let's make two change to our existing creating_a_post_test.rb file:
      "    sign_in(:author)
          ...
          page.text.must_include "Status: Unpublished"
      "
    - We can then add a few additional tests:
      - A simple test to ensure visitors do not have access to the new post form:
        "  scenario "unauthenticated site visitors cannot visit new_post_path" do
            visit new_post_path
            page.must_have_content "You need to sign in or sign up before continuing"
          end"
      - In fact, they don't even need to see the new post button on the index
        "  scenario "unauthenticated site vistiors cannot see new post button" do
            # When I visit the blog index page
            visit posts_path
            # Then I should not see the "New Post" button
            page.wont_have_link "New Post"
          end"
      - Let's consider a post "published" if a simple boolean database value is flipped to true. Editors should see this value in the Post form, but authors should not. That gives us 2 more simple tests
        "  scenario "authors can't publish" do
            # Given an author's account
            sign_in(:author)

            # When I visit the new page
            visit new_post_path

            # There is no checkbox for published
            page.wont_have_field('published')
          end

          scenario "editors can publish" do
            # Given an editor's account
            sign_in(:editor)

            # When I visit the new page
            visit new_post_path

            # There is a checkbox for published
            page.must_have_field('Published')

            # When I submit the form
            fill_in "Title", with: posts(:cr).title
            fill_in "Body", with: posts(:cr).body
            check "Published"
            click_on "Create Post"

            # Then the published post should be shown
            page.text.must_include "Status: Published"
          end"
  - GREEN: Creating Posts
    - Run those tests! After every error is corrected... Do you see the same errors as listed here?
      "ruby -Itest test/features/posts/creating_a_post_test.rb"
    - ERROR: wrong number of arguments (1 for 0)
      - Our sign_in method in test_helper.rb doesn't have an argument for who to sign in. Modify it to accommodate, with a default to editor, so current tests still work:
        "  def sign_in(role = :editor)
            visit new_user_session_path
            fill_in "Email", with: users(role).email
            fill_in "Password", with: "password"
            click_on "Sign in"
          end"
    - ERROR: No fixture named 'author' found for fixture set 'users'
      - I bet you know what to do here.
      - You should add a new fixture for :author and one for :editor
        - Try it yourself first. How might we determine what role each user record belongs to?
          - What, you want to see an example? OK!
            "author:
              email: author@example.com
              encrypted_password: <%= User.new.send(:password_digest, 'password') %>
              role: author

            editor:
              email: editor@example.com
              encrypted_password: <%= User.new.send(:password_digest, 'password') %>
              role: editor
            "
    - ERROR: SQLite3::SQLException: table users has no column named role...
      - Every test breaks, because our fixtures cannot load without a role column on user.
      - Add a migration. Users should have a 'role' attribute. Just a string will do for now
        - rails generate migration add_role_to_users role
        - Check out that generated file. Does it look like it will set things up correctly?
        - Run migrations, and ensure your test db is reflecting the schema change
    - FAILURE: 1) Expected "Awesome Portfolio ..." to include "Status: Unpublished". and 2) expected to find published
      - First, let's add the HTML to show if a Post is published or not:
        "<p id="status">
          <b>Status:</b>
          <%= @post.published? ? "Published" : "Unpublished" %>
        </p>"
      - That should get the first Failure taken care of. Now lets focus on giving editors the publish capability.
      - Add the published attribute to the form. Depending on your theme, it may be something like:
        "    <div class="field">
              <%= f.label :published %>
              <%= f.check_box :published %>
            </div>"
      - ERROR: undefined method `published' for #<Post:0x007ffef4275ad8>
        - Add a migration to have 'published' attribute for posts
          - rails generate migration add_published_to_posts published:boolean
          - How's the generated migration look?
          - run it:
            "rake db:migrate test:prepare"
      - Run the test again. Why is it still failing? The attribute is in the form, in the view, and in the database. Shouldn't Rails just put the pieces together?
        - Let's troubleshoot. What does save_and_open_page show you about the post's "status"?
        - Are you properly checking the checkbox in the form? save_and_open_page can show this as well.
        - If all looks well, let's take a look at the last 200 lines or so of the test log file, immediately after running this one test (eg: NOT `rake`):
          "tail -n200 log/test.log"
          - Scroll back through the logs until you find the details about the post creation. Look for something like:
            "Processing by PostsController#create"
          - Does the params hash include the published attribute?
            ""published"=>"1"
            "
          - Why isn't it getting saved? What does the log report happens next?
            - Did you notice the line:
              "Unpermitted parameters: published"
            - How do we fix that?
              - We need to permit the published parameter!
              - Where do we do that? How do we allow it only for editors, and not authors?
                - The controller is the only part of MVC that is session-aware.
                - We need one additional param permitted, if the user is an editor.
                - Ruby allows lists to end with a comma
                - So we can conditionally add a final item to our post_params method:
                  "      params.require(:post).permit(:title, :body, (:published if current_user.role == "editor"))
                  "
    - FAILURE: in "authors can't publish" expected to find Published
      - This actually seems like a bad message in the test output. We asserted that the page WONT have Published.
      - But it's properly failing. The Published field is there for authors, when it should not be.
      - Hm, seems like we should wrap the "Published" check box with some role-checking logic as well:
        "  <% if current_user.role == "editor" %>
            <div class="row collapse">
              <div class="small-3 columns">
                <%= f.label :published, class: "right inline", title: "Is this post published?", data: {tooltip: true } %><br>
              </div>

              <div class="small-9 columns">
                <%= f.check_box :published %>
              </div>
            </div>
          <% end %>
        "
  - REFACTOR: This is key.
    - In 2 different places, we did a literal check of the value of current_user.role to permit a behavior. This is a code smell. We really want to know if the user has publishing permission. In the future, that may not be just editors. Our implementation is exposed.
    - How can we refactor the check on publishing policy? With the number of checks we will need to do throughout our app, this is really important to get right.
    - Let's encapsulate that behavior in an object.
    - We should be able to ask a PostPolicy object, given the current_user and a @post, if publishing is allowed.
      "    if PostPolicy.new(current_user, @post).publish?"
    - Then we can keep the implementation in a single place for better maintainability.
    - The new code is not shorter, but it is Better with a capital B! :]
    - What does the implementation look like?
      - We can create a PORO (plain old ruby object) in a new directory, app/policies
      - We should have one policy file for each Resource in our app.
      - post_policy.rb should define a `publish?` method to encapsulate our business logic:
        "class PostPolicy
          attr_accessor :user, :post

          def initialize(user, post)
            @user = user
            @post = post
          end

          def publish?
            @user.role == "editor"
          end
        end
        "
      - Try that out!
      - Is your test still passing, if you use the PostPolicy object to check publish permission?
    - So, we will still have our code littered with instantiations of PostPolicy, and passing in current_user...
      - Wouldn't it be nice if we had a short-hand way to access the policy method, operating under the convention of current_user?
      - Enter the Pundit gem!
      - #READ about the Pundit Gem
        - Pundit Gem README: https://github.com/elabs/pundit
        - Another possibly useful resource: Pundit Gem sections of The Rails 4 way: http://hijk.it/0U0v37360312
      - Install the gem, and refactor your permission checks according to Pundit conventions.
      - rails generate pundit:policy post
        - IMPORTANT: edit this policy class include a create? policy and publish? policy (and others eventually)
          - Check the README for hints on implementation
          - This is the "meat" of this chapter's exercise, without a policy all the other behaviors will be much more tedious!
  - Further Refactors
    - Fix your fixtures
      - add `published: true` to the existing fixtures
    - Optional, but recommended: add an index for the published column in your database for better performance
    - We'll need to do fairly often checks on the user's role. Add some utility methods to the User class for .author? and .editor?
      "  def author?
          role == 'author'
        end

        def editor?
          role == 'editor'
        end	"
      - Now you can clean up that PostPolicy a little:
        "  def publish?
            @user.editor?
          end"
  - RED: BDD those other behaviors
    - Write tests for all those other user stories.
  - GREEN: Pundit it up.
    - Use Pundit to get all these permitted behaviors sorted out.
    - You may want to add a publish method to the post model like this:
      "def publish!
        published = true
        save!
      end"
    - add in code to your index view to only show links if the policy allows it:
      "<% @posts.each do |post| %>
        <tr id="<%= dom_id(post) %>">
          <td><%= post.title %></td>
          <td><%= post.body %></td>
          <td><%= link_to 'Show', post %></td>
          <% if policy(post).update? %>
            <td><%= link_to 'Edit', edit_post_path(post) %></td>
          <% end %>
          <% if policy(post).destroy? %>
            <td><%= link_to 'Destroy', post, method: :delete, data: { confirm: 'Are you sure?' } %></td>
          <% end %>
        </tr>
      <% end %>
      "
  - REFACTOR
    - Code Coverage - how much of your app is tested?
      - http://en.wikipedia.org/wiki/Code_coverage
      - Check test code coverage with SimpleCov locally and, optionally, http://Coveralls.io online.
    - DRY up your tests with helper methods
    - Extra credit / Discussion: What are some ways to improve test coverage?
