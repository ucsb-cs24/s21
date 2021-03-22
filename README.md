# ucsb-cs24/s21

Jekyll-based website for UCSB CS24 Winter 2021, for shared course materials.

* website: <https://ucsb-cs24.github.io/s21/>
* The theme currently being used can be find in the jekyll-theme value in `_config.yml`
* The navigation is set by the values in `_data/navigation.yml`

# Travis-CI


Build Status: [![Build Status](https://travis-ci.org/ucsb-cs24/w21.svg?branch=master)](https://travis-ci.org/ucsb-cs24/w21)

The continuous integration service [travis-ci.org](https://travis-ci.org) can be used to check whether a Github Pages site is
building properly, and if not, see the syntax errors.

The site for this repo is:  <https://travis-ci.org/ucsb-cs24/s21>

* At that site you can enable builds (if the logo shows grey for no info), or see a log of the latest build.
* Also, see the green dots, yellow dots, and red x's on the [Commit log of this repo](https://github.com/ucsb-cs24/s21/commits/master)
* [These instructions](https://docs.travis-ci.com/user/status-images/) explain how to add a Build Status logo to a README.md
   








To test locally:
* One time setup:
    * `git clone` the repo
    * Install rvm (the Ruby version manager)
    * Run `./setup.sh` to install correct ruby version, bundler version, and bundle the gems
* From then on, to test the site locally:
    * Run `./jekyll.sh
    * Point browser to <http://localhost:4000>
