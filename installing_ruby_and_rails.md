# 0.3 Installing Ruby and Rails

##Ensure your laptop setup meets the following requirements:
  - Ruby 2.1.2 at the latest patch level.
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

##Setup for Mac OS X 10.9 or above

####Install Homebrew including latest git and qt
```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
  - follow the prompt to install command line tools
  - once the installation is successful and home brew is installed

```
brew doctor
```
  - if you get `Your system is ready to brew` then continue to install git. Otherwise fix the errors homebrew has provided.
  Once you fix the errors and receive `Your system is ready to brew` continue on.

```
brew update
brew install git
```
  - To verify git was installed

```
which git
```
  - you should get `/usr/local/bin/git`

```
brew update
brew install qt
```

####Install Rbenv
```
brew install rbenv ruby-build rbenv-gem-rehash
```

```
rbenv install 2.1.2 (or current patch level)
```

```
rbenv global 2.1.2 # sets 2.1.2 to default
```

- Follow our slide instructions (LINK?)
- [Another optional reference](http://www.createdbypete.com/articles/ruby-on-rails-development-setup-for-mac-osx//)  (don't bother installing mysql or redis)

#Assignment:
Paste the output of `which ruby` ,  `gem env`, and `which rails` into the assignment submission online
