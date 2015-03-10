# Intro to CRUD

Rails apps are built around the concept of "resources". This is the representation in code of a real-world noun, like a User, or a Project. There is a standard set of actions you'll likely want to preform on all resources in your app: Create, Read, Update, and Delete… collectively called CRUD.

Being able to "CRUD a resource" ends up being a very common pattern, so Rails is heavily optimized to make this easy. In fact, you can get full CRUD behavior from rails with just one or two commands in your terminal, thanks to the power of the Rails scaffold generator. We'll play with that a little today, to see what it can do for us, and to start to get a sense of how Rails treats resources.

For your portfolio site, you really want to be able to show off your expertise as a developer. One of the best ways to do this is to have a place where you can write articles that share what you are learning as you pick up new dev skills. There are gobs of eager learners who can benefit from your guidance, so don't be shy about writing up what you've learned and getting something out there!

You'll want your Rails app to have a resource called Article that you can CRUD. The Article resource will have attributes of a "title" and a "body," and each new one you create will be stored in a database, until it is deleted. You can then build individual web pages within your app for making a new article, editing an existing one, and viewing a list of everything that the database is holding.

So, with a few good user stories, we can let the **B**ehavior of the app **D**rive our **D**evelopment process.

Before you jump in, there is a little background reading and watching for you to complete.

Ready to go?
