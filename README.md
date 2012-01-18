Heroku buildpack: nginx
=======================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpack)
for nginx.

Usage
-----

Example usage:

    $ ls -R *
    conf:
    mime.types     nginx.conf.erb

    html:
    index.html

    $ heroku create --stack cedar --buildpack http://github.com/essh/heroku-buildpack-nginx.git
    ...

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack... done
    -----> Nginx app detected
    -----> Fetching nginx binaries
    -----> Vendoring nginx 1.0.11
    ...

The buildpack will detect your app as nginx if it has the file
`nginx.conf.erb` in the `conf` directory. You must define all `listen`
directives as `listen <%= ENV['PORT'] %>;` and also include `daemon off;` in
order for this buildpack to work correctly.
