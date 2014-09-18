### Write a User Story

Start with Given/When/Then (GWT) comments:
```ruby
  scenario "new project has invalid data" do
    # Given invalid project data is entered in a form
    # When the form is submitted with a short name and missing technologies_used field
    # Then the form should be displayed again, with an error message
  end
```

- How would you flesh that out?
- What does invalid data look like?
- Perhaps both fields should have a minimum length?
- After you've attempted to translate to the spec to code, check out the next page for a solution.
