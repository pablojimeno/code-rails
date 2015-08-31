# Example web search spec

Search Google with a simple pec test.

Please use your own search term:

### Create ~/my_app_path/spec/search_spec.rb

```ruby
require "spec_helper"

describe "My search page" do
  it "has results" do
    visit "http://google.com"
    fill_in "q", with: "Code Fellows"
    click_on "Google Search"
    page.text.must_include "codefellows.org"
    page.text.must_include "twitter.com/CodeFellowsOrg"
  end
end
  ```

Make sure your spec_helper file includes:

**Example spec_helper.rb:**
```ruby
# ~/myapp/spec/spec_helper.rb

require "minitest/autorun"
require "minitest/spec"

class FeatureSpec < MiniTest::Spec
  require "capybara/poltergeist"
  include Capybara::DSL
  Capybara.default_driver = :poltergeist
  register_spec_type(/page$/, self)
end
```

**Ex

In this example, we are ensuring that 2 releavent links appear on the first page of search results.

Note the `spec_helper` file required at the top of `search_spec.rb`. Based on what the READMEs tell you, you'll probably want it looking something like this...


**Important reminder:** This `spec_helper.rb` file sets up Capybara to work for any feature specs you create that have a description ending in "...page".
