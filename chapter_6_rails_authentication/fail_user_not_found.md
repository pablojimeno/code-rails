### FAIL:

    Expected [...page content...] to include "user@example.com". (or similar)

Oh, right - our spec says that we should see the author's name on the article's page.

Add some HTML to the `app/views/articles/show.html.erb`, so that the article's author will show the author's email address:

```html
<p id="author">
  <b>By:</b>
  <%= @article.author.email %>
</p>
```
