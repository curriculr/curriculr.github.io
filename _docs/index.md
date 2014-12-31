---
layout: docs
title: Getting started
side_menu_docs:
  - title: Home
    url: docs/index.html
    active: true
  - title: Installation
    url: docs/installation.html
  - title: Configuration
    url: docs/configuration.html
side_menu_tutorials:
  - title: Administrator Guide
    url: docs/administrator.html
  - title: Instructor Guide
    url: docs/instructor.html
  - title: Student Guide
    url: docs/student.html
---

Curriculr is a free open-source online course management and delivery system designed specifically for MOOCs (Massive Open Online Courses). It was meant to be:

- **Full-fledged**: Instructors can create courses and organize their contents into units and lectures with videos, audios, images, and documents. Students can enroll in classes, participate in discussions, attend lectures, attempt quizzes and exams, and track their progress.

- **Internationalized**: It comes out of the box with support for two locales `en` (English) and `ar` (Arabic); and other locales can easily be added.

- **Multi-tenant**: Tenants, which are called accounts (not to be confused with user accounts) are identified by subdomains and are completely separate from one another. Each account (tenant) acts as if it is a separate site with its own configuration, courses, users and theme.

- **Themeable**: It supports themes and theme inheritance. Adding a new theme can be as easy as providing a name and changing a few CSS style classes.

- **Extensible**: It was designed to be extensible by means of other gems, plugins or mountable engines; just like any other Rails application.

On the client side, Curriculr supports all the browsers and platforms supported by [Bootstrap 3](http://getbootstrap.com). For more information on Bootstrap 3 browser support refer to <http://getbootstrap.com/getting-started/#support>.

On the server side, Curriculr is built using

- [Ruby on Rails](http://rubyonrails.org/) &mdash; Our web application framework.
- Either [PostgreSQL](http://www.postgresql.org/) or [MySQL](http://www.mysql.com) &mdash; Our main data store.
- [Redis](http://redis.io/) &mdash; For configuration, translations, and background jobs.
- [Sidekiq](http://sidekiq.org) &mdash; For background processing.
- [ImageMagick](http://www.imagemagick.org) &mdash; For processing images.
- [Minitest](https://github.com/seattlerb/minitest), fixtures, and [Capybara](https://github.com/jnicklas/capybara) &mdash; For testing.
- [MediaElement.js](http://mediaelementjs.com) &mdash; For HTML5 video and audio playing.

A complete list of the gems used in building Curriculr is found at [Gemfile](https://github.com/curriculr/curriculr/blob/master/Gemfile).

Our goal is to keep Curriculr as standard a Rails application as possible so that all the best practices of Rails development and deployment can easily be leveraged.