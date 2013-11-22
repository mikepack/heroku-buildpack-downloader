Heroku buildpack: Downloader
=======================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for downloading files when you deploy your project. Files are downloaded into $ROOT/downloads.
It doesn't do anything else, so to actually compile your app you should use [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) to combine it with a real buildpack.

Usage
-----
To use this buildpack, you should prepare .buildpacks file that contains this buildpack url and your real buildpack url.  

    $ ls
    .buildpacks
    ...
    
    $ cat .buildpacks
    https://github.com/mikepack/heroku-buildpack-downloader
    https://github.com/heroku/heroku-buildpack-ruby

    $ heroku create --buildpack https://github.com/ddollar/heroku-buildpack-multi

    $ git push heroku master
    ...


Add URLs to download to .downloads. Remember the UNIX standard is to leave the last line blank.

    https://www.google.com/images/srpr/logo1w.png
    https://www.google.com/images/srpr/logo2w.png
    https://www.google.com/images/srpr/logo3w.png
    (blank line)


You can verify your downloads exist by running the following command.

    $ heroku run "ls -al downloads"
    -rw-------  1 u22102 22102  151 2013-11-21 23:22 logo1w.png
    -rw-------  1 u22102 22102  151 2013-11-21 23:22 logo2w.png
    -rw-------  1 u22102 22102  151 2013-11-21 23:22 logo3w.png

