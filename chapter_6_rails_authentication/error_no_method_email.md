### ERROR:

    undefined method `email' for nil:NilClass

What is `nil` in this error message? That error says we tried to send `nil` the message `email`. (`nil` is an instance of `NilClass`).

What is returning `nil` in this case? It's `author`, right? So, our article knows it should have an author, but it doesn't have one.

We want the currently signed in user to be the author.  So let's edit our `ArticlesControlle`r's `create` method.

Immediately after the new article is successfully saved, add:

```ruby
current_user.articles << @article
```

Run the test again:

    $ ruby -Itest test/features/articles/creating_a_article_test.rb
