
### Error:

    SQLite3::ConstraintException: column email is not unique

Where did that error come from? What does the stack trace tell you?

Read the instructions in the new `users.yml` fixutre file. Give your fixtures more meaningful names, rather than "one" and "two". These are your first users! Bit and Byte? King and Kong?

What attributes do your first users need to have set within the fixtures?


It's passing! Where'd that route come from? See (and examine) all new available routes with:

    $ rake routes
