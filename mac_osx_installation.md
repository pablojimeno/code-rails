# Setup for Mac OS X 10.9 or above

You should have ruby 2.0 installed by default. You can use this "system ruby" to install a number of helpful tools to let you customize your dev environment.

## Install Homebrew, latest git, and qt

Homebrew is a package manager for Mac. It will now be the first place you look when you need to install or update something. To install the `brew` command, use your system ruby to run a script from the homebrew repo:

```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
Follow the prompt to install **command line tools**.

Once the installation is successful and home brew is installed, run:

```
$ brew doctor
```
 If you get `Your system is ready to brew` then continue to install git. Otherwise fix the errors homebrew has provided.

 Once you fix all the errors and receive `Your system is ready to brew` continue on by installing git with brew.

```
$ brew update
$ brew install git
```
To verify git was installed:

```
$ which git
```
…you should get: `/usr/local/bin/git`

## Configure Git
Depending on your shell, add this line to your `~/.bash_profile` or `~/.zshrc`: `export PATH="/usr/local/bin:$PATH"`

Check the version to ensure you have the latest:
```
$ git --version
```
(It should be something higher than `2.2`)


Tell your git installation who you are, and how you like it:

```
$ git config --global color.ui true
$ git config --global user.name "YOUR NAME"
$ git config --global user.email "YOUR@EMAIL.com"
$ ssh-keygen -t rsa -C "YOUR@EMAIL.com"
```

Now install "qt":

```
$ brew update
$ brew install qt
```

...and a few gems

```
$ gem install bundler
$ gem install capybara-webkit
```







