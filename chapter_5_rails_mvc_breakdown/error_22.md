
### Error:

    AbstractController::ActionNotFound: The action 'update' could not be found for ProjectsController

We did not need to do anything to get the same form partial to have a different button text. How did Rails know to change it?


####This is how the form works

In the new form, the `@project` object is a new object, and so:

    @project.new_record? == true

When the form is rendered in the edit action, we are using an object we got from the DB, so:

    @project.new_record? == false

Rails handles the button text for us, thanks to the [`form_for` method](http://api.rubyonrails.org/classes/ActionView/Helpers/FormHelper.html#method-i-form_for). Thanks, Rails!

####Now, to get passed the error:

Submitting the same form, when in edit mode, now goes to the `ProjectsController#update` action, instead of `#create`. Let's add that action.

```ruby
  def update
  end
```

Run the specs again.
