### Failure:

Did you get something like?

    Expected /projects$/ to match "/projects/1".


Well, that's not returning us to the form at `/new`! It's showing a successfully created project!

We should still see the `/new` form if we entered invalid data.

Let's have our model validate the user data to ensure it meets our requirements. The Rails model "validations" will help us here!

