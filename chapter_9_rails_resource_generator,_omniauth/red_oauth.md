### RED: OAuth

Write out the user stories for logging in via Twitter.

We will give you specs for logging in via Twitter here. We're going to use a mock object, so that we don't have to actually connect via the internet to Twitter to test sign in.

What is a "mock"? The 7 year old slide deck, below, has some good info. Review the first 35 slides, follow the code examples to practice READING code, and get the most of it. The examples at the end of the slides are from older libraries, which are likely out of date. Don't spend too much time there.

http://jamesmead.org/talks/2007-07-09-introduction-to-mock-objects-in-ruby-at-lrug/

We're going to have to set some environment settings for Capybara, Devise, and Omniauth (included in code sample below).

Background article on OmniAuth's wiki: https://github.com/intridea/omniauth/wiki/Integration-Testing

Copy this code into near the end of `auth/sign_in_test.rb`:
```ruby
scenario "sign in with twitter works" do
  visit root_path
  click_on "Sign In"
  OmniAuth.config.test_mode = true
  Capybara.current_session.driver.request.env['devise.mapping'] = Devise.mappings[:user]
  Capybara.current_session.driver.request.env['omniauth.auth'] = OmniAuth.config.mock_auth[:twitter]
  OmniAuth.config.add_mock(:twitter,
                          {
                          uid: '12345',
                          info: { nickname: 'test_twitter_user'},
                          })
  click_on "Sign in with Twitter"
  save_and_open_page
  page.must_have_content "test_twitter_user, you are signed in!"
end

# Courtesy of: https://gist.github.com/ivanoats/7071730
# with help from https://github.com/intridea/omniauth/wiki/Integration-Testing
```



