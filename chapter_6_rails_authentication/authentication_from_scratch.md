# Authentication From Scratch

Let's sort all this out by building out a very basic authentication system from scratch.  Then we will use a popular and production-ready gem, Devise, for our portfolio.

Create authentication in a fresh Rails app from scratch.

Revised version (Pro subscription needed): [Rails Cast #250 (Authentication from Scratch)](http://railscasts.com/episodes/250-authentication-from-scratch-revised?view=asciicast)

The RailsCast uses Rails v3.2.1, so you have two options:
1. Install and use that v3.2.1 of Rails, try to match all gem versions exactly (refer to GitHub repo)

- **Recommended**: Use the latest Rails 3 version, which has some minor differences
  - Use underscores to create the app with your desired version
        $ rails _3.2.17_ new auth
  - Rails 3.2.11+ will require and add the `attr_accessible` line for you when a model is generated, so pay attention to what's happening there.
  - If you need it, there is [an example repo](https://github.com/codefellows/auth) of creating auth from scratch, done with Rails 3.2.14 on the [Code Fellows GitHub account](https://github.com/codefellows). Do not directly duplicate/clone/copy/paste that repo!


