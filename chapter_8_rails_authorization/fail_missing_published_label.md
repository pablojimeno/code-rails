### FAILURE:

    Expected "Awesome Portfolio ..." to include "Status: Unpublished".

### FAILURE:

    expected to find published


Did you see these two failures messages?

First, let's add the HTML to show if an Article is published or not:

```html
<p id="status">
  <b>Status:</b>
  <%= @article.published? ? "Published" : "Unpublished" %>
</p>
```

That should get the first **Failure** taken care of. Now lets focus on giving editors the publish capability. Add the published attribute to the form. Depending on your theme, it may be something like:

```html
<div class="field">
  <%= f.label :published %>
  <%= f.check_box :published %>
</div>
```
