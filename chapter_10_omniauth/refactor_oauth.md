### REFACTOR: OAuth

Is your Twitter sign-in link in the place you want it? Now's a good time to move it if you want it elsewhere.

Trace through your OAuth flow, and ensure you are following along with what's happening. Are you actually using all those new methods in your User model?

Where can you make the code easier to read?

Now that you have twitter, what if you want visitors to be able to sign in with Github? (or Facebook, Linkedin etc...)

We can combine the functionality for these.

Make a test for logging in with Github...

Now lets make code it...
