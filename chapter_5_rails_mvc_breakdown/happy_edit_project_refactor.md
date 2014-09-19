## REFACTOR:
Check your coding style and clarity. Anything you need to clean up?

It looks like the `show`, `edit`, and `update` actions all set up the `@project` instance variable in the exact same way. Let's DRY that up.

  1. Create a new private method called `set_project`
  - The contents of that method should be the code that is repeated in the `show`/`edit`/`update` actions that sets up the instance variable
  - Replace the code in those actions with a simple call to this new method
  - Better yet, find a way to call the `set_project` method before each of those actions that need it, so you don't even have to repeat the method call.
  - After you've tried it on your own, take a look at how it is done in the scaffold-generated `PostsController`.

