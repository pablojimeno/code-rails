# MulitOauth (example with: Github)

Now you can sign in to your app with Twitter!
While Twitter is a great way to authenticate people into your app, what if you want to identify a user by their email?  Twitter doesn't send one back your app.

We have a couple of options.  We can setup ask the user to provide an email (and log into an existing account on our app) or we can use a differenct service.  Infact, we can use as many servies as we want and the setup is pretty darn simple, since we've already done most of it for Twitter.

Lets set it up with Github

``` ruby
gem 'omniauth-github'
```

In the previous section we used forman as our server.  If you didn't like that particular gem, now is your chance change to Pow.  (Don't forget to get Powder with it)

http://pow.cx/ (only for macs)

Register your app with Github
`https://github.com/settings/developers`

use `http://127.0.0.1:3000/users/auth/github/callback`

configure your devise initializer for github
``` ruby
config.omniauth :github, ENV['GITHUB_ID'], ENV['GITHUB_SECRET']
```

Remember to set these environement variables in your .env file if you have one.  (check out gem dot_env if you don't)

Next, you will have to revise your the methods in your user model to be used for all your omniauth callbacks (this time we are going to compare the information given to use by the Auth service with the email in our database)

```ruby
  def self.from_omniauth(auth)
    auth_search = { email: auth.info.email }

    where(auth_search).first_or_create do |user|
      user.provider = auth.provider
      user.uid =  auth.uid
      user.username = auth.info.nickname
      user.email = auth.info.email
    end
  end
```

That should do it!!!
