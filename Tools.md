# Tools

Those are some tools that perform static code analysis, or profiling for the application to indicate problems in rails coding style, database queries performance or security threats.

Some of them are run one time producing a report, others are always running with the application indicating potential problems

## Table of Contents

* [Code Style](#style)
	* [Rails Best Practices](#rails-best-practices)
	* [Robocup](#robocup)
* [Performance](#performance)
	* [Bullet](#bullet)
* [Security](#security)
	* [Brakeman](#breakman)

<a name="style"/> Code Style
==========

<a name="rails-best-practices">Rails Best Practices</a>
--------------------
> rails_best_practices is a code metric tool to check the quality of rails codes.

To use:

add in gem file under the `:development` group

    gem "rails_best_practices"

Bundle, then run:

    rails_best_practices -f html

in the project's main directory, this will produce an HTML report with the probles found in the root directory of the project `rails_best_practices_output.html`, for all the options available type:

    rails_best_practices -h

For more details visit: [https://github.com/railsbp/rails_best_practices](https://github.com/railsbp/rails_best_practices)

<a name="robocup">Robocup</a>
-------

<a name="performance">Performance</a>
===========

<a name="bullet">Bullet</a>
------

> The Bullet gem is designed to help you increase your application's performance by reducing the number of queries it makes. It will watch your queries while you develop your application and notify you when you should add eager loading (N+1 queries), when you're using eager loading that isn't necessary and when you should use counter cache.

To use:

add in gem file under the `:development` group:

    gem "bullet"

then in `development.rb` add :

    config.after_initialize do
        Bullet.enable = true
        Bullet.console = true
    end

This will log the warnings in the browser console, you have to navigate to all the pages that performs database queries for the gem to show warnings about them.

Example query without optimization

    @neighborhood.shouts.keep_if {|shout| shout.user != @user && shout.comments.select {|c| c.user == @user}.empty?}

Bullet will show two warnings here

- The user of the shouts isn't retreived ahead
- The user of the comment on the shout isn't retreived ahead

To solve this we need first to include the user of the shout

    @neighborhood.shouts.includes(:user).keep_if {|shout| shout.user != @user && shout.comments.select {|c| c.user == @user}.empty?}

This will eliminate the first warning, to eliminate the second we need to include the user of the comment on the shout

    @neighborhood.shouts.includes(:user, :comments => :user).keep_if {|shout| shout.user != @user && shout.comments.select {|c| c.user == @user}.empty?}

For more details visit [https://github.com/flyerhzm/bullet](https://github.com/flyerhzm/bullet). Also there's a rails cast on it [http://railscasts.com/episodes/372-bullet](http://railscasts.com/episodes/372-bullet)

<a name="security">Security</a>
========

<a name="brakeman">Brakeman</a>
--------
> Brakeman is a static analysis tool which checks Ruby on Rails applications for security vulnerabilities.

To use:

add in gem file under the `:development` group:

    gem 'brakeman', :require => false

Bundle, then run:

    brakeman -o output.html

in the project's root directory, the output format is determined by the file extension or by using the -f option. Current options are: `text`, `html`, `tabs`, `json` and `csv`.

For more details visit: [https://github.com/presidentbeef/brakeman](https://github.com/presidentbeef/brakeman)