# Deploy to Heroku

Follow this guide to get your app up and running on Heroku:

https://devcenter.heroku.com/articles/getting-started-with-rails4

<br />
**Hints & Troubleshooting**:

* One really important step that is left out of that article is that you need to tell Rails that it is ok to serve static assets, which Rails 4 will not do by default. If you don't do that, your website images will seem to vanish over time.

* Find these settings in the Production Environment config file (`config/environments/production.rb`), which is used on Heroku, and set them to true - `config.serve_static_files` and `config.assets.digest`

* Some steps you have already done (generating your app, initializing the git repo, etc), so be sure not to blindly copy/paste.

* FOR THE LOVE OF CLARITY, please name your Heroku app when you create it:

       $ heroku create my-rad-portfolio

* Did you include the `rails_12factor` gem in production?

* Heroku can't use SQLite for it's database. It needs PostreSQL.

* Did you include the 'pg' gem?

* You have 2 options:

  1. Switch to Postgres, locally. This WILL BE time consuming to set up if you haven't already, but you'll want to do it eventually. Go for it now ONLY IF you have the time. Skip it for now if you are feeling pressed, we can help you later on. If you decide to the least painful way is to follow this post by Ivan.
https://www.codefellows.org/blog/three-battle-tested-ways-to-install-postgresql

  2. Use SQLite locally (in development), and Postgres on Heroku (in production).

* Create a gem group called :production, and include:

      gem "pg"

* Did you move SQLite to development only?

* Do you have minitest-rails available in all environments?

* Did you run migrations after deploying?

      $ heroku run rake db:migrate

* If you're using Google Fonts and run into issues with it loading, either change the protocol from `http://fonts...` to `https://fonts...`, or leave the protocol out and just do `//fonts...`

**Hint**:

A working Rails 4.0 Gemfile:

```ruby
source "https://rubygems.org"

ruby "2.1.0"

gem "coffee-rails", "~> 4.0.0"
gem "jbuilder", "~> 1.2"
gem "jquery-rails"
gem "minitest-rails"
gem "rails", "4.0.2"
gem "sass-rails", "~> 4.0.0"
gem "turbolinks"
gem "uglifier", ">= 1.3.0"
gem "foundation-rails"

group :development do
  gem "sqlite3"
end

group :doc do
  gem "sdoc", require: false
end

group :production do
  gem "rails_12factor"
  gem "pg"
end

group :test do
  gem "minitest-rails-capybara"
  gem "launchy"
end
```
