# As an employer, I want to see a custom blog so that I know this developer has good communication skills, is an expert in their field, and demonstrates technical expertise

Describe the behavior with a spec. Go write a spec file for this story now.

After you've tried do create your own spec from scratch, check out the hidden hints.

**Hints**:

1. <span style="color: white">
Use a generator to create the test.
</span>

- <span style="color: white">
  $ rails generate ...
</span>

- <span style="color: white">
  $ rails generate minitest:feature VisitingTheArticleIndex --spec
</span>

- <span style="color: white">
  Give your feature a name matching the feature.
</span>

- <span style="color: white">
  feature "Visiting the Article Index" do ...
</span>

- <span style="color: white">
  Write your scenario to describe the context
</span>

- <span style="color: white">
  scenario "with existing articles, show list" do ...
</span>

- <span style="color: white">
  Think through what the flow is like for the users.
</span>

- <span style="color: white">
  An article will be written
</span>

- <span style="color: white">
  Someone will visit the article listing (at "/articles")
</span>

- <span style="color: white">The article that was created should be visible there.</span>

**The Path**:

Want to just follow the path?

1. <span style="color: white">
  Before writing the spec, add comments for the Given-When-Then.
</span>

- Check out this example of how to use guiding GWT comments with [this gist](https://gist.github.com/brookr/d284e740392cdb1dbae9/5946dc80a6414d1c219a24a8c09e0ebfecdd1f30).

- <span style="color: white">
  Start by setting up the given context with an article already in the database, so the index page has something to show
</span>

- <span style="color: white">
  Article.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")
</span>

- <span style="color: white">
  Then tell Capybara to visit the index page
</span>

- <span style="color: white">
  Use the Rails "path helper" to get to the right URL
</span>

- <span style="color: white">
  Run this command to see all available routes: rake routes
</span>

- <span style="color: white">
  You'll want something like: visit articles_path
</span>

- Now you can fill in the GWT with ruby code using these capybara commands and spec assertions at [this gist](https://gist.github.com/brookr/d284e740392cdb1dbae9/7380e522032b8f8b813fa5855d63c3df64f77bfc).
