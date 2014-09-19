### Error:
```
ActionView::Template::Error: undefined method `name' for nil:NilClass
```
- What is nil? (again)
  - @project is nil, we tried to access @project.name. Nil has no method called `name`.
  - we need to set the value in the Controller. How do we know which project to show? It's in the params hash, and it's called id.
    "  def show
        @project = Project.find(params[:id])
      end
    "
- OK, now your test has no errors! Celebrate!
- ...But it's failing because expected text is not there. Specifically, there is no notice that a project was successfully created. We need to add some code in to do that, and in Rails, this is called **the Flash**.
