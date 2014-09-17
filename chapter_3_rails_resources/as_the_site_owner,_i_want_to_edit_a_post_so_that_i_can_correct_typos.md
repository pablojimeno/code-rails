#As the site owner, I want to edit a post so that I can correct typos

Describe the behavior with a spec
Hint: Use a generator to create the test:
rails generate minitest:feature EditingAPost

Hint: Give your feature a name matching the file
feature "Editing a Post" do ...

Hint: Write your scenario to describe the context
scenario "submit updates to an existing post" do ...

Hint: Think through what the flow is like for the users.
The post author goes to an existing Post detail ("show") page

That page should have a link to "Edit" that the author can click

A form is filled in with the changed attributes
The form is submitted
The newly updated post should be shown to the author with a confirmation message

Path:
Before writing the spec, add comments for the GWT:

```
require "test_helper"

feature "editing a post" do
  scenario "submit updates to an existing post" do
    # Given an existing post

    # When I click edit and submit changed data

    # Then the post is updated

  end
end
```

Hint: Create a new post, and store it in a local variable
post = Post.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")

Hint: Use the Rails path helper to get to the right URL

visit post_path(post)</br>
View "Completed" for a complete specification @brookr
[COMPLETE]</br>
Fill in the GWT with capybara commands and assertions:

```
require "test_helper"

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
```

