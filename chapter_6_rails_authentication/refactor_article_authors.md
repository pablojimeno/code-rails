## REFACTOR: Article Authors

We aren't done yet! Check out what happens when we run `$ rake`.

### ERROR:

    undefined method `email' for nil:NilClass

The editing spec doesn’t know who the author is:

Let's add the author to the fixture, since it's assumed every `article` has an `author`. Use the proper user name from your fixtures:
```YAML
  cf:
    title: Code Fellows
    body: Means striving for excellence
    author: one

  cr:
    title: Code Rails
    body: This is how I learned web development
    author: one
```

Rails knows we mean a `User` when we specify the `author`. Cool, eh?

NOW... we have 1 Failure and 1 Error (still) because we are testing actions that require user sign in.

We can add our sign-in snipped to the start of each test (edit article and delete article):
```ruby
  visit new_user_session_path
  fill_in "Email", with: users(:one).email
  fill_in "Password", with: "password"
  click_on "Sign in"
```

Or, better yet... Let's move that snippet into `test_helper.rb`, in a method called `sign_in`. Now we can replace the 4 lines elsewhere with a simple call to: `sign_in`.

Try it all out in your browser. How's it look there? What else can you clean up or refactor?
