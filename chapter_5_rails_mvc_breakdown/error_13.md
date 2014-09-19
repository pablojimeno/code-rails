### Error:

```
ActionView::MissingTemplate: Missing template projects/show, application/show with {:locale=>[:en], :formats=>[:html], :handlers=>[:erb, :builder, :raw, :ruby, :jbuilder, :coffee]}.
```
- You know the drill! Create the view file for the show action
  ```html
  <h2><%= @project.name %></h2>
  <p>Technologies used: <%=@project.technologies_used %></p>
  ```
- What directory does the file go in?
- What should the file be called?
