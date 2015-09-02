# Write spec for show & index views

**Sandbox** guidance - can you do this off **The Path**?

Give it a try, and use the *The Path* on the next pages only if you need them below one step at a time as needed.

## Create the spec file for index of portfolio items

1. Add fixture files with some sample data in `test/fixtures/projects.yml`.  Here's an example:

    ```YAML
  portfolio:
     name: How meta
     technologies_used: Ruby, Rails, Zurb, Javascript

  freelance:
     name: Barnyard Cereal
     technologies_used: Ruby, Rails, Farmville API, Automilker
    ```

2. Generate the file:

       $ rails g minitest:feature projects/showing_project_index --pretend

3. Write the feature and scenario.

  Example spec:
<pre style="color: #f7f7f7; font-size: 1.1em;">
    <code>
    require "test_helper"

    feature "As the site visitor, I want to see a developer's portfolio" do

      scenario "viewing all projects" do
        # Given a a couple of projects (loaded from fixtures)

        # When I visit /projects
        visit projects_path

        # Then I should see a list of projects
        page.text.must_include "Barnyard Cereal"
        page.text.must_include "Ruby, Rails"
      end
    end
    </code>
</pre>

4. Implement the feature.

Much of this spec may already be implemented from your work with Create! Make sure it looks good, and works as specified.

## Create the spec file for showing a single project

    $ rails g minitest:feature projects/showing_a_project --pretend

1. Write the feature and scenario.

2. Implement the spec; there isn't much to do, if anything.

3. Ask for help if you get stuck!

