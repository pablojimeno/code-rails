# 0.3 Installing Ruby and Rails

##Ensure your laptop setup meets the following requirements:
  - Ruby 2.1.1 at the latest patch level.
    - Ruby should be installed in userspace, not at the system level. If you are using `sudo` to install gems, then "you're doing it wrong".
    - If you're on a Mac, you should use the Homebrew package manager: http://brew.sh. On linux your system will already have a package manager.
  - Rails, latest version 4.1

## Setup for Ubuntu 13.04 (or latest Ubuntu)

####Choose RVM or Rbenv

- rbenv
    - follow instructions in our [slide deck (THIS LINK IS BROKEN)](http://www.stehem.net/2012/05/08/how-to-install-ruby-with-rbenv-on-ubuntu-12-04.html)

####Capybara with poltergeist gem and PhantomJS

- [Instructions for PhantomJS/Poltergeist set up on Ubuntu](http://faculty.washington.edu/ivanoats/blog/2014/01/08/setting-up-phantomjs-on-ubuntu/)
- fedora: set qmake to the right version of qt

##Setup for Mac OS X

####Install XCode command line tools
(INSTRUCTIONS?)

####Install Homebrew including latest git and qt
(INSTRUCTIONS?)

####Install Rbenv
```
brew install rbenv ruby-build rbenv-gem-rehash
```

```
rbenv install 2.1.1 (or current patch level)
```

```
rbenv global 2.1.1
```

- Follow our slide instructions (LINK?)
- [Another optional reference](http://www.createdbypete.com/articles/ruby-on-rails-development-setup-for-mac-osx//)  (don't bother installing mysql)

#Assignment:
Paste the output of `which ruby` ,  `gem env`, and `which rails` into the assignment submission online

