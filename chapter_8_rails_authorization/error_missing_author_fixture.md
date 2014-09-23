### ERROR:

    No fixture named 'author' found for fixture set 'users'

I bet you know what to do here. You should add a new fixture for `:author` and one for `:editor`

Try it yourself first. How might we determine what role each user record belongs to?

What, you want to see an example? OK!
```YAML
author:
  email: author@example.com
  encrypted_password: <%= User.new.send(:password_digest, 'password') %>
  role: author

editor:
  email: editor@example.com
  encrypted_password: <%= User.new.send(:password_digest, 'password') %>
  role: editor
```
