### Error:

```
AbstractController::ActionNotFound: The action 'create' could not be found for ProjectsController
```
- More progress! Capybara is now trying to submit our form data to the create action! Therefore... What do we need next?
- You should know the drill by now, add that action in the controller! But this time, the method is going to need to be a bit different:
  ```ruby
    def create
      @project = Project.new(params[:project])
      if @project.save
        flash[:notice] = "Project has been created."
        redirect_to @project
      else
       # we'll get to this in a bit
      end
    end
 ```
- Can you read that code clearly enough to understand what it is doing?
- What kind of value does `@project.save?` return?
