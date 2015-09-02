
### ERROR:

    Undefined method `author' for #<Article:0x007f923c8a7e80> (or similar)

Right. We have not defined our `.author` method for an `Article`.

Our `@article` instance needs to know the associated user - in other words, who wrote the article (the author). We can use Rails associations to solve this problem.

It's time to *READ* about [Rails associations](http://guides.rubyonrails.org/v3.2.13/association_basics.html).

So, what kind of association do we need?

Since each user can write many articles, and each article belongs to just one user, we can use `has_many` and `belongs_to` to define the relationship.

But let's call the writer of an `article` its `author`. We can tell Rails to use a different name, but still expect a `User` object.

Modify your models as shown below.

Add to `article.rb`:

```ruby
belongs_to :author, class_name: "User"
```

Add to `user.rb`:
```ruby
has_many :articles, foreign_key: "author_id"
```
Run this spec again:

    $ ruby -Itest test/features/articles/creating_a_article_test.rb
