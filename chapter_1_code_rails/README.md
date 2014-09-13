# Chapter 1: Code Rails
Chapter 1: BDD & TATFT

- Welcome aboard! Please #read a brief intro now: https://gist.github.com/brookr/6863595
- Lecture & Slides
  - What is a Web App? Download: https://www.dropbox.com/s/apwd6dr737flkei/Day%201%20-%20Intro%20for%20Rails%20JS%20and%20UX.pdf
  - Key Concepts
    - Dynamic vs Static generation of HTML/CSS/JS
    - Layers of abstraction
    - Language vs Framework
    - Ruby Gem building blocks
    - Agile Development
      - #Watch: [Agile: An Introduction]( http://www.youtube.com/watch?v=OJflDE6OaSc )
      - #Watch: [Intro to Scrum](http://www.youtube.com/watch?v=XU0llRltyFM) You can stop watching at 7:15 where the ad for the tools start.
      - #Read: [Visions of a Post-Agile world](http://blog.sprint.ly/post/41801740808/visions-of-a-post-agile-world)
- As a developer, I want to use a Project Management App so that I can track my tasks and progress
  - Learn how to write a good user story: #Read http://www.mountaingoatsoftware.com/blog/advantages-of-the-as-a-user-i-want-user-story-template
  - Project Management Apps
    - Huboard.com
      - Super-easy github integration (just uses GH issues)
      - Nice kanban board layout
      - Free
    - Sprint.ly
      - Enforces the User Story method: #Read http://www.mountaingoatsoftware.com/topics/user-stories
      - GitHub integration
      - Well designed, and is fun to use
      - Has a Free plan for up to 3 members
    - Pivotal Tracker
      - Popular, Widely known and respected
      - Compatible with the User Story method: http://www.mountaingoatsoftware.com/topics/user-stories
      - Free for open source
      - GitHub Integration
      - Email integration
    - Asana
      - No out-of the box github integration
      - General purpose tool, can be used for agile
    - Trello
      - No out-of the box github integration
      - More free-form, make your own way
- As a developer, I want to understand automated testing so that I can use BDD.
  - How do we know it works?
    - You can test manually, with teams of real people, or you can automate it. Or both!
  - Types of Testing
    - Unit Tests
      "Unit testing tests "the smallest testable part of an application". This could be an object-oriented class, or even an individual function (or method). Unit tests are fast because they test only one thing at a time. Each test case should be independent of the others. They help find problems early, make it easy to change both the unit under test, and other parts of your program that depend on your unit. They can help simplify system-wide integration testing. Unit tests provide "documentation as code". Not as good as real documentation, but it has its advantages because unit tests that are out of date will fail. Unit tests drive design by specifying "the ends" and not "the means". Disadvantages of unit testing are that because it is so specific, it can't catch more complex errors that rely on multiple units. For example, complex states of multiple objects, or problems with multiple threads. In Rails, we typically use unit testing for Models, and you can find the unit tests in the spec/models directory."
      - #Read: http://en.wikipedia.org/wiki/Unit_testing
    - Functional Tests
      - #Read: http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html
    - Integration Tests
      - "integration tests show that the major parts of a system work well together" - The Pragmatic Programmer, a recommended book: http://pragprog.com/the-pragmatic-programmer
    - Acceptance Tests
      - Complete User stories with as close to real life data as possible
    - Regression Tests
      - Tests that ensure bugs are not produced after changes to apparently-unrelated code are made. Also, tests that are put in place to ensure that bugs do not re-appear.
  - Types of development
    - Test Driven Development (TDD)
      "Test-driven development (TDD) is a software development process that relies on the repetition of a very short development cycle: first the developer writes an (initially failing) automated test case that defines a desired improvement or new function, then produces the minimum amount of code to pass that test, and finally refactors the new code to acceptable standards. Kent Beck, who is credited with having developed or 'rediscovered' the technique, stated in 2003 that TDD encourages simple designs and inspires confidence (from http://en.wikipedia.org/wiki/Test-driven_development )."
    - BDD
      "In software engineering, behavior-driven development (abbreviated BDD) is a software development process based on test-driven development (TDD). Behavior-driven development combines the general techniques and principles of TDD with ideas from domain-driven design and object-oriented analysis and design to provide software developers and business analysts with shared tools and a shared process to collaborate on software development, with the aim of delivering software that matters (as opposed to software that doesn't matter). (from http://en.wikipedia.org/wiki/Behavior_driven_development )."
      - #Read this thoughtful opinion piece from a Java developer: What BDD Has Taught Me: http://hadihariri.com/2012/04/11/what-bdd-has-taught-me/
      - #Watch this thoughtful lightning talk from Bryan Liles: http://www.youtube.com/watch?v=LfmAzLAKKoc&t=22s
      - In this outline / workbook, when we say "BDD a ________" We mean:
        - Red: Write a spec and watch it fail. For the first few days, we'll provide the specs to get you going
        - Green: Research / Learn the part of Rails you need and write the code to make the spec pass
        - Refactor: Analyze the code quality and refactor it if time available.
