
### Error:
```
AbstractController::ActionNotFound: The action 'index' could not be found for ProjectsController
```

Your `ProjectsController` doesn't have an `index` action!

So we can just add an index method in the ProjectsController class:

```ruby
class ProjectsController < ApplicationController
  def index
  end
end
```

Run the test again ...
