#As the site owner, I want to edit a post so that I can correct typos

Describe the behavior with a spec
- Hint: <span style="color: white">Use a generator to create the test:</sapn>
rails generate minitest:feature EditingAPost</span>

- Hint: <span style="color: white">Give your feature a name matching the file:
    - <span style="color: white">feature "Editing a Post" do ...</span>

- Hint: <span style="color: white">Write your scenario to describe the context
scenario "submit updates to an existing post" do ...</span>

- Hint: <span style="color: white">Think through what the flow is like for the users.

The post author goes to an existing Post detail ("show") page

That page should have a link to "Edit" that the author can click

A form is filled in with the changed attributes
The form is submitted
The newly updated post should be shown to the author with a confirmation message

Path:
Before writing the spec, add comments for the GWT:

- Hint: <span style="color: white"> Create a new post, and store it in a local variable</span>

<span style="color: white">post = Post.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")</span>

- Hint: <span style="color: white"> Use the Rails path helper to get to the right URL</span>

<span style="color: white">visit post_path(post)</span>

Fill in the GWT with capybara commands and assertions:

