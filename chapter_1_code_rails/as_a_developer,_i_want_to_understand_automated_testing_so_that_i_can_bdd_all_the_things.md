# As a developer, I want to understand automated testing so that I can BDD all the things


## How do we know our app works?

  You can test manually, with teams of real people and a lot of clicking, or you can automate it.

### Types of Testing
####Unit Tests

Unit testing tests "the smallest testable part of an application". This could be an object-oriented class, or even an individual function (or method). Unit tests are fast because they test only one thing at a time. Each test case should be independent of the others. They help find problems early, make it easy to change both the unit under test, and other parts of your program that depend on your unit. They can help simplify system-wide integration testing. Unit tests provide "documentation as code". Not as good as real documentation, but it has its advantages because unit tests that are out of date will fail. Unit tests drive design by specifying "the ends" and not "the means". Disadvantages of unit testing are that because it is so specific, it can't catch more complex errors that rely on multiple units. For example, complex states of multiple objects, or problems with multiple threads. In Rails, we typically use unit testing for Models, and you can find the unit tests in the spec/models directory.

Please Read [this Wikipedia page](http://en.wikipedia.org/wiki/Unit_testing) about unit testing

#### Functional Tests

Please read [this article](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.htm) about the difference between functional and unit testing (THIS LINK IS BROKEN)

#### Integration Tests

> "integration tests show that the major parts of a system work well together"

-[The Pragmatic Programmer](http://pragprog.com/the-pragmatic-programmer), a recommended book

#### Acceptance Tests

Complete User stories with as close to real life data as possible

#### Regression Tests

Tests that ensure bugs are not produced after changes to apparently-unrelated code are made. Also, tests that are put in place to ensure that bugs do not re-appear.

### Types of development
#### Test-Driven Development (TDD)

>"Test-driven development (TDD) is a software development process that relies on the repetition of a very short development cycle: first the developer writes an (initially failing) automated test case that defines a desired improvement or new function, then produces the minimum amount of code to pass that test, and finally refactors the new code to acceptable standards. Kent Beck, who is credited with having developed or 'rediscovered' the technique, stated in 2003 that TDD encourages simple designs and inspires confidence"

[source](http://en.wikipedia.org/wiki/Test-driven_development )

#### Behavior-Driven Development (BDD)
>"In software engineering, behavior-driven development (abbreviated BDD) is a software development process based on test-driven development (TDD). Behavior-driven development combines the general techniques and principles of TDD with ideas from domain-driven design and object-oriented analysis and design to provide software developers and business analysts with shared tools and a shared process to collaborate on software development, with the aim of delivering software that matters (as opposed to software that doesn't matter).

[source](http://en.wikipedia.org/wiki/Behavior_driven_development)

Please read this thoughtful opinion piece from a Java developer: [What BDD Has Taught Me](http://hadihariri.com/2012/04/11/what-bdd-has-taught-me/).

Please watch [this thoughtful lightning talk](http://www.youtube.com/watch?v=LfmAzLAKKoc&t=22s) video from Bryan Liles. TATFT.

## In this workbook, when we say "BDD a ________" We mean:

- **Red**: Write a spec and watch it fail. For the first few days, we'll provide the specs to get you going
- **Green**: Research / Learn the part of Rails you need and write the code to make the spec pass
- **Refactor**: Analyze the code quality and refactor it if time available.

## Now you know...
Phew, that was lots of information about testing. Now it's time to really learn it, by putting it in to practice.
