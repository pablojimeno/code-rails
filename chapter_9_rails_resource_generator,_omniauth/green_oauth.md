# GREEN: OAuth

You have the feature spec'd out, so you are now ready to write code. 

Use your test to guide you, and hints from the path here help you when you are stuck.

### Here is the *Path*:

Add the `omniauth-twitter` gem to your Gemfile:

```ruby
gem 'omniauth-twitter'
```

We're going to need to use environment variables to store our Twitter credentials on Heroku, so we might as well start using them in development. This is a Rails best practice - **do not check sensitive info into a Git repository**.

The `dotenv` and Figaro gems help with this. Actually, this is a good time to start using Foreman, a way to start up your Rails server and any other processes it might depend on. It uses `dotenv` for configuration management.

Add the Foreman gem to your system, not to your Gemfile:

    $ gem install foreman

Now read up on [what it does and how it works](http://mauricio.github.io/2014/02/09/foreman-and-environment-variables.html).

Do not miss the "Isolating the configuration" section of that article, as that is most relevant for us.

#### Create a Twitter App

1. Visit this page on Twitter to get started:

    https://dev.twitter.com/apps/new

- Use http://127.0.0.1:3000/users/auth/twitter/callback as the callback URL. Using "localhost" instead of the special IP will not validate.

- After your Twitter app is created, you'll have to edit the app's settings and check off "Allow this application to be used to sign in with twitter."

- For some reason you may have to save the setting twice. Go back and double check that the check-box is ***really*** checked. This seems to be a long-standing bug with Twitter.

- Copy the consumer key and consumer secret into your `.env` file (or `config/application.yml` if you are using Figaro).

<br />

#### Adjust Devise's configuration

In `config/initializers/devise.rb`, add:

```ruby
config.omniauth :twitter, Rails.application.secrets.twitter_key, Rails.application.secrets.twitter_secret
```

Go to `config/secrets.yml` and under development, set `twitter_key` and `twitter_secret` to load from system ENV vars.

Add Devise's `:omniauthable` module to the `devise` line in `app/models/user.rb`.

You'll now see a <u>sign in with twitter link</u> on `http://localhost:3000/users/sign_in`. (Thanks, Devise!)

We may want to put the link in the main nav, but let's get our functionality working first, before we worry about presentation.

If you try to sign in now, you'll see:

  > "The action 'twitter' could not be found for Devise::OmniauthCallbacksController"

We'll fix that by running:

    $ rails g controller omniauth_callbacks --skip-test-framework
    $ rails g migration add_omniauth_to_users provider uid name


... and adding this code to `config/routes.rb` in the `devise_for` line:

```ruby
controllers: {omniauth_callbacks: "omniauth_callbacks"}
```

Follow the rest of the steps from RailsCast Episode #235 (revised), except you will also need to add in `app/models/user.rb`:

```ruby
user.name = auth.info.nickname
```
instead of user.username (depends on your app). Also:

```ruby
user.email = "#{user.name}-CHANGEME@twitter.example.com"
```

Since devise *requires* an email for an new user (through model validations), we have to assign a fake one that the user can change later.

A handful of methods will be useful in the User model:

```ruby
def self.from_omniauth(auth)
  where(provider: auth.provider, uid: auth.id).first_or_create do |user|
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

Your `app/controllers/omniauth_callbacks_controller.rb` should look like this:

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

Modify `app/views/devise/registrations/new.html.erb` to include an `if` statement around the password fields; the user doesn't need to enter a password and confirmation *if* the user is signing in with Twitter.

Also, modify the `registrations/edit.html.erb` to include an `if` statement around the password fields.

Now, your registration views should look something like this:

```html
<h2>Edit <%= resource_name.to_s.humanize %></h2>

<%= form_for(resource, :as => resource_name, :url => registration_path(resource_name), :html => { :method => :put }) do |f| %>
  <%= devise_error_messages! %>

  <div><%= f.label :email %><br />
  <%= f.email_field :email, :autofocus => true %></div>

  <% if devise_mapping.confirmable? && resource.pending_reconfirmation? %>
    <div>Currently waiting confirmation for: <%= resource.unconfirmed_email %></div>
  <% end %>

  <div><%= f.label :password %> <i>(leave blank if you don't want to change it)</i><br />
  <%= f.password_field :password, :autocomplete => "off" %></div>

  <div><%= f.label :password_confirmation %><br />
  <%= f.password_field :password_confirmation %></div>
  <% if f.object.encrypted_password.present? %>
    <div><%= f.label :current_password %> <i>(we need your current password to confirm your changes)</i><br />
    <%= f.password_field :current_password %></div>
  <% end %>

  <div><%= f.submit "Update" %></div>
<% end %>

<h3>Cancel my account</h3>

<p>Unhappy? <%= button_to "Cancel my account", registration_path(resource_name), :data => { :confirm => "Are you sure?" }, :method => :delete %></p>

<%= link_to "Back", :back %>
```

