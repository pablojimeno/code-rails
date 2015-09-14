### RED: OAuth

Write out the user stories for logging in via Twitter.

We will give you specs for logging in via Twitter here. We're going to use a mock object, so that we don't have to actually connect via the internet and Twitter to test sign in.

#### What is a "mock"?

The 7 year old slide deck, below, has some good info. Review the first 35 slides, follow the code examples to practice **READING** code, and get the most of it. The examples at the end of the slides are from older libraries, which are likely out of date. Don't spend too much time there.

http://jamesmead.org/talks/2007-07-09-introduction-to-mock-objects-in-ruby-at-lrug/

Can you tell why it is we want to mock out the Twitter component?

We're going to have to set some environment settings for Capybara, Devise, and Omniauth (included in the code sample below).

Background article on OmniAuth's wiki:

https://github.com/intridea/omniauth/wiki/Integration-Testing

Copy this code near the end of `auth/sign_in_test.rb`:

```ruby
scenario "sign in with twitter works" do
  OmniAuth.config.test_mode = true
  OmniAuth.config.add_mock(:twitter,
                          {
                          uid: '12345',
                          info: { nickname: 'test_twitter_user'},
                          })
  visit root_path
  Capybara.current_session.driver.request.env['devise.mapping'] = Devise.mappings[:user]
  Capybara.current_session.driver.request.env['omniauth.auth'] = OmniAuth.config.mock_auth[:twitter]

  click_on "Sign in with Twitter"
  page.must_have_content "Logged in as test_twitter_user"
end

# Courtesy of: https://gist.github.com/ivanoats/7071730
# with help from https://github.com/intridea/omniauth/wiki/Integration-Testing
```



