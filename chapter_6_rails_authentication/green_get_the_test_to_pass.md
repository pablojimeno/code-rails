# GREEN: Get the test to pass

GREEN: Now work to get the test passing. Time to play in the sandbox and tackle this one without the Path. Try hard!

Hints:
- <span style="color: white">
Your app layout should have a 'Sign Out' link if current_user.present? and otherwise should have a 'Sign Up' and a 'Sign In' link. How do you find the proper path helpers?
</span>

- <span style="color: white"> Since the spec needs to sign in first, you need an existing user. Use one of your fixtures.
</span>
- <span style="color: white"> Fixtures can have embedded ruby in <%= erb tags %> </span>

- <span style="color: white"> You can use that to set a password like this:</br>
"dude:
  email: dude@example.com
  encrypted_password: <%= User.new.send(:password_digest, 'password') %>
"
</span>

What http verb should you use to destroy a user session?
