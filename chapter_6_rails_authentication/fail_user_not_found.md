### FAIL:

    Expected [...page content...] to include "user@example.com". (or similar)

Add some HTML to the `app/views/posts/show.html.erb`, so the article's author will show...

```html
<p id="author">
  <b>By:</b>
  <%= @post.author.email %>
</p>
```
