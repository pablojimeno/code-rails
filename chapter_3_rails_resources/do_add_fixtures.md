# Add Fixtures

Create a directory: /test/fixtures/

Add a file: posts.yml

Add sample data!

Hint: follow the pattern of using a name, followed by key, value pairs

For example:
```
cr:
  title: Code Rails
  body: This is how I learned web development!

http:
  title: Intro to HTTP
  body: It's all about the request-response cycle!

```
Fixtures are instantiated by default, so you can remove .create statements

Replace your existing objects, where appropriate. You can use the fixture to get attributes to use in your tests.

For example:
```
require "test_helper"

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

```


Does the order of your fixtures matter for the deletion spec?

What's the advantage of using fixtures instead of .create statements? Can you think of 3 benefits?

Assignment : Submit link to github commits, comment with Questions & Observations & sources/collaborators
