### Translate to Code


Consider these thoughts, if you get stuck:

**Hints**:

<span style="color: white">
  The URL should be "/projects". Why is that?
</span>

<span style="color: white">
  We want to handle the error in the create action, but we want to re-render the "new" view.
</span>

<span style="color: white">
  We aren't redirecting, so the browser still displays the url that it POSTed to.
</span>


Here's the solution:
<pre style="color: #f7f7f7; font-size: 1.1em;">
  <code style="margin: 0;">

scenario "new project has invalid data" do

  <p style="color: gray; padding: 0; margin: 0;">
  &num; Given invalid project data is entered in a form
  visit new_project_path
  </p>
  fill_in "Name", with: "Q"

  <p style="color: gray; padding: 0; margin: 0;">
  &num; When the form is submitted with a short name and missing technologies_used field
  </p>

  click_on "Create Project"

  <p style="color: gray; padding: 0; margin: 0;">
  &num; Then the form should be displayed again, with an error message
  </p>

  current_path.must_match /projects$/
  page.text.must_include "Project could not be saved"
  page.text.must_include "Name is too short"
  page.text.must_include "Technologies used can't be blank"

end

  </code>
</pre>
