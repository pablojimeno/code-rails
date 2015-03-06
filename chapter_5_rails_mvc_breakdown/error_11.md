### Error:

```
ActiveModel::ForbiddenAttributesError
```

Sounds like a security thing, eh? Something is forbidden? That is, something is not permitted? Like, only certain attributes of the resource should be allowed when users submit some form data?

Let's check the docs; read the code sample on [this Omniref page](http://www.omniref.com/?q=strong%20parameters).

Let's follow that pattern. We need a private method that flags our project attributes as safe to be saved. We can use that method wherever we need the form data.

After that, your controller should look like this:

```ruby
class ProjectsController < ApplicationController
  def index
    @projects = Project.all
  end

  def new
    @project = Project.new
  end

  def create
    @project = Project.new(project_params)
    if @project.save
      flash[:notice] = "Project has been created."
      redirect_to @project
    else
      # we'll get to this in a bit
    end
  end

  private
    def project_params
      params.require(:project).permit(:name, :technologies_used)
    end
end
```

Pay careful attention to how the `params` are accessed when the `.create` method is actually called.
