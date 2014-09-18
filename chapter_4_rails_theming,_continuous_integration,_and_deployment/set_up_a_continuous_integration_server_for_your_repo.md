# Set up a Continuous Integration server for your repo.
Get your tests running in the cloud, and put a nice green badge on your README on GitHub. Can it auto-deploy when your tests pass?

Read: <br>
http://jolicode.com/blog/online-ci-providers-are-the-new-black


* https://travis-ci.org
    * Read: http://about.travis-ci.org/docs/user/getting-started/
    * Read: http://stackoverflow.com/questions/10591599/rake-dbmigraion-not-working-on-travis-ci-build (top answer)
    * Hint:
        * Check out the Markdown source of https://github.com/codefellows/portfolio/blob/chapter-4/readme.md
        * Set up .travis.yml to deploy to Heroku whenever your build passes
            * http://about.travis-ci.org/blog/2013-07-09-introducing-continuous-deployment-to-heroku/

                    gem install travis
                * travis login

