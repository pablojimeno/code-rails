
### Error:

```
ActionView::MissingTemplate: Missing template projects/index, application/index with {:locale=>[:en], :formats=>[:html], :handlers=>[:erb, :builder, :raw, :ruby, :jbuilder, :coffee]}. Searched in:
```

Ok, Rails expects a template file to match our action. Sure thing. Create a file named "index.html.erb" in a new directory, `app/views/projects`. Put some basic html with embedded ruby in there:

```html
  <h2>My Portfolio</h2>

  <% @projects.each do |project| %>
    <div class="project" id="<%= dom_id(project) %>">
      <h3><%= project.name %></h3>
      <p><%= project.technologies_used %></p>
      <div class="nav">
        <%= link_to 'Show', project %> |
        <%= link_to 'Edit', edit_project_path(project) %> |
        <%= link_to 'Destroy', project, method: :delete, data: { confirm: 'Are you sure?' } %>
      </div>
    </div>
  <% end %>

  <br />
  <%= link_to 'New project', new_project_path %>
```

Now run the test again...
