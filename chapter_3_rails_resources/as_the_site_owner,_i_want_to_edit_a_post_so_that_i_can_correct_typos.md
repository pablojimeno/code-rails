#As the site owner, I want to edit an article so that I can correct typos

Describe the behavior with a spec
- Hint: <span style="color: white">Use a generator to create the test:</sapn>
rails generate minitest:feature EditingAnArticle</span>

- Hint: <span style="color: white">Give your feature a name matching the file:
    - <span style="color: white">feature "Editing a Article" do ...</span>

- Hint: <span style="color: white">Write your scenario to describe the context
scenario "submit updates to an existing article" do ...</span>

- Hint: <span style="color: white">Think through what the flow is like for the users.

The article author goes to an existing Article detail ("show") page

That page should have a link to "Edit" that the author can click

A form is filled in with the changed attributes
The form is submitted
The newly updated article should be shown to the author with a confirmation message

Path:
Before writing the spec, add comments for the GWT:

- Hint: <span style="color: white"> Create a new article, and store it in a local variable</span>

<span style="color: white">article = Article.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")</span>

- Hint: <span style="color: white"> Use the Rails path helper to get to the right URL</span>

<span style="color: white">visit article_path(article)</span>

Fill in the GWT with capybara commands and assertions:

