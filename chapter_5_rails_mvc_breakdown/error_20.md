### Error:
    ActionView::Template::Error: First argument in form cannot contain nil or be empty

We've seen this one before! Remember what to do?

Find the line number from your code where the error was hit:

    app/views/projects/_form.html.erb:1:in `_app_views_projects__form_html_erb__3579151376221201616_70184742725320'

Q: What is holds a value of nil on that line?

A: <span style="color: white">@project</span>, of course!

Q: Where's the right place to define it?

In the controller:
```ruby
def edit
  @project = Project.find(params[:id])
end
```

We can get the id of the Project we want to edit from the url (e.g., `.../projects/6/edit`). This is available under the `:id` key of the `params` object.

Re-run specs... do we get the next error?

