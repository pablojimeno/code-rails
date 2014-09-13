# Chapter 2: Rails Best Practices
Chapter 2: Rails Best Practices

- Intro:
  "Rails is a "best practices" framework. This means there is a "Rails Way" of accomplishing most common web development tasks.

  This ends up being very powerful. Once you understand the Rails Way, you can sit down to any rails app that follows best practices and get to work. You don't need to reinvent the wheel, or submit to NIH (Not Invented Here) syndrome. Don't be clever, just go with the community-established style.

  This starts with an absolute requirement that everything you do happens under version control. Git has proven to be one of the most powerful and flexible tools for versioning your work, and the Rails community has standardized around it almost entirely. Take your git skills further with the linked resources.

  Then read a chapter of the book Clean Code (used with permission). There are a number of much more specific style guides linked as well. Take note of what is new to you, and what you learn.

  Then write some code! Use the best practice of BDD to create a new Rails app, and give it a static html welcome page. Commit that to a new repo, and submit the repo url for your assignment."
- Add these user stories to your project management app, and then get to work on them:
  - As a developer, I want to use version control so that I can save history and collaborate with others
    - Git & DVCS
      "Everyone comes in to this course with different levels of experience with git. Choose from the assignments below to take your git skills to the next level:"
      - Try Git: http://www.codeschool.com/courses/try-git
      - Practice git with visual guide: http://pcottle.github.io/learnGitBranching/ — Try at least 3 levels!
      - Take it further: http://www.codeschool.com/courses/git-real
      - Advanced git: https://www.codeschool.com/courses/git-real-2
  - As a developer, I want a PM Tool to track my repo so that I can complete stories from my commit message, save time, and inform management and the customer.
  - As a Rails developer, I want my code to follow industry-standard best practices so that my projects are readable, scalable, and secure
    - Rails conventions:
      - README
        - #Read this article, written by a Code Fellows alumna: http://www.stephaniehekker.com/why-you-should-write-a-readme-for-your-application/
        - Decide on what you want to use as a standard README format for all your projects
      - Code for clarity
        - #Read Chpater 1 of the book Clean Code, by Uncle Bob Martin: https://www.dropbox.com/s/y9jxxvlgnbocvn7/Chapter%201%20-%20Clean%20Code%20-%20A%20Handbook%20of%20Agile%20Software%20Craftsmanship.pdf
        - #Read: http://agile.dzone.com/news/clarity-code-clarity-thought
        - Review: http://www.planetgeek.ch/wp-content/uploads/2013/06/Clean-Code-V2.2.pdf
        - Extra Credit: https://medium.com/on-coding/a70ca8382884
      - Ruby style guide
        - Whitespace
          - 2 spaces (not tabs)
          - No whitespace at the end of the line
          - A single newline at the end of every file
        - Comments
          - #Read: https://github.com/bbatsov/ruby-style-guide#comments (just read up to Classes and Methods)
        - Online resources:
          - #Read: https://github.com/bbatsov/ruby-style-guide
          - #Read and compare: https://github.com/styleguide
        - Gem tool:
          - gem install rubocop
          - DO: run rubocop from within your project directory for your work from Chapter 1.
          - Extra Credit: figure out how to ignore a warning (like for double-quoted strings, which Brook says is fine)
      - Rails Gemfile: #Read http://mcdowall.info/posts/gemfile-best-practices-and-discourse/
      - Your IDE: A text editor #demo
        - Remap shift-space to underscore: http://gfxmonk.net/2009/01/29/remap-shiftspace-to-underscore.html
        - How to set up Sublime Text for our conventions. Choose Sublime Text / Preferences / Settings - User and enter these settings:
          "{
            "ignored_packages":
            [
              "Vintage"
            ],
            "save_on_focus_lost": true,
            "tab_size": 2,
            "translate_tabs_to_spaces": true,
            "trim_trailing_white_space_on_save": true,
            "ensure_newline_at_eof_on_save": true
          }"
        - Install the package manager for your version of Sublime.
        - Find & install some great recommended packages.
        - Get to know your editor:
          - #Watch a few of these hints that look interesting to you: https://tutsplus.com/course/improve-workflow-in-sublime-text-2/
          - Recommended: Multi-cursor, Instant file switching.
      - You should know this site exists: http://rails-bestpractices.com (A lot of what's there may not yet make sense. That's ok.)
  - As an employer, I want your site to have a welcome page so that I can learn about what an awesome Rails developer you are
    - Apply best practices: BDD a static front page for your Rails portfolio app.
    - RED
      - Write a feature spec for your user story above
        - You'll need a new Rails 4 app. Let's call this Portfolio.
          - Hint: We are not using the default Test::Unit framework, so you will want to use the handy `--skip-test-unit` flag:
            - rails new portfolio --skip-test-unit
          - Once you've generated the app, clean up the Gemfile according to best practices above.
        - We want you to use minispec and capybara to BDD this. You'll have to set this up within your Rails project. Here are some documentation resources:
          - #Read https://github.com/blowmage/minitest-rails
          - #Read https://github.com/blowmage/minitest-rails-capybara
          - Don't blindly copy/paste every command from those docs. That will mess you up.
            - Rather: understand what the commands do.
            - Decide which you need, which you don't, and which you may need to modify.
            - RETYPE! Copy/paste is the enemy of learning.
          - Instead of configuring this in a file called `minitest_helper.rb`, use the standard test helper file: `test_helper.rb` in the test/ directory
          - Really Stuck? Ask a classmate, ask a TA or Instructor, or watch a video of Ivan do it with an older version of Rails and MiniTest
            - http://www.youtube.com/watch?v=0pl-h-CHWEA
        - Now create a test (remember what the docs said about how to create a new feature test???) in the test/features/ directory (make the directory if you don't have it) that visits the root of your Rails app to ensure the Welcome index view is showing.
        - Ensure your specs runs as the default task when you run `rake`
        - It should fail. That's ok! If you see an error, ensure everything is set up correctly.
    - GREEN
      - There is an example of the WelcomeController in the official Ruby on Rails Getting Started Guide. #Read (but do not do-along) up through section 4: http://guides.rubyonrails.org/getting_started.html
      - Create a Welcome controller to handle static pages
        - type `rails` to #Read the list of available CLI commands that rails offers
        - type `rails generate` to #Read all the generators that are available in your rails project
        - type `rails generate controller` and #Read the docs on the Rails controller generator
        - Use that info to create a Welcome controller with an index view
        - Look carefully at each file that is generated. Delete any unwanted files before committing your changes.
      - Basic Rails Routing
        - A route is how your app maps URLs to a Rails controller. "The Rails router recognizes URLs and dispatches them to a controller's action" - http://guides.rubyonrails.org/routing.html
        - You need to set the "root" route. (Don't you just love saying that, no matter what your accent is?).
          - Check out and read the comments in config/routes.rb
          - For example, if you wanted to create a default route to a controller called "pigs" and an action called "fly" you would type:
            "root 'pigs#fly'"
          - You need to create a root route to your home controller and the index action
    - REFACTOR
      - Customize the HTML template
        - If you want to change the <title> tag of the page, where would you go?
          - Hints: The title tag is something in the page layout, that is set application wide right now.
          - Is it M,V, or C?
      - Add some basic information about you. Why would someone want to hire you? What you add doesn't have to be styled well, but try to structure it with basic HTML.
  - As a Rails developer, I want a roadmap of what I need to know so that I can always move towards achieving mastery
    - Updated Map: http://hijk.it/1v0B0f441K1h
    - #Read the overview essay: https://www.codefellows.org/blogs/this-is-why-learning-rails-is-hard
