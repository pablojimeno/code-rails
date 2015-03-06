### Error:

```
ActionController::RoutingError: uninitialized constant ProjectsController
```

Rails doesn't know what `ProjectsController` means!

Create a new file named `projects_controller.rb` in `app/controllers/`

```ruby
class ProjectsController < ApplicationController
end
```

Be careful with pluralization - a fundamental convention in Rails!

Run the test again ...
