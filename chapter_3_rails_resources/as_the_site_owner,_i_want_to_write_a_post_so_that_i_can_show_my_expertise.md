# As the site owner, I want to write a post so that I can show my expertise

Describe the behavior with a spec
Hint: Use a generator to create the test:
rails generate minitest:feature CreatingAPost

Hint: Give your feature a name matching the file
feature "Creating a Post" do ...

Hint: Write your scenario to describe the context
scenario "submit form data to create a new post" do ...

Hint: Think through what the flow is like for the users.
The post author goes to a blank Post form
The form is filled in with the attributes of the new Post (title, body)
The form is submitted
The newly created post should be shown to the author with a confirmation message
Path:
Before writing the spec, add comments for the GWT:

```
require "test_helper"

feature "Creating a post" do
  scenario "submit form data to create a new post" do
    # Given a completed new post form

    # When I submit the form

    # Then a new post should be created and displayed

  end
end
```
Hint: Use the Rails path helper to get to the right URL

visit new_posts_path

View "Completed" for a complete specification
[COMPLETE] Fill in the GWT with capybara commands and assertions:

```
require "test_helper"

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
```

