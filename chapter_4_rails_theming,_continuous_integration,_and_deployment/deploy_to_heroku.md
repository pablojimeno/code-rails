# Deploy to Heroku
Read and do (with your app):<br> https://devcenter.heroku.com/articles/getting-started-with-rails4<br>

HINTS & Troubleshooting:<br>
* One really important step that is left out of that article is that you need to tell Rails that it is ok to serve static assets, which Rails 4 will not do by default.
Find this setting in the Production Environment config file, which is used on Heroku: config/environments/production.rb
Change it to true.<br>

* Some steps you have already done (generating your app, initializing the git repo, etc), so be sure not to blindly copy/paste.<br>

* FOR THE LOVE OF CLARITY, please name your heroku app when you create it:

        heroku create my-rad-portfolio

* Did you include the 'rails_12factor' gem in production?<br>
* Heroku can't use SQLite for it's database. It needs PostreSQL.
    * Did you include the 'pg' gem?<br>
    * You have 2 options
        * Switch to Postgres locally: This WILL BE time consuming to set up if you haven't already, but you'll want to do it eventually. Go for it now ONLY IF you have the time. Skip it for now if you are feeling pressed, we can help you later on. If you decide to the least painful way is to follow this post by Ivan:<br> https://www.codefellows.org/blog/three-battle-tested-ways-to-install-postgresql
        * Use SQLite locally (in development), and Postgres on Heroku (production):
            * Create a gem group called :production, and include:

                    gem "pg"

            * Did you move sqlite to development only?
* Do you have minitest-rails available in all environments?
* Did you run migrations after deploying?
        heroku run rake db:migrate
Hint:<br>
A working Rails 4.0 Gemfile:
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

        group :produciton do
          gem "rails_12factor"
          gem "pg"
        end

        group :test do
          gem "minitest-rails-capybara"
          gem "launchy"
        end
