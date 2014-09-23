
### ERROR:

    Unable to find field "Title"

What line is that from?! Huh? An earlier part of our test is now failing?

Since we need to be signed in before creating an article, Capybara isn't even seeing the form. Modify the test to sign in our fixture user before creating the test. Add something like (remember, type it, don't copy/paste):

```ruby
  # Given an authorized user complets a new post form
  visit new_user_session_path
  fill_in "Email", with: users(:one).email
  fill_in "Password", with: "password"
  click_on "Sign in"

  visit new_article_path
```
Hmm, we already had a few lines of code that looked just like that. Chance to refactor in a few minutes!

Run the spec just for this file again!
