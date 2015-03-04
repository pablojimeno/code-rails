#As the site owner, I want to edit an article so that I can correct typos

Describe the behavior with a spec. Attempt it yourself, then check out the hints if you need help.

**Hints**:

1. <span style="color: white">
  Use a generator to create the test.
</sapn>

- <span style="color: white">
  rails generate minitest:feature EditingAnArticle --spec
</span>

- <span style="color: white">
  Give your feature a name matching the feature.
</span>

- <span style="color: white">
  feature "Editing an Article" do ...
</span>

- <span style="color: white">
  Write your scenario to describe the context
scenario "submit updates to an existing article" do ...
</span>

- <span style="color: white">
  Think through what the flow is like for the users.
</span>

- <span style="color: white">
  The article author goes to an existing Article detail ("show") page
</span>

- <span style="color: white">
  That page should have a link to "Edit" that the author can click
</span>

- <span style="color: white">
  A form is filled in with the changed attributes. The form is submitted. The newly updated article should be shown to the author with a confirmation message.
</span>

**The Path**:

Still need The Path for this BDD process?

1. <span style="color: white">
  Before writing the spec, add comments for the GWT:
</span>

- <span style="color: white">
  Create a new article, and store it in a local variable.
</span>

- <span style="color: white">
  article = Article.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")
</span>

- <span style="color: white">
  Use the Rails path helper to get to the right URL
</span>

- <span style="color: white">
  visit article_path(article)
</span>

- <span style="color: white">
  Fill in the GWT with capybara commands and assertions.
</span>

