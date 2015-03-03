#As the site owner, I want to delete an article so that I can remove drunken rants

Describe the behavior with a spec

1. <span style="color: white">
  Use a generator to create the test:
rails generate minitest:feature DeletingAnArticle --spec
</span>

- <span style="color: white">
  Give your feature a name matching the file
feature "Deleting an Article" do ...
</span>

- <span style="color: white">
  Write your scenario to describe the context
scenario "article is deleted with a click" do ...
</span>

- <span style="color: white">
  Think through what the flow is like for the users.
</span>

- <span style="color: white">
  The article author goes to the Article index page
</span>

- <span style="color: white">
  That page should have a link to "Destroy" each article, that the author can click.
</span>

- <span style="color: white">
  The index page should no longer have that article
</span>

**The Path**:

1. <span style="color: white">
  Before writing the spec, add comments for the GWT.
</span>

- <span style="color: white">
  Create a new article, and store it in a local variable
</span>

- <span style="color: white">
  article = Article.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")
</span>

- <span style="color: white">
  Use the Capybara selectors to find the right Destroy link: github.com/jnicklas/capybara#finding
</span>

- <span style="color: white">
  page.find("tbody tr:last").click_on "Destroy"
</span>

- <span style="color: white">
  Fill in the GWT with capybara commands and assertions.
</span>


Finally, run all those specs with `rake` and WHOA, look at all those errors!
