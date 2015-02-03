Heroku buildpack: Run it
=================================

Heroku buildpack that runs all scripts in a given folder

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) that will execute every script in the .run_it_scripts folder. It doesn't do anytthing else so you should use [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) to combine it with a real buildpack.

One of the use cases could be downloading, compiling and installing source based packages.

Usage
-----

    $ ls
    .run_it_scripts
    .buildpacks

    $ heroku create --stack cedar --buildpack http://github.com/dollar/heroku-buildpack-multi.git

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack
    -----> Found a .vendor_urls file
           Vendoring https://s3.amazonaws.com/my-bucket/foo.tar.gz
    ...

The buildpack will detect that your app has a `.run_it_scripts` file in the root. Each file will be executed in order. It is up to you what to put in every script :)


