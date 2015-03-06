### Error:

    AbstractController::ActionNotFound: The action 'edit' could not be found for ProjectsController



We know what to do here, right? You need to add a another action in your controller.

Add an `edit` action to the `ProjectsController` - very similar to what you did before.

```ruby
def edit
end
```

Run the test again to see if that gets us to the next error...
