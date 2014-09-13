# Chapter 4: Rails Theming, Continuous Integration, and Deployment

## Intro:
On day four, we cover two main things: making your site look good, and sharing (deploying) your site to the internet. A bonus is that since we have been doing BDD, we can deploy based on whether our tests pass.

Review this whole outline, and find the user stories. Add them to your project management tool now.

As an employer, I want to see impressive visual design so that I know this developer has good taste

## RESEARCH
Let's learn a little about front-end frameworks.

#Read this short article on what front-end frameworks matter: https://medium.com/what-i-learned-building/99fdd6e46586
Twitter Bootstrap and Zurb Foundation are the 2 most popular front-end frameworks
Review the READMEs & docs for each:

https://github.com/twbs/bootstrap/

https://github.com/zurb/foundation

#Read these use-cases for a front-end framework (pretty much applies to both): http://www.sitepoint.com/11-reasons-to-use-twitter-bootstrap/
#Read this to understand the philosopical differences between Bootstrap and Foundation: https://medium.com/frontend-and-beyond/8b3812c7007c
We want you to use Zurb. Why do you think that is?
Practice with Zurb:
#Assignment: Watch and do: http://railscasts.com/episodes/417-foundation?view=asciicast. Push your resulting app to Github.
Hints:
This RailsCast is done with Rails 3.2. So you have some options:
Use Rails 3.2.13
> gem install rails -v 3.2.13
> rails _3.2.13_ new [appname]
Ensure you match all the other gem versions.
If you really get stuck, clone the finished app from GitHub, and just follow along closely with the code.
Use Rails 4.1, and try to figure out what is different
If you get stuck, use this as a reference: https://github.com/RailsApps/rails-foundation/
If you are using Rails 4 and Foundation 5, things may not work exactly as detailed in the RailsCast. Try this thread if you are having issues with the `@import` command: https://github.com/zurb/foundation/issues/2128 (Yikes!)
Note in Rails 4, you don't need to put gems in the :asset group: http://stackoverflow.com/questions/16406204/why-did-rails4-drop-support-for-assets-group-in-the-gemfile
To use the latest Foundation 5, the gem name is "foundation-rails": http://foundation.zurb.com/docs/upgrading.html
When the RailsCast suggests changing css values, put in your own values to see the change and get something you like.
RED
As a developer, I want a front-end framework so that I can easily modify the look and feel of my site
Write a spec to check for zurb foundation loading on root_path.
Path:
rails generate minitest:feature CheckForZurb
What can you look for your on your page to indicate that Zurb is in effect?
Hint:
One option would be to check for 'columns' in the page.body.
Better would be to see if a stylesheet with "zurb" in the name was getting loaded.
Please share if you come up with a better test!
GREEN
Add the zurb-foundation gem
Follow instructions in the README for the gem
Hints
You'll need to load in the javascript and stylesheets into your asset pipeline.
For more info on the asset pipeline, please #Read: http://guides.rubyonrails.org/asset_pipeline.html
REFACTOR
As a developer, I want to integrate a theme, so that my site doesn't look like all the other bootstrap sites out there
RED
The RailsCast is essentially building up a custom theme. If you like that approach, and have the css chops already, keep going with it to make your site look the way you want it.
Here's some nice Creative Commons images you can use as background: http://unsplash.com/
Otherwise, choose a theme:
Here are some collections of Zurb themes... You may also be able to find your own. Paying $5-$40 for a professionally designed theme is a good deal and a great time saver.
ONLY USE A THEME THAT MATCHES YOUR FOUNDATION VERSION. Look closely at what version of Foundation it is based on. Do not proceed if you do not have a match with your app.
http://themeforest.net/collections/3083675-sweet-zurb-foundation-themes (Avoid the joomla/drupal/wordpress options, you want just HTML5 + CSS3)
https://www.foundationmade.com/themes/all/sort/newest/page/1 (look for Zurb 5 templates)
http://www.themplio.com/categories/foundation-free (these aren't as nice, but they are free)
...and whatever you find. Google away, and share your best finds with the class!
Write a spec to verify the theme loads properly. What does your theme do that you can test for? You may need to look into the theme code to find out. Don't be afraid of coming back and re-writing this test once you have the theme loaded.
GREEN
Add the theme's files to the appropriate places in the Rails file hierarchy
#Read again if needed: The Rails Asset Pipeline Guide, especially section 2.1: http://guides.rubyonrails.org/asset_pipeline.html
Remember, "assets" are the css, js, image, etc files your site uses.
The theme you selected should simply have html/css/js/images that you need to extract from the theme and add to your Rails app. Copy/paste is ok here!
Some things belong in app/assets and others in vendor/assets - what is the difference?
REFACTOR
How can you customize your downloaded theme and make it stand out from the crowd?
At least add some copy unique to who you are and what you want your site to be about (hint: you!)
Option 1: If you have time, do it!
Option 2: If you don't end up with time, enter in some user stories into the Project Management site to remind yourself in the future what you'd like to customize.
As a parent, I want to see the good work my kid does so that I can show it off to my friends
Add additional spec that is modification of the day 1 welcome_page_spec, but checks instead against your public domain name.
This will essentially be a ping-test to ensure your app is up and running in production.
Deploy to Heroku
#Read and do (with your app) : https://devcenter.heroku.com/articles/getting-started-with-rails4
HINTS & Troubleshooting:
One REALLY important step is left out of that article:
You need to tell Rails that it is ok to serve static assets, which Rails 4 will not do by default.
Find this setting in the Production Environment config file, which is used on Heroku: config/environments/production.rb
Change it to true.
Some steps you have already done (generating your app, initializing the git repo, etc), so be sure not to blindly copy/paste.
FOR THE LOVE OF CLARITY, please name your heroku app when you create it:
heroku create my-rad-portfolio
Did you include the 'rails_12factor' gem in production?
Heroku can't use SQLite for it's database. It needs PostreSQL.
Did you include the 'pg' gem?
You have 2 options
Switch to Postgres locally: This WILL BE time consuming to set up if you haven't already, but you'll want to do it eventually. Go for it now ONLY IF you have the time. Skip it for now if you are feeling pressed, we can help you later on.
Use SQLite locally (in development), and Postgres on Heroku (production):
Create a gem group called :production, and include:
gem "pg"
Did you move sqlite to development only?
Do you have minitest-rails available in all environments?
Did you run migrations after deploying?
heroku heroku run rake db:migrate
Hint:
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
Set up your custom domain name (register a new one, if you don't already have one).
Personal Portfolio domain names should be:
Memorable
Appropriate for work
Easy to say and spell over the phone. Say it out loud a few times and try to tell it to other people.
#Assignment: Get your own at a Domain Name Registrar: https://canvas.instructure.com/courses/853911/assignments/2753651
#Assignment: Sign up for Amazon Web Services (AWS): https://canvas.instructure.com/courses/853911/assignments/2753692
 Setup Domain Name Service (DNS) on Route 53. Read #stepbystep: http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/R53Example.html
Configure heroku app: Read #stepbystep: https://devcenter.heroku.com/articles/custom-domains
As a developer, I want my app to only go to production when all tests pass, so that I know my live code is working and I don't deploy bugs.
#Assignment: Set up a Continuous Integration server for your repo. Get your tests running in the cloud, and put a nice green badge on your README on GitHub. Can it auto-deploy when your tests pass?
Read: http://jolicode.com/blog/online-ci-providers-are-the-new-black
Option 1: Travis-CI
Read: http://about.travis-ci.org/docs/user/getting-started/
Read: http://stackoverflow.com/questions/10591599/rake-dbmigration-not-working-on-travis-ci-build (top answer)
README Hint:
Check out the Markdown source of https://github.com/codefellows/portfolio/blob/chapter-4/readme.md
#assignment: Set up .travis.yml to deploy to Heroku whenever your build passes
http://about.travis-ci.org/blog/2013-07-09-introducing-continuous-deployment-to-heroku/
gem install travis
travis login
Option 2: https://www.shippable.com/
Option 3: http://wercker.com/
