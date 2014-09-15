# As a dev, I want a basic Rails app up and running on port 3000 of my computer

BDD `rails new sample-app`. Write your test first! What would a test that looks on port 3000 look like?

Be careful where you run this command. Be sure to make this new app outside of your current project directory tree. You don't need to submit this new rails app with your main project code.

Once you've created the Rails app, how can you start it up?

Need a hint? Try changing in to the directory for the new Rails project you just created, and type just `rails`.

**Example specification:**
```ruby
# ~/myapp/spec/features/rails_new_spec.rb

require "spec_helper"

describe "My Rails App welcome page" do
  it "shows the welcome message" do
    visit "http://localhost:3000"
    page.text.must_include "Welcome aboard"
  end
end
```
