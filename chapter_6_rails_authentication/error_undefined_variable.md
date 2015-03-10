### Error:

    Undefined local variable or method `new_user_registration_path'

**Let's begin by *RTFM*:** [The Devise README]( https://github.com/plataformatec/devise).

Carefully follow all the steps, but take note of these tips:

- The **Getting Started** section will have instructions to get set up.

- Read carefully the output of the `devise:install` generator. There are five suggested steps. Read and understand each as best you can, then do as instructed, IF NEEDED. "Generating views" is recommended.

- There are more instructions in the **Getting Started** section to follow. Read them carefully. Yes, the config file has things you need to change.

- When you generate your Devise model, call it "User." Delete the `test/model` directory this creates. Note that a fixture was created for you.

- As always, visually inspect the migration before you run it.

Re-run your test.

If needed, get schema changes reflected in test environment:

    $ rake db:test:prepare

Check out the changes in routes.rb:

    $ git diff config/routes.rb

What other changes did Devise make?

Read and understand them all:

    $ git diff
