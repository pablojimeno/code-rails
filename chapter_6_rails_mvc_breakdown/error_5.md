### Error:

```
ActionView::Template::Error: undefined method `each' for nil:NilClass
```

What is coming up as `nil`? Something in our template *should* have a value, but does not.

`@projects` is `nil`, because we haven't put anything in the `@projects` array yet!

We need to fill in the value of `@projects`. The proper place to do this is in the `ProjectsController`.

In the `ProjectsController`, inside the index method, what should you put? We want to get ALL projects from the database, with an `ActiveRecord` query like `@projects = Project.all`.

```ruby
class ProjectsController < ApplicationController
  def index
    @projects = Project.all
  end
end
```

Run the test again...
