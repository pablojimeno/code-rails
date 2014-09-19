# Write spec for show & index views.
- Write spec for show & index views.
  - Sandbox guidance... Can you do this off the path? Give it a try, and use the path nested below one step at a time as needed.
    - Create the spec file for index of portfolio items
      - Add fixture files with some sample data in test/fixtures/projects.yml, eg:
        "portfolio:
          name: How meta
          technologies_used: Ruby, Rails, Zurb, Javascript

        freelance:
          name: Barnyard Cereal
          technologies_used: Ruby, Rails, Farmville API, Automilker
        "
      - rails g minitest:feature projects/showing_project_index --pretend
      - Write the feature and scenario
        - Set "Completed: Visible" to see the spec below, after you've attempted it.
          - [COMPLETE] The spec:
            "require "test_helper"

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
            "
      - Much of this spec may already be implemented from your work with Create! Make sure it looks good, and works as specified.
    - Create the spec file for showing a single project
      - rails g minitest:feature projects/showing_a_project --pretend
      - Write the feature and scenario
      - Implement the spec, there isn't much to do, if anything. Ask for help if you get stuck!
