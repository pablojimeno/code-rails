### GREEN Polymorphic

Watch [RailsCast #154 *Polymorphic Association (Revised)*](http://railscasts.com/episodes/154-polymorphic-association-revised)

Refactor comments so that they work on articles ***and*** projects.

You will need a `change` migration for Comments
  - add in the `id` and `type` fields and remove the article `id`

  - Use the sample code from today's slides if needed

  - If you get stuck and need to render a `@commentable` type, use some light metaprogramming with `instance_variable_set`

  - reference this diff of ["Adding Polymorphic Comments" ](https://github.com/UW-Advanced-Rails-2014/portfolio/commit/e5ac9ac700ad1aa3ae5d0cfe4bf6626930dd32b8#diff-ad7009a67ee4df1721dd8e449dffec56R36)
