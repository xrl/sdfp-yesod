SDFP Haskell Webapp
===================

Whew, this was a bear to set up. It may take a while even with a fast internet connection and fast computer.

First off, do yourself a favor and use the cabal-dev package. This package is almost like Ruby's Bundler: it uses the cabal file as a library manifest and puts them in a project-specific namespace. ```cabal-dev``` does not, however, namespace the binary executable so you'll have to make sure you're runnig the correct version.

Building the App
----------------

1. ```cabal-dev install``` and go grab a coffee/lunch/dinner.
2. Install postgres and configure your app for it in config/postgres.yml
3. ```yesod -d devel``` to start a devel (auto-reloading server) using the cabal-dev namespace
4. Access your application with [http://localhost:3000](http://localhost:3000)

Yesod
-----

The big kahuna for Haskell webapps (if the number of dependencies and build time are any indication). It's got a book [O'Reilly book on Yesod](http://www.yesodweb.com/book) and quite a few blogposts. It also uses an allegedly zippy webserver. Eventually I'll rip that out for a mongrel2 ZMQ driver, but for now I'll Warp.

Deployment
----------

Given how long it takes to build the darn thing I imagine deployment will require some finesse. I do not develop on a system which looks like SDFP so I will not be able to simple ```scp``` the file over.

Postgres Setup
--------------

I advocate development setups use a local postgres installation.

```initdb -D postgres/ --username=sdfp -W```

Choose a password and remember it. Now create a database on that server.

```createdb --username=sdfp -h localhost sdfp```

Now edit config/postgres.yml with those settings.