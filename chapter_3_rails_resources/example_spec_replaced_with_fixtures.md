# Example spec replaced with fixtures

```ruby
require "test_helper"

feature "Creating an article" do
  scenario "submit form data to create a new article" do
    # Given a completed new article form
    visit new_article_path
    fill_in "Title", with: articles(:cr).title
    fill_in "Body", with: articles(:cr).body

    # When I submit the form
    click_on "Create Article"

    # Then a new article should be created and displayed
    page.text.must_include "Article was successfully created"
    page.text.must_include articles(:cr).title
  end
end

```
