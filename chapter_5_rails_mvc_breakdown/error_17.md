### Error:

Are you using Fixtures yet? Perhaps you see an error like:

    NoMethodError: undefined method `projects' for #<#<Class:0x007ffbccbb4c28>:0x007ffbcc960558>

Here's what we need to do:

1. Create a fixture file called `projects.yml` in `test/fixtures/`

- Add some data to it. Remember, YAML is white space sensitive (and how!):
    ```YAML
    portfolio:
      name: How meta
      technologies_used: Ruby, Rails, Zurb

    freelance:
      name: Barnyard Cereal
      technologies_used: Ruby, Rails, Farmville API, Automilker
    ```
- Ensure you are using the fixtures by their correct names when accessing them in your test.
