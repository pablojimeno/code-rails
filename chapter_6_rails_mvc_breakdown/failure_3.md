
### Failure:

    Expected ...page text... to include "Name is too short"

Well, of course! We should show error messages if there are any!

Luckily, Rails will store that for us, right on the `@project` instance. Let's check there, and show any error messages we find.

Let's add some HTML to show the messages, and some ERB to loop over however many messages there are.

Modify your "new" template so it looks like this (type, don't copy/paste):

```html
<h1>New project</h1>

<%= form_for(@project) do |f| %>
  <% if @project.errors.any? %>
    <div id="error_explanation">
      <h2><%= pluralize(@project.errors.count, "error") %> prohibited this project from being saved:</h2>

      <ul>
      <% @project.errors.full_messages.each do |msg| %>
        <li><%= msg %></li>
      <% end %>
      </ul>
    </div>
  <% end %>

  <div class="field">
    <%= f.label :name %><br />
    <%= f.text_field :name %>
  </div>
  <div class="field">
    <%= f.label :technologies_used %><br />
    <%= f.text_area :technologies_used %>
  </div>
  <div class="actions">
    <%= f.submit %>
  </div>
<% end %>

<%= link_to 'Back', projects_path %>
```

Woot! Now there are 2 passing specs!

