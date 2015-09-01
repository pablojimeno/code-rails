# Simple Web Search

### As a dev, I want a spec to test a web search, so that I can learn more about automating interaction with web pages

To complete this user story, you will create a spec file that uses a headless browser to interact with a web page.

To start: Add a Gemfile to the project you started in the last step to manage the gems on which it depends. Include the rake gem, first off:

```ruby
# ~myapp/Gemfile

source "https://rubygems.org"

gem "rake"
```

Read the [Capybara Readme](https://github.com/jnicklas/capybara). Don't worry if it doesn't **all** make sense yet.

Add Capybara as a gem dependency for your project. Modify your Gemfile to include:
```ruby
# ~myapp/Gemfile

gem "capybara"
```
Read the [Poltergeist docs](https://github.com/jonleighton/poltergeist) and then add to Gemfile:
```ruby
# ~myapp/Gemfile

gem "poltergeist"
```

Then be sure to run `bundle install` from your project directory to install all gems.

## Capybara drives the browser

Now write a spec file that uses the Capybara commands to tell the browser to run a web search. Let the READMEs be your guide!

Example spec is in the subsection, but try to write it yourself first.

When you run this spec, you should now see it as a passing test if you have everything connected up properly.
