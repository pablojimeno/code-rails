### Error:

```
ActiveModel::ForbiddenAttributesError
```
- Sounds like a security thing, eh? Like, only certain attributes should be allowed when users submit form data?
- Let's check the docs
    - Read the code sample here: http://www.omniref.com/?q=strong%20parameters
- Let's follow that pattern. We need a private method that flags our project attributes as safe to be saved. We can use that method wherever we need the form data.
- In the end, your controller should look like this:
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

Pay careful attention to how the params are accessed when the .create method is actually called.
