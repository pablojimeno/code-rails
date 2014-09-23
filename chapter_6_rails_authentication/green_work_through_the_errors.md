# GREEN: Work through the errors


- Error: Unable to find link or button "Sign Up"
    - Add a link to your application layout. Use the path helper: new_user_registration_path
- Error: Undefined local variable or method `new_user_registration_path'
    - Let's begin by RTFM: The Devise README: https://github.com/plataformatec/devise
    - Carefully follow all the steps, but take note:
        - The "Getting Started" section will have what you need to do to get set up.
        - Read carefully the output of the 'devise:install' generator. There are 5 suggested steps. Read and understand each as best you can, then do as instructed, IF NEEDED. Generating views is recommended.
        - There are more instructions in the "Getting Started" section to follow... Read carefully. Yes, the config file has things you need to change.
        - When you generate your devise model, call it User. Delete the test/model directory this creates. Note a fixture was created for you.
        - As always, visually inspect the migration before you run it.
        - Re-run your test. If needed:
        ```
        "rake db:test:prepare # Get schema changes reflected in test environment"
        ```
        - Check out the changes in routes.rb:
        ```
        "git diff config/routes.rb"
        ```
        - What other changes did devise make? Read and understand them all.
        ```
        "git diff"
        ```
- Error: SQLite3::ConstraintException: column email is not unique
    - Where did that error come from? What does the stack trace tell you?
    - Read the instructions in the new users.yml fixutre file.
    - Give your fixtures more meaningful names, rather than "one" and "two". These are your first users! Bit and Byte? King and Kong?
    - What attribute do they need set?
    - It's passing! Where'd that route come from?
    - See all new available routes with:
    ```
    "rake routes"
    ```
