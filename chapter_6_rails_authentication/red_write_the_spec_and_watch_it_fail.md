## RED: write the spec and watch it fail
Generate a spec feature:

**Hint**:
<pre style="color: #f7f7f7">
  $ rails g minitest:feature auth/sign_up
</pre>

##### A Good Strategy:
You'll probably need to write your spec to conform to the Devise defaults. Don't focus on customizing Devise just yet. Adjust your specs as you go to match the flow Devise is expecting. Test along in your browser as needed.

Example Spec:
<pre style="color: #f7f7f7">
<code>
require "test_helper"

feature("
  As a site visitor, I want to be able to sign up for an account,
  so that I can perform actions that require me to be logged in.
") do
  scenario "sign up" do
    # Given a registration form
    visit "/"
    click_on "Sign Up"

    # When I register with valid info
    fill_in "Email", with: "test@example.com"
    fill_in "Password", with: "password"
    fill_in "Password confirmation", with: "password"
    click_on "Sign up"

    # Then I should be signed up
    page.must_have_content "Welcome! You have signed up successfully"
    page.wont_have_content "There was a problem with your sign up"
  end
end
</code>
</pre>