- As a developer, I want to use and understand BDD so that my projects turn out great
  - As a dev, I want a simple program that has a welcome message, so that I learn how to write and test a simple ruby project
    - Use BDD with MiniSpec to create a ruby class that has an instance variable containing a welcome message
      - #Read and do: How to Set Up Your First Minispec Project, From Scratch: https://gist.github.com/ivanoats/6833823
      - Example specification:
        "require "minitest/autorun"
        require "minitest/spec"
        require "welcome"

        describe Welcome do
          it "has a message" do
            hello = Welcome.new
            hello.message.must_match "Welcome"
          end
        end
        "
    - MiniSpec Quick Reference: http://mattsears.com/articles/2011/12/10/minitest-quick-reference
  - As a dev, I want a program to test a web search, so that I can learn more about interacting with web pages
    - Add a Gemfile to your project to manage the gems on which your projects depends. Include the rake gem to get started.
      "source "https://rubygems.org"

      gem "rake""
    - #Read the Capybara Readme. Don't worry if it doesn't all make sense yet: https://github.com/jnicklas/capybara
    - Add Capybara as a gem dependency for your project. Modify your Gemfile to include:
      "gem "capybara""
    - #Read the Poltergeist docs: https://github.com/jonleighton/poltergeist, add to Gemfile.
    - Example specification for a google search, please use your own search term:
      "require "spec_helper"

      describe "My search page" do
        it "has results" do
          visit "http://google.com"
          fill_in "q", with: "Code Fellows"
          click_on "Google Search"
          page.text.must_include "codefellows.org"
          page.text.must_include "twitter.com/CodeFellowsOrg"
        end
      end
      "
    - Example spec_helper.rb:
      "require "minitest/autorun"
      require "minitest/spec"

      class FeatureSpec < MiniTest::Spec
        require "capybara/poltergeist"
        include Capybara::DSL
        Capybara.default_driver = :poltergeist
        register_spec_type(/page$/, self)
      end"
    - Important reminder: This spec_helper.rb file sets up Capybara to work for any feature specs you create that have a description ending in "...page".
  - As a dev, I want a web page that outputs a welcome message via HTML, so that I can learn how to test web pages
    - Use BDD to develop a simple HTML page
      - You can create an html page with your text editor.
      - If you create a file called `index.html`, you can see it in your browser by putting the full location in your browser's address bar. On a Mac, from the same directory as the file, you can type:
        "open index.html"
      - Alternatively, get any directory's files online locally with a tiny ruby script:
        "#!/usr/bin/env ruby

        #
        # example:
        #  serve public 4001
        #
        # Spin up a quick web server for files in the specified directory (first arg)
        # on the port number given (second arg).
        #

        require "webrick"

        s = WEBrick::HTTPServer.new(
          :DocumentRoot => (ARGV[0] || Dir.pwd),
          :Port => (ARGV[1] || 4000)
        )

        trap('INT') { s.shutdown }

        s.start"
        - OR you can create a serve function in your ~/.bashrc or ~/.bash_profile (in your home directory)
          "function serve {
            port="${1:-4000}"
            ruby -r webrick -e "s = WEBrick::HTTPServer.new(:Port => $port, :DocumentRoot => Dir.pwd); trap('INT') { s.shutdown }; s.start"
          }

          # important: the commands inside the string (inside the double quotes) must all be on *one* line
          # https://gist.github.com/ivanoats/6613386/deb67edc9bb62567cede2cd4487ed0fde48c4be8  "
        - OR you can create a serve.sh file, and make it executable: https://gist.github.com/ivanoats/6613386
    - Example specification:
      "require "spec_helper"

      describe "A local web page" do
        it "has a welcome headline" do
          visit "/something/goes/here/..."
          page.text.must_include "Welcome aboard"
        end
      end"
  - As a dev, I want a basic Rails app up and running on port 3000 of my computer
    - BDD `rails new sample-app`. Write your test first! What would a test that looks on port 3000 look like?
    - Be careful where you run this command. Be sure to make this new app outside of your current project directory tree. You don't need to submit this new rails app with your main project code.
    - Once you've created the Rails app, how can you start it up?
      - Need a hint? Try changing in to the directory for the new Rails project you just created, and type just `rails`.
    - Example specification:
      "require "spec_helper"

      describe "My Rails App welcome page" do
        it "shows the welcome message" do
          visit "http://localhost:3000"
          page.text.must_include "Welcome aboard"
        end
      end"
- As a Rails developer, I want to understand the structure of a Rails app so that I can understand Rails conventions
  - WTF just happened when I typed "rails new …" ???
    - You have a fresh new Rails app, which by default says "Welcome Aboard"
    - #Read the short Section 3.2 only from the "Getting Started" Rails Guide: http://guides.rubyonrails.org/getting_started.html#creating-the-blog-application
  - What is Rails? It is a:
    - Ruby framework
      "Rails is actually a collection of 7 different ruby gems that are designed to function independently or together, to form a framework for web apps."
    - Utilizes Convention over Configuration
      - #Read: http://en.wikipedia.org/wiki/Convention_over_configuration
      - Optional bonus #Read: http://softwareengineering.vazexqi.com/files/pattern.html
    - Open source, build around community best practices
    - Remember our slides:
      - Web app vs Web site
      - Can persist user data in a database
