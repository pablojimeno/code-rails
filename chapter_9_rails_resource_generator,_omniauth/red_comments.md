### RED: Comments

Write some specs for these stories...
  - As a site visitor I want to write a comment from a blog article page so that I can troll the author.

  - As an author or editor I want to approve comments so that my blog does not have spam comments.

Where is the best place to put these additional specs? How many do you need to cover the above user stories sufficiently?

Comments should not display until they are approved by an author or editor. How do you want approval to work? A checkbox on an edit form? A button that PATCHes to `CommentsController#update`?

Comments should store this info:
- author
- author_url
- author_email
- user_ip
- user_agent
- referrer
- content:text
- approved:boolean

You now have all the info you need to write your specs. Go to it! Proceed when you have a bunch of errors/failuers.
