
### FAILURE:

    in "authors can't publish" expected to find Published

This is left over from the previous **FAIL**.

This seems like a bad message in the test output. We asserted that the page WONT have Published. But, actually, it's properly failing. The Published field is there for authors, when it should not be. Hm, seems like we should wrap the "Published" check box with some role-checking logic as well:

```html
<% if current_user.role == "editor" %>
  <div class="row collapse">
    <div class="small-3 columns">
      <%= f.label :published, class: "right inline", title: "Is this article published?", data: {tooltip: true } %><br>
    </div>

    <div class="small-9 columns">
      <%= f.check_box :published %>
    </div>
  </div>
<% end %>
```




