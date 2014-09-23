# Chapter 6: Rails Authentication

Are your users authentic?

Nearly every web app needs some kind of authentication system, to ensure that users are who they say they are. Usually this is email/password-based. If the user who is signing in has access to the email and password of a user in the system, we can reasonably assume that user is authentically who they say they are.

  For a user to get in to the system in the first place, we need a way for them to register with our app, a sign-in page. Once they are registered, they can come and go via sign-in and sign-out routes that control create and destroy a "session", respectively. We don't need to store session info in the database, so it only needs the VC of MVC.

  Let's sort all this out by building out a very basic authentication system from scratch, then using the popular and production-ready gem Devise for our portfolio.
