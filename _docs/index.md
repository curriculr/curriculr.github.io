---
layout: docs
title: Getting started
side_menu:
  - title: Getting started
    url: docs/index.html
    active: true
  - title: Installation
    url: docs/installation.html
  - title: Configuration
    url: docs/configuration.html
  - title: Contribution
    url: docs/contribution.html
---

<div data-alert class="alert-box warning radius">
  <i class="fa fa-exclamation-triangle"></i> Work in progress
  <a href="#" class="close">&times;</a>
</div>

On the client side and out of the box, Duroosi comes with a theme based on [Bootstrap 3](http://getbootstrap.com), and therefore supports all the browsers and platforms supported by it. For more information on Bootstrap 3 browser support refer to <http://getbootstrap.com/getting-started/#support>.

On the server side, Duroosi is built using

- [Ruby on Rails](http://rubyonrails.org/) &mdash; Our web application framework.
- Either [PostgreSQL](http://www.postgresql.org/) or [MySQL](http://www.mysql.com)&mdash; Our main data store.
- [Redis](http://redis.io/) &mdash; For configuration and translations.
- [ImageMagick](http://www.imagemagick.org) &mdash; Used for processing images.
- [RSepc](http://rspec.info) &mdash; Our testing framework.
- [SublimeVideo](http://www.sublimevideo.net) and [MediaElement.js](http://mediaelementjs.com) &mdash; For HTML5 video and audio playing.

A complete list of the gems used in building Duroosi is found at [Gemfile](https://github.com/aalgahmi/curriculr/blob/master/Gemfile).

One of our goals is to keep Duroosi as standard a Rails application as possible so that all the best practices of Rails development and deployment can be easily leveraged.