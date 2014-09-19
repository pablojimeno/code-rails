### Translate to Code

[COMPLETE] Here's one option (highlight text to see solution):
<pre style="color: #f7f7f7">
  <code>
scenario "new project has invalid data" do
  ####### Given invalid project data is entered in a form
  visit new_project_path
  fill_in "Name", with: "Q"

  ####### When the form is submitted with a short name and missing technologies_used field
  click_on "Create Project"

  ####### Then the form should be displayed again, with an error message
  current_path.must_match /projects$/
  page.text.must_include "Project could not be saved"
  page.text.must_include "Name is too short"
  page.text.must_include "Technologies used can't be blank"
end
  </code>
</pre>
- That the url should be "/projects"... Why is that?
- We want to handle the error in the create action...
- But we want to re-render the new view
- We aren't redirecting, so the browser still displays the url that it POSTed to.
