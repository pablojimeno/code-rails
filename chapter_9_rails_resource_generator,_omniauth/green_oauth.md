### GREEN: OAuth

###Here is the *Path*:


Add the `omniauth-twitter` gem to your Gemfile:

    gem 'omniauth-twitter'

We're going to need to use environment variables to store our Twitter credentials on Heroku, so we might as well start using them in development. This is a Rails best practice - **do not check sensitive info into a git repository**.

The Figaro gem makes this easy. (Alternatives are dotenv and Foreman). Add the figaro gem:

    gem 'figaro'

Install the figaro (generate some files in your app):

    $ bundle
    $ rails generate figaro:install

Check out the files that it generated.

<br />


#### Create a Twitter App

- Visit this page on Twitter to get started: https://dev.twitter.com/apps/new

- Use http://127.0.0.1:3000/users/auth/twitter/callback as the callback URL. Using "localhost" instead of the special IP will not validate.

- After the app is created, you'll have to edit the app's settings and check off "Allow this application to be used to sign in with twitter".

- For some reason you may have to save the setting twice. Double check that the check-box is ***really*** checked.

- Copy the consumer key and consumer secret into your `config/application.yml` (or `.env` file, depending on which gem you're using).

<br />

#### Adjust Devise's configuration

In `config/initializers/devise.rb`, add:

```ruby
config.omniauth :twitter, ENV["TWITTER_CONSUMER_KEY"], ENV["TWITTER_CONSUMER_SECRET"]
```

Add `:omniauthable` to the `devise` line in `app/models/user.rb`.

You'll now see a <u>sign in with twitter link</u> on http://localhost:3000/users/sign_in. We may put the link in the main nav, but let's get it working first.

If you try to sign in now, you'll see:

  > "The action 'twitter' could not be found for Devise::OmniauthCallbacksController"

We'll fix that by running:

    $ rails g controller omniauth_callbacks --skip-test-framework
    $ rails g migration add_omniauth_to_users provider uid


... and adding this code to `config/routes.rb` in the `devise_for` line:

```ruby
controllers: {omniauth_callbacks: "omniauth_callbacks"}
```

You may already have a hash there if you're using `strong_parameters` in Rails 3.

Follow rest of steps from Railscast #235 (revised), except you will also need to add in `app/models/user.rb`:

```ruby
user.name = auth.info.nickname #(instead of user.username; depends on your app)
user.email = "#{user.name}-CHANGEME@twitter.example.com"
```
Since devise requires an email, we have to assign a fake one that the user can change later.

https://gist.github.com/ivanoats/7076128
```ruby
def self.from_omniauth(auth)
  where(auth.slice(:provider, :uid)).first_or_create do |user|
    user.provider = auth.provider
    user.uid = auth.uid
    user.name = auth.info.nickname
    user.email = "#{user.name}-CHANGEME@twitter.example.com"
  end
end

def self.new_with_session(params, session)
  if session["devise.user_attributes"]
    new(session["devise.user_attributes"], without_protection: true) do |user|
      user.attributes = params
      user.valid?
    end
  else
    super
  end
end

def password_required?
  super && provider.blank?
end

def update_with_password(params, *options)
  if encrypted_password.blank?
    update_attributes(params, *options)
  else
    super
  end
end
```

Your `app/controllers/omniauth_callbacks_controller` should look like this:

https://gist.github.com/ivanoats/7076144
```ruby
class OmniauthCallbacksController < ApplicationController
  def all
    user = User.from_omniauth(request.env["omniauth.auth"])
    if user.persisted?
      flash.notice = "#{user.name}, you are signed in!"
      sign_in_and_redirect user, notice: "#{user.name}, you are signed in!"
    else
      session["devise.user_attributes"] = user.attributes
      redirect_to new_user_registration_url
    end
  end
  alias_method :twitter, :all
end
```


Modify `app/views/devise/registrations/new.html.erb` to include an `if` statement around the password fields.

https://gist.github.com/ivanoats/7076164

Modify `registrations/edit.html.erb` to include an `if` statement around the password fields.

https://gist.github.com/ivanoats/7076257


