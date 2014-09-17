# As the site owner, I want to write a post so that I can show my expertise

Describe the behavior with a spec. Go write a spec file for this story now.
<span style="color: white">
Hint: Use a generator to create the test:
rails generate minitest:feature CreatingAPost

Hint: Give your feature a name matching the file
feature "Creating an Article" do ...

Hint: Write your scenario to describe the context
scenario "submit form data to create a new article" do ...

Hint: Think through what the flow is like for the users.
The article author goes to a blank Article form
The form is filled in with the attributes of the new Article (title, body)
The form is submitted
The newly created article should be shown to the author with a confirmation message
Path:
Before writing the spec, add comments for the GWT:

```ruby
require "test_helper"

feature "Creating an article" do
  scenario "submit form data to create a new article" do
    # Given a completed new article form

    # When I submit the form

    # Then a new article should be created and displayed

  end
end
```
Hint: Use the Rails path helper to get to the right URL

visit new_articles_path

Fill in the GWT with capybara commands and assertions:

```ruby
require "test_helper"

feature "Creating an article" do
  scenario "submit form data to create a new post" do
    # Given a completed new article form
    visit new_post_path
    fill_in "Title", with: "Code Rails"
    fill_in "Body", with: "This is how I learned to make web apps."

    # When I submit the form
    click_on "Create Article"

    # Then a new post should be created and displayed
    page.text.must_include "Article was successfully created"
    page.text.must_include "how I learned to make web apps"
  end
end
```

</span>




