### Error:

    The action 'edit' could not be found for ProjectsController

We know what to do here, right? You need to add a another action in your controller. Add this method to your controller's existing contents (`app/controllers/projects_controller.rb`).
```ruby
    def edit

    end
```
Run the test again to see if that gets us to the next error...
