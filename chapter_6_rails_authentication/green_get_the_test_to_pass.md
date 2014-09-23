# GREEN: Get the test to pass

 Now work to get the test passing. Time to play in the sandbox and tackle this one without the *Path*. Try hard!

Hints (highlight them when you get stuck):
- <span style="color: white">
Your app layout should have a 'Sign Out' link if current_user.present? and otherwise should have a 'Sign Up' and a 'Sign In' link. How do you find the proper path helpers?
</span>

- <span style="color: white"> Since the spec needs to sign in first, you need an existing user. Use one of your fixtures.
</span>

- <span style="color: white"> Fixtures can have embedded ruby in <%= erb tags %> </span>

- <span style="color: white"> You can use that to set a password like this:

<pre style="color: #f7f7f7">
dude:
  email: dude@example.com
  encrypted_password: <%= User.new.send(:password_digest, 'password') %>
</pre>

What HTTP verb should you use to `destroy` a user `session`?
