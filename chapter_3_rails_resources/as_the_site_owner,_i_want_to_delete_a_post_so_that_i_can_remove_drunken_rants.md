#As the site owner, I want to delete a post so that I can remove drunken rants

Describe the behavior with a spec

Hint: Use a generator to create the test:
rails generate minitest:feature DeletingAPost

Hint: Give your feature a name matching the file
feature "Deleting a Post" do ...

Hint: Write your scenario to describe the context
scenario "post is deleted with a click" do ...

Hint: Think through what the flow is like for the users.

The post author goes the Post index page

That page should have a link to "Destroy" each post, that the author can click

The index page should no longer have that post

Path:
Before writing the spec, add comments for the GWT:
```
require "test_helper"

feature "Deleting a Post" do
  scenario "post is deleted with a click" do
    # Given an existing post

    # When the delete link is clicked

    # Then the post is deleted

  end
end
```

Hint: Create a new post, and store it in a local variable

post = Post.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")

Hint: Use the Capybara selectors to find the right Destroy link: https://github.com/jnicklas/capybara#finding

page.find("tr:last").click_on "Destroy"

View "Completed" for a complete specification @brookr

[COMPLETE] Fill in the GWT with capybara commands and assertions:
```
require "test_helper"

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
end
```
Run all those specs with `rake` and WHOA, look at all those errors!
