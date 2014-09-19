## RED: Write a spec for edit (update)

Did you try to write this spec on your own first? Highlight the blocks below to see a solution. Yours doesn't have to match exactly.

Start by writing the GWT:
<pre style="color: #f7f7f7">
  <code>
require "test_helper"

feature "As the site owner, I want to edit a project so that I can correct typos" do
    scenario "editing an existing project" do
    # Given an existing project

    # When I make changes

    # Then the changes should be saved and shown

    end
  end
  </code>
</pre>

Now fill in the blanks with some Capybara directives. View the solution below after you think you've got it.

[COMPLETE] solution for `edit_project_test.rb`

<pre style="color: #f7f7f7">
  <code>
require "test_helper

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
  </code>
</pre>

