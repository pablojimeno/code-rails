# Chapter 8: Rails Authorization

BDD authorization roles for Portfolio

We're going to add the ability to mark blog articles as "published" (or not). And, we will specify who can publish articles.

To manage this, we will create three roles on your portfolio site:

 - **Editors**: these are the site admins that can do everything, including marking articles as "published"

 - **Authors**: these can write articles, but not publish them.

 - **Visitors**: the default user type, a regular site visitor, they can only view published articles.

Ready to give it a go? Your assignment: Modify your portfolio to have the above behaviors.

Write a whole bunch of user stories for all these behaviors. Add these to your PM tool:

#### Authors
  - As an author I want to only see my own articles so that I can focus on my work

  - As an author I want to create articles so that I can share great content with the world

  - As an author I want to update articles so that I can fix typos

  - As an author I should not be able to publish articles so that I can give the editor publishing control, and I should see a 'not authorized' message if I try to hack it

  - As an author I should not be able to delete articles so that I can give the editor publishing control


#### Editors
  - As an editor I want to see all articles regardless of published status in the blog index so that I can choose which articles to publish

  - As an editor I want to create articles so that I can share great content with the world

  - As an editor I want to update articles so that I can fix typos

  - As an editor I want to publish articles so that I can make articles live on the site

  - As an editor I want to delete articles so that I can remove opium-fueled Jabberwocky


#### Visitors (unauthenticated users)
  - As a site visitor (user) I want to view (read) articles so that I can enjoy quality content

  - As a site visitor I should not be able to delete, update or create articles so that I can't modify a site I don't own

  - As a site visitor I want to only see published articles so that I don't see crap drafts
