# As a developer, I want a front-end framework so that I can easily modify the look and feel of my site

<br>
## RED

####CheckForZurb
Write a spec to check for zurb foundation loading on `root_path`.

<br>
**The Path**:

    $ rails generate minitest:feature


What can you look for your on your page to indicate that Zurb is in effect?

**Hint**:

<span style="color: white">
  One option would be to check for "columns" in the page.body. Better would be to see if a stylesheet with "zurb" in the name was getting loaded within the HTML.

Have other ideas? Please share if you come up with a better test!
</span>

<br>

## GREEN

### Add the Zurb Foundation gem

Follow instructions in the gem's README:
https://github.com/zurb/foundation-rails

You'll be adding the JavaScript and stylesheets so they will load through your asset pipeline. For more info on the asset pipeline, read the Rails Guide:
http://guides.rubyonrails.org/asset_pipeline.html

You may also want to check out a more automated approach, with a RailsApps application generator:
https://github.com/RailsApps/rails_layout

