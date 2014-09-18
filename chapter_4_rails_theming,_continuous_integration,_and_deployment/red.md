# Red
####CheckForZurb
Write a spec to check for zurb foundation loading on root_path.<br>
Path:

    rails generate minitest:feature


What can you look for your on your page to indicate that Zurb is in effect?

Hint:<br>
<span style="color: white"> One option would be to check for 'columns' in the page.body.
Better would be to see if a stylesheet with "zurb" in the name was getting loaded.
Please share if you come up with a better test!</span>
