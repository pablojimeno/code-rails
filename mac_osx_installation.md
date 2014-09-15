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

####Configure Git
```
git config --global color.ui true
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR@EMAIL.com"
ssh-keygen -t rsa -C "YOUR@EMAIL.com"
```
####Installing Rails
```
gem install rails
```

- rehash rbenv and see if rails installed correctly

```
rbenv rehash
rails -v
# Rails 4.1.5
```

- [Another optional reference](http://www.createdbypete.com/articles/ruby-on-rails-development-setup-for-mac-osx//)  (don't bother installing mysql or redis)
