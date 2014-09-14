## Setup for Ubuntu 13.04 (or latest Ubuntu)

- first install some dependencies for Ruby

```
sudo apt-get update
sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties
```

####Choose RVM or Rbenv

- rbenv:

```
cd
git clone git://github.com/sstephenson/rbenv.git .rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL

git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
exec $SHELL

rbenv install 2.1.2
rbenv global 2.1.2
ruby -v
```
- rvm:

```
sudo apt-get install libgdbm-dev libncurses5-dev automake libtool bison libffi-dev
curl -L https://get.rvm.io | bash -s stable
source ~/.rvm/scripts/rvm
echo "source ~/.rvm/scripts/rvm" >> ~/.bashrc
rvm install 2.1.2
rvm use 2.1.2 --default
ruby -v
echo "gem: --no-ri --no-rdoc" > ~/.gemrc
```

####Configure Git
```
git config --global color.ui true
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR@EMAIL.com"
ssh-keygen -t rsa -C "YOUR@EMAIL.com"
```
####Install Rails

```
gem install rails
```
- if you are using rbenv you need to make the rails executable available

```
rbenv rehash
```
- to make sure you have installed rails correctly:

```
rails -v
# Rails 4.1.5
```

####Capybara with poltergeist gem and PhantomJS

- [Instructions for PhantomJS/Poltergeist set up on Ubuntu](http://faculty.washington.edu/ivanoats/blog/2014/01/08/setting-up-phantomjs-on-ubuntu/)
- fedora: set qmake to the right version of qt
