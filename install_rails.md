# Install Ruby and Rails


## Install a Ruby Version Manager

Don't use RVM. 

If you are already using RVM, go ahead and remove it. You can delete all things RVM from your system with a single command:

```
  rvm implode
```

How about using [chruby](https://github.com/postmodern/chruby)? Review it's docs for the latest setup instructions.

For easier installation of multiple ruby versions, use `ruby-install`. Get it going by reading the docs.

## Install Bundler and capybara-webkit:

```
gem install bundler
gem install capybara-webkit
```

## Install Rails

Now that you are humming along on the latest ruby, let's get the latest (stable) rails. It's as easy as:

```
$ gem install rails
```

Verify:
```
$ rails -v
Rails [version number]
```

