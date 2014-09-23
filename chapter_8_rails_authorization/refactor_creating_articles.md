
## REFACTOR Creating Articles

This is key. In 2 different places, we did a literal check of the value of `current_user.role` to permit a behavior. This is a code smell. We really want to know if the user has publishing permission. In the future, that may not be just editors. Our implementation is exposed.

How can we refactor the check on publishing policy? With the number of checks we will need to do throughout our app, this is really important to get right. Let's encapsulate that behavior in an object. We should be able to ask an `ArticlePolicy` object, given the `current_user` and an `@article`, if publishing is allowed.

```ruby
  if ArticlePolicy.new(current_user, @article).publish?
```

Then we can keep the implementation in a single place for better maintainability. The new code is not shorter, but it is Better with a capital B! :] What does the implementation look like?

We can create a PORO (plain old ruby object) in a new directory, `app/policies`. We should have one policy file for each Resource in our app. `article_policy.rb` should define a `publish?` method to encapsulate our business logic:
```ruby
  class ArticlePolicy
    attr_accessor :user, :article

    def initialize(user, article)
      @user = user
      @article = article
    end

    def publish?
      @user.role == "editor"
    end
  end
```

Try that out! Is your test still passing, if you use the `ArticlePolicy` object to check publish permission?


So, we will still have our code littered with instantiations of `ArticlePolicy`, and passing in `current_user`. Wouldn't it be nice if we had a short-hand way to access the policy method, operating under the convention of `current_user`?
Enter the Pundit gem!

## Pundit Gem

- Read the Pundit Gem README: https://github.com/elabs/pundit
- Another possibly useful resource: Pundit Gem sections of The Rails 4 way: http://hijk.it/0U0v37360312
- Install the gem, and refactor your permission checks according to Pundit conventions.

        $ rails generate pundit:policy article

IMPORTANT: edit this policy class include a `create?` policy and `publish?` policy (and others eventually). Check the README for hints on implementation. This is the ***meat*** of this chapter's exercise; without a policy all of the other behaviors will be much more tedious!

## Further Refactors
  - Fix your fixtures by adding `published: true` to the existing fixtures.
  - Optional, but recommended: add an index for the published column in your database for better database performance
  - We'll need to do fairly often checks on the user's role. Add some utility methods to the `User` class for `.author?` and `.editor?`.

```ruby
  def author?
      role == 'author'
  end

  def editor?
      role == 'editor'
  end
```

Now you can clean up that ArticlePolicy a little:
```ruby
  def publish?
    @user.editor?
  end
```
