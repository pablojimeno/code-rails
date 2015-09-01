### ERROR:

    undefined method `published' for #<Article:0x007ffef4275ad8>

Generate a migration that adds a 'published' attribute to the articles table.

    $ rails generate migration add_published_to_articles published:boolean

How's the generated migration look? Good?

    $ rake db:migrate test:prepare

Run the test again. Why is it still failing? The attribute is in the form, in the view, and in the database. Shouldn't Rails just put the pieces together?

Let's troubleshoot. What does `save_and_open_page` show you about the article's "status"?

Are you properly checking the checkbox in the form? `save_and_open_page` can show this as well.

If all looks well, let's take a look at the last 200 lines or so of the test log file, immediately after running this one test (NB: that's NOT `rake`):

    $ tail -n200 log/test.log

Scroll back through the logs until you find the details about the article creation. For real, do this now. Learning to read the server logs is a clutch troubleshooting skill. It can look like a lot of intimidating gobbletygook, but if you read it carefully, you'll see Rails is reporting exactly what is going on. That's often very useful!

Look for something like the following in the output:

    Processing by ArticlesController#create

Does the `params` hash include the `published` attribute?

    "published" => "1"

Why isn't it getting saved? What does the log report next?

Did you notice the line:

    Unpermitted parameters: published

How do we fix that? We need to `permit` the `published` parameter!

Where do we do that? How do we allow it only for editors, and not authors?

The controller is the only part of MVC that is session-aware. We need one additional `param` permitted, if the user is an editor.

Ruby allows lists to end with a comma - that means we can conditionally add a final item to our `article_params` method:

```ruby
params.require(:article).permit(:title, :body, (:published if current_user.role == "editor"))
```
