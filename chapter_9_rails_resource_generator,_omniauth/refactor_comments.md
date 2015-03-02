### REFACTOR: Comments
Actually, don't refactor just yet. The client just called in some additional requirements. "Just a quick thing," they said. Wouldn't it be faster for commenter to sign up if they could use their Twitter accounts?

Hm, we need to understand how OAuth works. Doing a little research into what's going on, you come across this meetup talk: [Authentication with OAuth](https://www.youtube.com/watch?v=khnmMv4_RCE)

BDD an OAuth login:
- Site Visitors can only comment if they log in with Twitter (and/or optionally Facebook or LinkedIn)

- What value should go in the new user's `role` column?

- Authors and Editors can still comment, too

Watch: [RailsCast #235 (Devise and Omniauth)](http://railscasts.com/episodes/235-devise-and-omniauth-revised?view=asciicast)

You don't have to follow along, but it's good practice if you have the time. It's a revised episode so you should be able to get it running. You may want to just dive in and follow the GREEN path here instead.

