### Error:
```
NameError: uninitialized constant ProjectsController::Project
```

`Project` is the uninitialized constant. Remember this error from Chapter 1? (It's also the error we saw before we added a `ProjectController`).

An unititialized constant error usually means the class is not defined yet. So, we need a model class; let's generate one.

Read about the model generator:

    $ rails generate model

Create a `Project` model:

    `$ rails generate model Project name technologies_used --no-test-framework`


What did this generator do for you? Read the output of it carefully.

It created 2 files. You could have typed out the content of the files manually instead.

Your `app/models/project.rb` doesn’t contain much.

The migration file will set up your database to store project data.

It will create a new table with columns for the attributes you specified.

Check out the migration file the generator created, and make sure the table and column names make sense.

Run the test again...

Did you get an error like this one?

```
Migrations are pending; run 'bin/rake db:migrate RAILS_ENV=test' to resolve this issue. (ActiveRecord::PendingMigrationError)
```

If so, you do indeed need to run those migrations. It's a simple rake command:

    $ rake db:migrate

But that only affects your development environment. Use this command to get your test env up to date:

    $ rake db:test:prepare

If you're curious, you can see all db related rake tasks by searching rake tasks that contain "db":

    $ rake -T db


Run the test again...
