Heroku buildpack: Run it
=================================

Heroku buildpack that runs all scripts in a given folder

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) that will execute every script in the ```.buildpack_run_scripts``` folder. It doesn't do anytthing else so you should use [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) to combine it with a real buildpack.

This buildpack can be used as a method to download, compile, do fancy processing of data and install source based packages.

Usage
-----

    $ ls
    .buildpack_run_scripts
    .buildpacks

    $ heroku create --buildpack http://github.com/dollar/heroku-buildpack-multi.git

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack
    =====> Downloading Buildpack: https://github.com/fnavarrog/heroku-buildpack-run-scripts
    =====> Detected Framework: RunScripts
    -----> Found a folder to execute (/tmp/buildpackWkgFp/.buildpack_run_scripts)
    -----> Running '/tmp/buildpackWkgFp/.buildpack_run_scripts/00_generic_script.sh'
           hip, hip, horray!
    ...

The buildpack will detect that your app has a `.buildpack_run_scripts` file in the root of the application. Each file will be executed in alphabetical order (find). It is up to you what to put in each script :)


