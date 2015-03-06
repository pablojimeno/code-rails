
### Error:

```
ActionView::Template::Error: First argument in form cannot contain nil or be empty
```

OK, that's fairly clear. We tried to call a method with a `nil` argument, and it doesn't like that. The method is the `form_for` method that helps us generate HTML for the "New Project" form. The error is thrown on line 3.

We have:

`form_for(@project)` in `app/views/projects/new.html.erb:3`

Let's look at the `form_for` docs:

    $ ri form_for

You can also find the docs on the web. For example, you could [search for form_for on Omniref](http://www.omniref.com/?q=form_for).

You should see a lot of good info, and it's worth a cursory read.

OK, `form_for` is expecting an object, but we haven't assigned anything to `@project` yet in our Controller action (where such things are supposed to transpire). Therefore, `@project` is `nil`.

What should it be set to in the Controller? How about a new instance of the Project class? Add this line to the `new` method in your projects controller:

```ruby
@project = Project.new
```

Here's MVC in action again! The Controller gets data from the Model and hands it to the View.
