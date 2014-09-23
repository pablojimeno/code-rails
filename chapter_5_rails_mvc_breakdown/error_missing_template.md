### Error: Missing Template

    Error: ActionView::MissingTemplate: Missing template projects/create, application/create with {:locale=>[:en], :formats=>[:html], :handlers=>[:erb, :builder, :raw, :ruby, :jbuilder, :coffee]}.

- Good progress. Now, rather than moving right through to the `show` action, it is staying in the `create` action.
- Since the save (in `ProjectsController#create`) fails, the `else` block that we left blank earlier is executed.
- Since there is no `redirect` or `render` statement, Rails drops down to our `views` folder, and looks for a `create.html.erb` template to match the action name, by convention.
- We don't really want to do this. We want to show the same `new` page with the Project form on it, but now with the error messages we picked up from the failed save.
- So let's add some logic to the `else` block when our save fails.
- For starters, lets just add a `render` statement to render the existing `new` view. Your `create` action should now look like this:
```ruby
  def create
    @project = Project.new(project_params)
    if @project.save
      flash[:notice] = "Project has been created."
      redirect_to @project
    else
      render :new
    end
  end
```
- See the change?
