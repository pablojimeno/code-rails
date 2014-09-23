
### ERROR:

    Undefined method `articles' for nil:NilClass

What is `nil`? Where exactly is that error occurring? Read the error output.

`app/controllers/posts_controller.rb`... what line number? What method?

The `articles` method is called on `current_user`

... but current_user is nil

... because no one is signed in yet!

Only signed-in users should be able to create articles.

Let's restrict some `ArticlesController` actions to signed-in users only, with a helper method from Devise. Add this line just under the `ArticlesController` class definition:

```ruby
    before_action :authenticate_user!, except: [:index, :show]
```

The `before_action will` run before any actions in the Controller are executed.

With the `:except` option, we can prevent the filter from running when the user requests index & show, since those actions can be publicly accessible.

Run the spec again:

    $ ruby -Itest test/features/posts/creating_a_post_test.rb
