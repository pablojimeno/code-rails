# As the site owner, I want to write an article so that I can show my expertise

Describe the behavior with a spec. Go write a spec file for this story now.

- Hint:<span style="color: white"> Use a generator to create the test:
rails generate minitest:feature CreatingAnArticle --spec</span>

- Hint: <span style="color: white">Give your feature a name matching the file
feature "Creating an Article" do ...</span>

- Hint: <span style="color: white">Write your scenario to describe the context
scenario "submit form data to create a new article" do ...</span>

- Hint: <span style="color: white">Think through what the flow is like for the users.
The article author goes to a blank Article form
The form is filled in with the attributes of the new Article (title, body)
The form is submitted
The newly created article should be shown to the author with a confirmation message
Path:
Before writing the spec, add comments for the GWT: </span>

- Hint: <span style="color: white"> Use the Rails path helper to get to the right URL

<span style="color: white"> visit new_articles_path</span>

<span style="color: white"> Fill in the GWT with capybara commands and assertions: </span>




