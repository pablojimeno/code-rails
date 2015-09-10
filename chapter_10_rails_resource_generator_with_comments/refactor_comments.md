### REFACTOR: Comments

Actually, don't refactor just yet. The client just called in some additional requirements. "Just a quick thing," they said, "wouldn't it be faster for a commenter to fill in those name & url fields if they could use their Twitter accounts to sign up?"

"Like, one-click authorization," you suggest helpfully.

"That'd be so cool! Thanks," they say. It's nice to be appreciated.

## Now, lets make signing in a breeze with one click authorization.

Hmm, in order to do this, we need to understand how OAuth works.

Doing a little research into what this is all about, you come across a meetup talk, [Authentication with OAuth](https://www.youtube.com/watch?v=khnmMv4_RCE).

Let's start our refactoring with some tests.



