# Authentication From Scratch

 Let's sort all this out by building out a very basic authentication system from scratch, then using the popular and production-ready gem Devise for our portfolio.


Create authentication in a fresh Rails app from scratch. Do this first.
  - Revised version (pro) : http://railscasts.com/episodes/250-authentication-from-scratch-revised?view=asciicast
  - That uses Rails v3.2.1, so you have options
    - Install and use that version of Rails, try to match all versions exactly (refer to github repo)
    - Recommended: Use the latest Rails 3 version, which has some minor differences
      - Use underscores to create the app with your desired version
        "rails _3.2.16_ new auth"
      - Rails 3.2.11+ will require and add the attr_accessible line for you when a model is generated, so pay attention to what's happening there.
      - If you need it, there is an example repo of this, done with Rails 3.2.14 on the Code Fellows GitHub account. Do not directly duplicate/clone/copy/paste that repo.
