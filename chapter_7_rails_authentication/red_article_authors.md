## RED: Article Authors

One way is that we can specify this by adding two lines to the bottom of our "Creating an Article" spec:

```ruby
page.has_css? "#author"
page.text.must_include users(:one).email # Use your fixture name here.
```

We can run just this one spec from our app root with:

    $ ruby -Itest test/features/articles/creating_a_article_test.rb

Let's see what we need to do, to get this going in the next section!
