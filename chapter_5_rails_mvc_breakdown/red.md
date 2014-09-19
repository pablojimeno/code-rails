## RED: Write spec for create

Remember what generator you can use to create the test for you? You can even have the generator place the new test file directly in your `test/features/projects/` directory.

    $ rails generate minitest:feature projects/CreatingAProject

What should your test look like? (Highlight bullet points to see the steps of the test).
- <span style="color: white">
    Start at the project index
  </span>
    - <span style="color: white; font-family: courier">
    visit projects_path
      </span>
- <span style="color: white">
    Click a link to see the form for creating a new project
  </span>
    - <span style="color: white; font-family: courier">
        click_on "New Project"
    </span>
- <span style="color: white">
    Fill in the form...
  </span>
- <span style="color: white">
    Submit it...
  </span>
- <span style="color: white">
    Then verify the correct page loaded, and you are seeing the newly created project.
  </span>
- <span style="color: white">
    If you need further hints highlight the whitespace below to see the full spec. Did you produce something similar?
  </span>

[COMPLETE] Spec:
<pre style="color: #f7f7f7">
    <code>
    require "test_helper"

feature "As the site owner, I want to add a portfolio item so that I can show off my work" do
  scenario "adding a new project" do
    visit projects_path
    click_on "New Project"
    fill_in "Name", with: "Code Fellows Portfolio"
    fill_in "Technologies used", with: "Rails, Ruby, Bootstrap, HTML5, CSS3"
    click_on "Create Project"
    page.text.must_include "Project has been created"
    assert page.has_css?("#notice"), "Expected a flash notice on this page, none found."
    page.status_code.must_equal 200
  end
end
    </code>
</pre>
