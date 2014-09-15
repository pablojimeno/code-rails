# Example spec

```ruby
# ~/myapp/spec/features/welcome_page_spec.rb

require "spec_helper"

describe "A local web page" do
  it "has a welcome headline" do
    visit "/something/goes/here/..."
    page.text.must_include "Welcome to my page"
  end
end
```
