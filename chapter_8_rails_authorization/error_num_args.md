### ERROR:

    wrong number of arguments (1 for 0)

Our `sign_in` method in `test_helper.rb` doesn't have an argument for who to sign in. Modify it to accommodate, with a default to editor, so current tests still work:
```ruby
  def sign_in(role = :editor)
    visit new_user_session_path
    fill_in "Email", with: users(role).email
    fill_in "Password", with: "password"
    click_on "Sign in"
  end
```
