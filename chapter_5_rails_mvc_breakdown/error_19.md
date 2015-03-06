### Error:

    Capybara::ElementNotFound: Unable to find field "Name"

Read the stack trace... What line number did that happen on?

    test/features/projects/edit_project_test.rb:9:in `block (2 levels) in <main>'

That's line 9 of our test. Look there, in the example file, it's:

```ruby
fill_in :name, with: "My Rad Portfolio"
```

**Q**: What do you think the error means?

**A**: <span style="color: white">
  There is no field for Capybara to fill in.
</span>

**Q**: Why is that?

**A**: <span style="color: white">
  course, the edit template is blank!
</span>

Add some content to our template. What does it need?
Tell the user we are on the Edit page:

```html
<h1>Edit Project</h1>
```

A way to navigate away without saving:

```html
<%= link_to "Cancel", :back %>
```

In between these, it needs... the edit form!

We already have a form in new. Are you just going to copy and paste it? How do we repurpose it? That is, DRY it up?

Extract it to a partial

Create a new file in `app/views/projects/` called `_form.html.erb`

Cut from the entire contents of the `app/views/projects/new.html.erb`, except for the `h1` and the link at the bottom

Paste the form into `_form.html.erb`:

What's with the underscore?

```html
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
```

Replace that in the `new.html.erb` view with a render line. It should look like this now:

```html
<h1>New project</h1>

<%= render "form" %>

<%= link_to 'Back', projects_path %>
```

Does that actually work? Re-run the create test to ensure:

    ruby -Itest test/features/projects/creating_project_test.rb

Put the same render line in our edit template:
```html
<h1>Edit Project</h1>

<%= render "form" %>

<%= link_to "Cancel", :back %>
```
Does that get us to the next error? Re-run the edit spec.


