# Chapter 11: OmniAuth

Now that we have the capability to add comments to our blog, we need to authorize people to do so.  But signing in all the time is such a pain and we can bet that users will get tired of it.  So... while we're at it, why don't we make it super easy, and let Google, Github, Facebook or Twitter handle the sign in process for us.

Lets set it up.  Start with your tests!!!

### BDD an OAuth login

Requirements:

- Site Visitors can only comment if they log in with Twitter (and/or, optionally, Facebook or LinkedIn).

- What value should go in the new user's `role` column?

- Authors and Editors can still comment, too

Watch Ryan Bates' [RailsCast Episode #235: Devise and Omniauth](http://railscasts.com/episodes/235-devise-and-omniauth-revised?view=asciicast). You don't have to follow along, but it's good practice if you have the time.

It's a revised episode so you should be able to get it running without unexpected problems. After watching, you be familiar with the concepts you'll need to dive into the next section here instead.
