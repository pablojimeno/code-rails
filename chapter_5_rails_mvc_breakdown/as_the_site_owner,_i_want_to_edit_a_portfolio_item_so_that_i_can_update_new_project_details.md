# As the site owner, I want to edit a portfolio item so that I can update new project details
- As the site owner, I want to edit a portfolio item so that I can update new project details
  - RED: Write spec for edit (update)
    - rails generate minitest:feature projects/editing_a_project --pretend
      - Spec: Try to write this spec on your own first... view "completed" to see an example. Yours doesn't have to match exactly.
        - Start by writing the GWT:
          "require "test_helper"

          feature "As the site owner, I want to edit a project so that I can correct typos" do
            scenario "editing an existing project" do
              # Given an existing project

              # When I make changes

              # Then the changes should be saved and shown

            end
          end
          "
        - Now fill in the blanks with some Capybara directives.
        - [COMPLETE] edit_project_test.rb
          "require "test_helper"

          feature "As the site owner, I want to edit a project so that I can correct typos" do
            scenario "editing an existing project" do
              # Given an existing project
              visit edit_project_path(projects(:portfolio))

              # When I make changes
              fill_in "Name", with: "My Rad Portfolio"
              click_on "Update Project"

              # Then the changes should be saved and shown
              page.text.must_include "Success"
              page.text.must_include "Rad Portfolio"
              page.text.wont_include "Code Fellows Portfolio"
            end
          end
          "
  - GREEN: Keep running the spec and resolving errors until it works! Remember, you can run just this one test with the following command from our project root:
    "# that is a "dash capital i" option to the ruby command
    ruby -Itest test/features/projects/editing_a_project_test.rb"
    - Error: The action 'edit' could not be found for ProjectsController
      - We know what to do here, right? Edit app/controllers/projects_controller.rb to add (without removing what's there):
        "  def edit

          end"
      - Run the test again to see if that gets us to the next error...
    - Are you using Fixtures yet? Perhaps you see an error like: NoMethodError: undefined method `projects' for #<#<Class:0x007ffbccbb4c28>:0x007ffbcc960558>
      - Create a fixture file called `projects.yml` in test/fixtures/
      - Add some data to it. Remember, YAML is white space sensitive (and how!):
        "portfolio:
          name: How meta
          technologies_used: Ruby, Rails, Zurb

        freelance:
          name: Barnyard Cereal
          technologies_used: Ruby, Rails, Farmville API, Automilker
        "
      - Ensure you are using the fixtures by their correct names when accessing them in your test.
    - Error: AbstractController::ActionNotFound: The action 'edit' could not be found for ProjectsController
      - Add an edit action to the ProjectsController. Very similar to what you did above.
    - Error: ActionView::MissingTemplate: Missing template projects/edit, application/edit with {:locale=>[:en], :formats=>[:html], :handlers=>[:erb, :builder, :raw, :ruby, :jbuilder, :coffee]}.
      - This looks familiar. We need to create a file. Where does it go?
        - app/views/portfolio/
        - What's it call?
          - edit.html.erb
            - How do we create that from the command line?
              - touch app/views/projects/edit.html.erb
      - Does creating that blank file allow us to get a new error message now? Yes! Progress!
    - Error: Capybara::ElementNotFound: Unable to find field "Name"
      - Read the stack trace... What line number did that happen on?
        - Something like:
          "test/features/projects/edit_project_test.rb:9:in `block (2 levels) in <main>'"
          - That's line 9 of our test.
          - Look there. In the example file, its...
            "fill_in :name, with: "My Rad Portfolio""
          - The error means there is no field for Capybara to fill in.
          - Of course, the edit template is blank!
      - Add some content to our template.
        - What does it need?
          - Tell the user we are on the Edit page
            "<h1>Edit Project</h1>
            "
          - A way to navigate away without saving
            "<%= link_to "Cancel", :back %>
            "
          - In between these, it needs... The edit form!
            - We already have a form in new... How do we repurpose it?
              - Extract it to a partial
              - Create a new file in app/views/projects/ called _form.html.erb
              - Cut from the entire contents of the app/views/projects/new.html.erb, except for the h1 and the link at the bottom, paste in to _form.html.erb:
                "<%= form_for(@project) do |f| %>
                  <% if @project.errors.any? %>
                    <div id="error_explanation">
                      <h2><%= pluralize(@project.errors.count, "error") %> prohibited this project from being saved:</h2>

                      <ul>
                      <% @project.errors.full_messages.each do |msg| %>
                        <li><%= msg %></li>
                      <% end %>
                      </ul>
                    </div>
                  <% end %>

                  <div class="field">
                    <%= f.label :name %><br />
                    <%= f.text_field :name %>
                  </div>
                  <div class="field">
                    <%= f.label :technologies_used %><br />
                    <%= f.text_area :technologies_used %>
                  </div>
                  <div class="actions">
                    <%= f.submit %>
                  </div>
                <% end %>"
              - Replace that in the new.html.erb view with a render line. It should look like this now:
                "<h1>New project</h1>

                <%= render "form" %>

                <%= link_to 'Back', projects_path %>
                "
              - Does that actually work? Re-run the create test to ensure:
                "ruby -Itest test/features/projects/creating_project_test.rb"
              - Put the same render line in our edit template:
                "<h1>Edit Project</h1>

                <%= render "form" %>

                <%= link_to "Cancel", :back %>
                "
              - Does that get us to the next error? Re-run the edit spec.
    - Error: ActionView::Template::Error: First argument in form cannot contain nil or be empty
      - We've seen this one before! Remember what to do?
        - Find the line number from your code where the error was hit:
          "app/views/projects/_form.html.erb:1:in `_app_views_projects__form_html_erb__3579151376221201616_70184742725320'"
        - What is nil on that line?
          - @project! Where's the right place to define it?
            - In the controller:
              "  def edit
                  @project = Project.find(params[:id])
                end"
            - We can get the id of the Project we want to edit from the url (eg: .../projects/6/edit). This is available under the :id key of the params object.
      - Re-run specs... do we get the next error?
    - Error: AbstractController::ActionNotFound: The action 'update' could not be found for ProjectsController
      - NB: We did not need to do anything to get the same form partial to have a different button text. How did Rails know to change it?
        - In the new form, the @project object is a new object, and so:
          "@project.new_record? == true
          "
        - When the form is rendered in the edit action, we are using an object we got from the db, so:
          "@project.new_record? == false"
        - Rails handles the button text for us. Thanks, Rails!
      - Submitting the same form, when in edit mode, now goes to the ProjectsController#update action, instead of create. Let's add that action.
        "  def update

          end
        "
      - Run the specs again.
    - Error: ActionView::MissingTemplate: Missing template projects/update, application/update with {:locale=>[:en], :formats=>[:html], :handlers=>[:erb, :builder, :raw, :ruby, :jbuilder, :coffee]}.
      - With no render or redirect in the action, Rails will look, by convention, for a template with the same name as the action.
      - But we don't want it to drop down to an "update" template... we want to show the Project detail page (show view) if it saved successfully. Let's try to update the model attributes based on what was in the form, and redirect if it works.
        "  def update
            @project = Project.find(params[:id])

            if @project.update_attributes(project_params)
              redirect_to @project, notice: 'Project was successfully updated.'
            end
          end
        "
    - It works! Wowza!
  - REFACTOR:
    - Check your coding style and clarity. Anything you need to clean up?
    - It looks like the show, edit, and update actions all set up the @project instance variable in the exact same way. Let's DRY that up.
      - Create a new private method called `set_project`
      - The contents of that method should be the code that is repeated in the show/edit/update actions that sets up the instance variable
      - Replace the code in those actions with a simple call to this new method
      - Better yet, find a way to call the `set_project` method before each of those actions that need it, so you don't even have to repeat the method call.
      - Take a look at how it is done in the scaffold-generated PostController
  - What if the user enters bad data in the edit form?? We need to test the unhappy path.
    - RED: Add a scenario for this...
      "  scenario "incorrectly editing an existing project" do
          # Given an existing project

          # When I submit invalid changes

          # Then the changes should not be saved, and I should get to try again
        end
      "
      - Fill in the GWT with some capybara commands and the appropriate matchers
    - GREEN: Can you follow along with the error messages, and get them passing?
      - Hints:
        - Here's a full scenario:
          "  scenario "incorrectly editing an existing project" do
              # Given an existing project
              visit edit_project_path(projects(:portfolio))

              # When I submit invalid changes
              fill_in "Name", with: "Err"
              click_on "Update Project"

              # Then the changes should not be saved, and I should get to try again
              page.text.must_include "prohibited"
              page.text.must_include "Name is too short"
            end"
        - Here's a full update action:
          "  def update
              @project = Project.find(params[:id])

              if @project.update_attributes(params[:project])
                redirect_to @project, notice: 'Project was successfully updated.'
              else
                render :edit
              end
            end
          "
        - Was that so bad? ;]
    - REFACTOR: Run rake and ensure all your tests are still passing. Anything need cleanup? Commit and push to origin!
