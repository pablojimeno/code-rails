### Error:

```
ActionView::Template::Error: undefined method `name' for nil:NilClass
```

What part of our code could possibly be `nil` (again)?


**Hint**:

<span style="color: white;">
  @project is returning nil.
</span>

<span style="color: white;">
  We tried to access @project.name. Nil has no method called name.
</span>


We need to set the value in the controller action. How do we know which project to show? It's in the `params` hash, and it's called `id`.

Try it yourself, but if you're still getting an error with your test, then make sure your `show` action looks like this:
<pre style="color: #f7f7f7; font-size: 1.1em;">
<code>
def show
  @project = Project.find(params[:id])
end
</code>
</pre>

OK, now your test has no errors, but your test is **failing**.

Celebrate!
