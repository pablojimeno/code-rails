# Add Fixtures

Create a directory for your fixtures:

    /test/fixtures

Add a file:

    articles.yml

Add sample data!

**Hints**:

<span style="color: white">
  follow the pattern of using a name, followed by key, value pairs
</span>

<pre style="background-color: white">
<code style="color: white; font-size: 1.1em;">
cr:
  title: Code Rails
  body: This is how I learned web development!

http:
  title: Intro to HTTP
  body: It's all about the request-response cycle!
</code>
</pre>

Fixtures are instantiated by default, so you can remove `.create` statements.

Replace your existing objects, where appropriate. You can use the fixture to get attributes to use in your tests.

Does the order of your fixtures matter for the deletion spec?

What's the advantage of using fixtures instead of `.create` statements? Can you think of 3 benefits?
