## RED: Creating Articles
What do we need to do to write tests for those user stories?

We need a way to access the site as different roles:
  - Signed in as editor (think: admin)
  - Signed in as author
  - not signed in at all (just a site visitor)

That will provide the "scenarios" for our resource CRUD tests. Today, let's focus just on articles.

We want to specify that we can sign in as an author to create a article, that is not yet published. Let's make two change to our existing `creating_an_article_test.rb` file:

```ruby
  sign_in(:author)
  ...
  page.text.must_include "Status: Unpublished"
```

We can then add a few additional tests. A simple test to ensure visitors do not have access to the new article form:

```ruby
scenario "unauthenticated site visitors cannot visit new_article_path" do
  visit new_article_path
  page.must_have_content "You need to sign in or sign up before continuing"
end
```

In fact, they don't even need to see the new article button on the index
```ruby
scenario "unauthenticated site vistiors cannot see new article button" do
    # When I visit the blog index page
    visit articles_path
    # Then I should not see the "New Article" button
    page.wont_have_link "New Article"
end
```

Let's consider an article `published` if a simple boolean database value is flipped to true. Editors should see this value in the Article form, but authors should not. That gives us 2 more simple tests:

```ruby
  scenario "authors can't publish" do
    # Given an author's account
    sign_in(:author)

    # When I visit the new page
    visit new_article_path

    # There is no checkbox for published
    page.wont_have_field('published')
  end
```
and:

```ruby
  scenario "editors can publish" do
    # Given an editor's account
    sign_in(:editor)

    # When I visit the new page
    visit new_article_path

    # There is a checkbox for published
    page.must_have_field('Published')

    # When I submit the form
    fill_in "Title", with: articles(:cr).title
    fill_in "Body", with: articles(:cr).body
    check "Published"
    click_on "Create Article"

    # Then the published article should be shown
    page.text.must_include "Status: Published"
  end
```

Let's see what it takes to get these to green!
