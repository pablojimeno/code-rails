## RED: Add a scenario


Outline your scenario for *the unhappy path* using GWT.

```ruby
scenario "incorrectly editing an existing project" do
  # Given an existing project
  # When I submit invalid changes
  # Then the changes should not be saved, and I should get to try again
end
```

Fill in the GWT with some Capybara commands and the appropriate matchers.
