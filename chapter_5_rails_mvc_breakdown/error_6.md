### Error:
```
NameError: uninitialized constant ProjectsController::Project
```

- Project is the uninitialized constant. Remember this error from chapter 1?
  - an unititialized constant error usually means the class is not defined yet
  - We need a model class, so let's generate one
    - Read about the model generator:

      `$ rails generate model`
    - Create a Project model

      `$ rails generate model Project name technologies_used --no-test-framework`

    - What did this generator do for you? Read the output of it carefully.
      - It created 2 files. You could have done this manually just as well.
      - `app/models/project.rb` doesn’t contain much.
      - The migration file will set up your database to store project data. It will create a new table with columns for the attributes you specified.
    - check out the migration file the generator created, and make sure the table & column names make sense

- Run that test again...
    - Did you get an error like this one?

    ```
    Migrations are pending; run 'bin/rake db:migrate RAILS_ENV=test' to resolve this issue. (ActiveRecord::PendingMigrationError)
    ```
    - If so, you do indeed need to run those migrations. It's a simple rake command:

    `$ rake db:migrate`

    - But that only affects your development environment. Use this command to get your test env up to date:

    `rake db:test:prepare`

    - Now, rerun the test, and keep on jamming!
