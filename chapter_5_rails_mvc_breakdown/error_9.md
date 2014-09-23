
### Error:

```
ActionView::Template::Error: First argument in form cannot contain nil or be empty
```

- Ok, that's fairly clear. We tried to call a method with a nil argument, and it doesn't like that. The method is the `form_for` method that helps us generate html for the new project form. The error is on line 3. We have: `form_for(@project)` in `app/views/projects/new.html.erb:3`
  - Let's look at the `form_for` docs:
    - `$ ri form_for` or visit http://www.omniref.com/?q=form_for
    - You should see a lot of good info, worth a cursory read

  - ok, form_for is expecting an object, but we haven't assigned anything to `@project` yet in our controller (where such things are supposed to transpire). `@project` is `nil`.
  - What should it be set to in the controller? How about a new instance of the Project class? Add this line to the `new` method in your Projects controller:
    ```ruby
    @project = Project.new
    ```
  - Here's MVC in action again! Controller uses the Model to get data for the View.
