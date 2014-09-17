# As an employer, I want to see a custom blog so that I know this developer has good communication skills, is an expert in their field, and demonstrates technical expertise

Describe the behavior with a spec

Hint: Use a generator to create the test:
rails generate minitest:feature VisitingThePostIndex

Hint: Give your feature a name matching the file
feature "Visiting the Post Index" do ...

Hint: Write your scenario to describe the context
scenario "with existing posts, show list" do ...

Hint: Think through what the flow is like for the users.
A post will be created
Someone will visit the post listing (at /posts/)
The post that was created should be visible there.
Path:
Before writing the spec, add comments for the Given-When-Then:
```
require "test_helper"
feature "Visiting the Post Index" do
  scenario "with existing posts" do
    # Given existing posts

    # When I visit /posts

    # Then the existing posts should be loaded

  end
end
```

Hint: Start by creating a post directly in the database, so the index page has something to show

Post.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")

Hint: Use the Rails "path helper" to get to the right URL
            "rake routes"


visit posts_path
View "Completed" for a complete specification
[COMPLETE]
Fill in the GWT with capybara commands and assertions:
```
require "test_helper"
feature "Visiting the Post Index" do
  scenario "with existing posts" do
    # Given existing posts
    Post.create(title: "Becoming a Code Fellow", body: "Means striving for excellence.")

    # When I visit /posts
    visit posts_path

    # Then the existing posts should be loaded
    page.text.must_include "Becoming a Code Fellow"
  end
end
```
