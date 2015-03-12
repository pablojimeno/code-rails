### GREEN: Comments

Follow **The Path** below ***only if you need it***.

Use the resource generator:

<pre style="color: #f7f7f7">
<code>
$ rails g resource comment author \
author_url \
author_email \
user_ip \
user_agent \
referrer \
content:text \
approved:boolean \
article:references \
--skip-test-framework
</code>
</pre>

Take a look at each generated file. See what it is doing?

Now follow the failing/erroring tests. You'll likely need to do these things:

- Code up a comment form, embedded in the article `show` view.

- Code up a `create` action in the `CommmentsController`.

- Modify your policies.

- Make sure to handle happy and unhappy path (the comment saves successfully or *un*successful).

- Just send the user back to the article, no need to create a comment show action.

Implement whatever you may need to get comment approval going. Let Pundit help you!
