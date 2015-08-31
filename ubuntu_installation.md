## Setup for Ubuntu 13.04 (or latest Ubuntu)

#### First install some dependencies for Ruby

```
sudo apt-get update
sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties
```

#### Install a Ruby Version Manager

Don't use RVM. How about using [chruby](https://github.com/postmodern/chruby)? Review it's docs for the latest setup instructions.

If you are already using RVM, go ahead and remove it. You can delete all things RVM from your system with a single command:

```
  rvm implode
```

#### Install Bundler and capybara-webkit:

```
gem install bundler
gem install capybara-webkit
```
####Install and configure Git
```
sudo add-apt-repository ppa:git-core/ppa
sudo apt-get update
sudo apt-get install git

git config --global color.ui true
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR@EMAIL.com"
ssh-keygen -t rsa -C "YOUR@EMAIL.com"
```
- To minimize how many times you have to enter your github credentials, use this when needed:
`git config --global credential.helper cache`

####Install Node.JS for CoffeeScript and the Asset Pipeline
```
sudo apt-get install -y python-software-properties python g++ make
sudo add-apt-repository ppa:chris-lea/node.js
sudo apt-get update
sudo apt-get install -y nodejs
```
