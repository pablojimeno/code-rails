
## GREEN: Pundit it up.

Use Pundit to get all these permitted behaviors sorted out. You may want to add a publish method to the article model like this:
```ruby
  def publish!
    published = true
    save!
  end
```

add in code to your index view to only show links if the policy allows it:
```html
<% @articles.each do |article| %>
  <tr id="<%= dom_id(article) %>">
    <td><%= article.title %></td>
    <td><%= article.body %></td>
    <td><%= link_to 'Show', article %></td>
    <% if policy(article).update? %>
      <td><%= link_to 'Edit', edit_article_path(article) %></td>
    <% end %>
    <% if policy(article).destroy? %>
      <td><%= link_to 'Destroy', article, method: :delete, data: { confirm: 'Are you sure?' } %></td>
    <% end %>
  </tr>
<% end %>
```

