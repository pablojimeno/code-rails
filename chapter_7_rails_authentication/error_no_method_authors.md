
### ERROR:

    Undefined method `articles' for nil:NilClass

What is `nil`? Where exactly is that error occurring? Read the error output.

It's in `app/controllers/articles_controller.rb`. What line number? What method?

The `articles` method is called on `current_user`...

... but, `current_user` is `nil`...

... because no one is signed in yet!

Only signed-in users should be able to create articles.

Let's restrict some `ArticlesController` actions to signed-in users only, with a helper method from Devise. Add this line just under the `ArticlesController` class definition:

```ruby
before_action :authenticate_user!, except: [:index, :show]
```

The `before_action` in Rails will run before any actions in the Controller are executed.

With the `:except` option, we can prevent the filter from running when the user requests `index` and `show`, since those actions can be publicly accessible.

Run the spec again:

    $ ruby -Itest test/features/articles/creating_a_article_test.rb
