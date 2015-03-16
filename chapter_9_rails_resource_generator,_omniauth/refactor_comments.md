### REFACTOR: Comments

Actually, don't refactor just yet. The client just called in some additional requirements. "Just a quick thing," they said, "wouldn't it be faster for a commenter to fill in those name & url fields if they could use their Twitter accounts to sign up?"

"Like, one-click authorization," you suggest helpfully.

"That'd be so cool! Thanks," they say. It's nice to be appreciated.

Hmm, we need to understand how OAuth works.

Doing a little research into what this is all about, you come across a meetup talk, [Authentication with OAuth](https://www.youtube.com/watch?v=khnmMv4_RCE).

Let's start our refactoring with some tests.

### BDD an OAuth login

Requirements:

- Site Visitors can only comment if they log in with Twitter (and/or, optionally, Facebook or LinkedIn).

- What value should go in the new user's `role` column?

- Authors and Editors can still comment, too

Watch Ryan Bates' [RailsCast Episode #235: Devise and Omniauth](http://railscasts.com/episodes/235-devise-and-omniauth-revised?view=asciicast). You don't have to follow along, but it's good practice if you have the time.

It's a revised episode so you should be able to get it running without unexpected problems. After watching, you be familiar with the concepts you'll need to dive into the next section here instead.

