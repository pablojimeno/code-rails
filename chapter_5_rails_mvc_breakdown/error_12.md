### Error:

```
AbstractController::ActionNotFound: The action 'show' could not be found for ProjectsController
```

Once a new `Project` instance is created and saved to the database, we want to "show" it to the user for verification. That's why the `create` action redirects to the `show` action. However, we haven't defined the `show` action yet.

Read more about the `redirct_to` method:
- [`redirect_to` method in the Rails API docs](http://api.rubyonrails.org/classes/ActionController/Redirecting.html)

- [Search for the `redirect_to` method on Omniref](http://www.omniref.com/?q=redirect_to)

Now is the time for you to create the show method in your `ProjectsController`.

Can you do it without a hint?

**Hint**:

The method name should be:

<pre style="color: #f7f7f7; font-size: 1.4em;">
  show
</pre>

With your new method, the controller should look like this:

<pre style="color: #f7f7f7; font-size: 1.1em;">
<code>
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
      [we'll get to this in a minute]
    end
  end

  def show

  end

  private
    def project_params
      params.require(:project).permit(:name, :technologies_used)
    end
end
</code>
</pre>
