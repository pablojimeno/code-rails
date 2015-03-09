### Error:

```
The action 'new' could not be found for ProjectsController
```

Good news! Capybara has made it past the "index" page, to the "New Project" page.

Hmmm, this error sounds like when the index action was missing a few lines back up in our test.

Right now, we expect there to be a form for the user to fill out to create a new project, right? How do we set up that controller action?

 Put a new method in the `ProjectsController`:

```ruby
def new
end
```

Run the test again... (I'll stop saying that now. Whenever you change the code, just run the test again!)

