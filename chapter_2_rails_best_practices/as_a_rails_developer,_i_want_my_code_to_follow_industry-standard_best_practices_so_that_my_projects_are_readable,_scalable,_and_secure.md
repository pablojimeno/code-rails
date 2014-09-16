# As a Rails developer, I want my code to follow industry-standard best practices so that my projects are readable, scalable, and secure

## Rails conventions:
### Read about READMEs
Take action after reading this article, written by a Code Fellows alumna: http://www.stephaniehekker.com/why-you-should-write-a-readme-for-your-application/

Decide on what **you** want to use as a standard README format for all your projects. Fork Stephanie's template, and modify to own desires, so you have a ready-to-go README to use for your assignments.

### Code for clarity:

- Read [Chpater 1 of Clean Code](https://www.dropbox.com/s/y9jxxvlgnbocvn7/Chapter%201%20-%20Clean%20Code%20-%20A%20Handbook%20of%20Agile%20Software%20Craftsmanship.pdf), by Uncle Bob Martin

- Read [Clarity of code is clarity of thought](http://agile.dzone.com/news/clarity-code-clarity-thought)

- Review this crazy [Clean Code Cheatsheet](http://www.planetgeek.ch/wp-content/uploads/2013/06/Clean-Code-V2.2.pdf)

- Optional reading: https://medium.com/on-coding/a70ca8382884

### Ruby style guides
- Whitespace
    - 2 spaces (not tabs)
    - No whitespace at the end of the line
    - A single newline at the end of every file
- Comments
    - Read:https://github.com/bbatsov/ruby-style-guide#comments (just read up to Classes and Methods)
- Online resources:
    - Read: https://github.com/bbatsov/ruby-style-guide
    - Read and compare: https://github.com/styleguide
- Gem tool:
    - gem install rubocop
    - **DO**: run rubocop from within your project directory for your work from Chapter 1.
    - Bonus challenge: figure out how to ignore a warning (like for double-quoted strings, which Brook says is fine)
- Cloud tool:
    - Connect https://houndci.com to your repo from yesterday
    - Commit a change, and open a new PR to trigger a code audit
    - Fix up any issues highlighted
- Rails Gemfile:
    - Read: http://mcdowall.info/posts/gemfile-best-practices-and-discourse/
    - Check out this gem: https://github.com/enilsen16/Eefgilm

### Your IDE: A text editor

- Remap shift-space to underscore: http://gfxmonk.net/2009/01/29/remap-shiftspace-to-underscore.html
- How to set up Sublime Text for our conventions. Choose Sublime Text / Preferences / Settings - User and enter these settings:

```
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
```
- Install the package manager for your version of Sublime.
    - Find & install some great recommended packages.
- Get to know your editor:
    - Watch a few of these hints that look interesting to you: http://code.tutsplus.com/courses/perfect-workflow-in-sublime-text-2
    - Recommended: Multi-cursor, Instant file switching.
    - You should know this site exists: http://rails-bestpractices.com (A lot of what's there may not yet make sense. That's ok.)
