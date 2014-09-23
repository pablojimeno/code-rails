
## GREEN: Can you follow along with the error messages, and get the spec passing on your own?

### If you need a hint:

#### Here's a complete scenario:
<pre style="color: #f7f7f7"><code>
scenario "incorrectly editing an existing project" do
  # Given an existing project
  visit edit_project_path(projects(:portfolio))

  # When I submit invalid changes
  fill_in "Name", with: "Err"
  click_on "Update Project"

  # Then the changes should not be saved, and I should get to try again
  page.text.must_include "prohibited"
  page.text.must_include "Name is too short"
end
</code></pre>

#### Here's a complete update action:
<pre style="color: #f7f7f7"><code>
  def update
    @project = Project.find(params[:id])

    if @project.update_attributes(params[:project])
      redirect_to @project, notice: 'Project was successfully updated.'
    else
      render :edit
    end
  end</code>
</pre>

**Was that so bad? ;]**
