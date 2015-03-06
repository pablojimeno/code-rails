### Error:

    E

    Finished tests in 0.013497s, 74.0905 tests/s, 0.0000 assertions/s.

      1) Error:
    As the site owner, I want to add a portfolio item so that I can show off my work Feature Test#test_0001_adding a new project:
    NameError: undefined local variable or method `projects_path' for #<#<Class:0x007fbd6cb0fe60>:0x007fbd6d9ff740>
        test/features/projects/creating_a_project_test.rb:5:in `block (2 levels) in <main>'

    1 tests, 0 assertions, 0 failures, 1 errors, 0 skips"

#### Let's break it down.

**The actual exception that was raised:**

```
NameError:
```

**The error message:**

```
undefined local variable or method `projects_path' for #<#<Class:0x007fbd6cb0fe60>:0x007fbd6d9ff740>
```

**The file and line number where the error occurred:**

```
test/features/projects/creating_a_project_test.rb:5:in `block (2 levels) in <main>
```

So what's that mean? Rails doesn't yet have any awareness of the `projects_path` url helper.

We can fix that! We know we need to add a new resource called Project. So we can tell Rails that this will be a RESTful resource.

Adding a line in `config/routes.rb` will make Rails aware of our CRUD paths, and give us the path helper we need to move past the current error. Just put in this line:

```ruby
  resources :projects
```

Run the test again. Do you now see a different error?
