# Generate an Article scaffold

Run and *read*:

    $ rails generate scaffold

Try it with the `--pretend` option to see what it will do.

Try it with the `--no-test-framework` option to see the difference. Much less *stuff* is created in your `/test` folder!

When you have the command to your liking, remove `--pretend` and run it for real.

You should have something like this hidden command:

<span style="color: white;">
    $ rails generate scaffold article title body:text --no-test-framework
</span>


Now, run your tests again!  They're *passing*, right?! You're in the GREEN!

No? Fix your specs so they pass with the scaffold's behavior!
