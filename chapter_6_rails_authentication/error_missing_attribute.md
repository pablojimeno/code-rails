### ERROR:

    ActiveModel::MissingAttributeError' can't write unknown attribute `author_id'

Right, we need an `author_id` column in our database to hold the association info. Which table gets this new column?


Let's add it with a migration.

    $ rails g migration AddAuthorIdToArticles author_id:integer

Open and read the new migration file. Does it look reasonable? It should add a new column, `author_id`, to the `articles` table, that will be a reference to a `User` record.

Run the migration:

    $ rake db:migrate

Now, go look at the change in `schema.rb`.

Since we changed our schema, we also need to update our test environment:

    $ rake db:test:prepare

Run the spec again.

Green, beautiful green!
