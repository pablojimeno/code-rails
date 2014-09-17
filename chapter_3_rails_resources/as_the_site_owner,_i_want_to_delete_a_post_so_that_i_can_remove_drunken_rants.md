#As the site owner, I want to delete a post so that I can remove drunken rants

Describe the behavior with a spec

- Hint: <span style="color: white">Use a generator to create the test:
rails generate minitest:feature DeletingAPost</span>

- Hint: <span style="color: white">Give your feature a name matching the file
feature "Deleting a Post" do ...</span>

- Hint: <span style="color: white">Write your scenario to describe the context
scenario "post is deleted with a click" do ...</span>

- Hint: <span style="color: white">Think through what the flow is like for the users.</span>

The post author goes the Post index page

That page should have a link to "Destroy" each post, that the author can click

The index page should no longer have that post

Path:
Before writing the spec, add comments for the GWT:

- Hint: <span style="color: white">Create a new post, and store it in a local variable</span>

    - <span style="color: white">post = Post.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")</span>

- Hint: <span style="color: white">Use the Capybara selectors to find the right Destroy link: github.com/jnicklas/capybara#finding</span>

    - <span style="color: white">page.find("tr:last").click_on "Destroy"</span>

[COMPLETE] Fill in the GWT with capybara commands and assertions:

Run all those specs with `rake` and WHOA, look at all those errors!
