### RED: Comments

Write some specs for these stories:

- As a site visitor I want to write a comment on a blog article page so that I can troll the author.

- As an editor I want to approve comments so that my blog does not have spam comments.

Where is the best place to put these additional specs? How many scenarios do you need to cover the above user stories sufficiently?

Comments should not display until they are approved by an editor.

How do you want approval to work? A checkbox on an edit form? A button that PATCHes to `CommentsController#update`?

Comments should store this info:

- commenter_name
- commenter_url
- commenter_email
- content:text
- article:belongs_to
- approved:boolean

You now have all the info you need to write your specs. Go to it! 

Proceed to the next section when you have a bunch of errors/failuers.
