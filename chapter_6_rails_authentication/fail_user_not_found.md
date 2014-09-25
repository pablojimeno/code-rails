### FAIL:

    Expected [...page content...] to include "user@example.com". (or similar)

Add some HTML to the `app/views/articles/show.html.erb`, so the article's author will show...

```html
<p id="author">
  <b>By:</b>
  <%= @article.author.email %>
</p>
```
