### Error:

    ActionView::MissingTemplate: Missing template projects/update, application/update with {:locale=>[:en], :formats=>[:html], :handlers=>[:erb, :builder, :raw, :ruby, :jbuilder, :coffee]}.

With no render or redirect in the action, Rails will look, by convention, for a template with the same name as the action.

But, we don't want it to drop down to an `update` template... we want to show the Project detail page (the `show` view) if it saved successfully.

Let's try to update the model attributes based on what was in the form, and redirect if it works:

```ruby
def update
  @project = Project.find(params[:id])

  if @project.update_attributes(project_params)
    redirect_to @project, notice: 'Project was successfully updated.'
  end
end
```

**It works! Wowza!**
