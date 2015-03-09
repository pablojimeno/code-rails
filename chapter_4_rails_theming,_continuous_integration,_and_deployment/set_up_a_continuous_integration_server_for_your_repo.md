## Set up a Continuous Integration server for your repo

Get your tests running in the cloud, and put a nice green badge on your README on GitHub. Can it auto-deploy when your tests pass?

Read this piece that says [Online CI Providers are the New Black](http://jolicode.com/blog/online-ci-providers-are-the-new-black
).

Read about [Getting Started with Travis CI](http://about.travis-ci.org/docs/user/getting-started/).

**Hints**:

* [rake db:migrate not working on Travis CI (via StackOverflow)](http://stackoverflow.com/questions/10591599/rake-dbmigraion-not-working-on-travis-ci-build) (the top answer)

* Check out the Markdown source of [the codefellows/portfolio repo's README](https://github.com/codefellows/portfolio/tree/chapter-4)

* Set up `.travis.yml` to deploy to Heroku whenever your build passes - follow the instructions here:

* [Introducing Continuous Deployment to Heroku](http://about.travis-ci.org/blog/2013-07-09-introducing-continuous-deployment-to-heroku/)

* `gem install travis`

* `travis login`

* `travis setup heroku` - this will automatically find your Heroku API key, and encrypt it in your `.travis.yml` file.

