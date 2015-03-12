
### FAILURE:

    in "authors can't publish" expected to find published

This is left over from the previous **FAILURE**.

This seems like a bad message in the test output. We asserted that the HTML will NOT have a 'published' field.

Actually, the test ***is*** properly failing. The error message's English is not correctly negated due to the way `minitest-capybara` generated this particular refutation's message (remember, we're using the `wont_have_field` refutation).

That is to say: Ideally, this error message would have read:

    in "authors can't publish" expected to *not* find published

The "published" field is there for authors, when it should not be. Hmm, seems like we should wrap the "published" check box with some role-checking logic as well:

```html
<% if current_user.role == "editor" %>
  <div class="row collapse">
    <div class="small-3 columns">
      <%= f.label :published, class: "right inline", title: "Is this article published?", data: {tooltip: true } %>
    </div>

    <div class="small-9 columns">
      <%= f.check_box :published %>
    </div>
  </div>
<% end %>
```

Run the tests!

Green!



