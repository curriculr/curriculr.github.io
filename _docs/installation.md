---
layout: docs
title: Installation
side_menu:
  - title: Getting started
    url: docs/index.html
  - title: Installation
    url: docs/installation.html
    active: true
  - title: Configuration
    url: docs/configuration.html
  - title: Contribution
    url: docs/contribution.html
---

<div data-alert class="alert-box warning radius">
  <i class="fa fa-exclamation-triangle"></i> Work in progress
  <a href="#" class="close">&times;</a>
</div>

Before Duroosi can be deployed, the following must be done:

- Either PostgreSQL or MySQL server is installed and is ready to accept connections. Change the `Gemfile` to include the gem of the database you installed and comment out the one you did not.

{% highlight ruby %}
...

# Either postgresql  
gem 'pg'
# or mysql
#gem 'mysql2'

...
{% endhighlight %}

- Redis server is installed and ready to accept connections.
- The application *secrets* has been specified. 

## Specifying Application Secrets
To deploy Duroosi, certain pieces of information (we call secrets) have to be provided. These secrets include, for instance, Rails' `secret_key_base`  or the name, email, and password of the first user (User with `id=1`) which is a special *root-like* or *super* user with ability to do anything and everything. These secrets defer from one environment to another and from one application instance to another and are stored in a file called `config/secrets.yml`.

As the name implies, the information contained in this file are supposed to be private that should not be shared at all. It's also highly advisable that it should not be included in any source control (Git, Mercurial, or Subversion) repository. Refer to [Secrets](/duroosi/docs/secrets.html) for more information on the secrets file and its contents.

Duroosi comes with an example secrets file [config/secrets_exemple.yml](https://github.com/aalgahmi/duroosi/blob/master/config/secrets_example.yml) filled with dummy settings. To generate a secrets file based on the example file run the following:

{% highlight sh %}
rake duroosi:secrets:generate
{% endhighlight %}

This will create the `secrets.yml` under the `config/` folder, if it does not exit already. Open this file and make the necessary changes.


## Deploying the Application

Now that the application secrets are provided, you can follow the steps below to deploy Duroosi into a `development` environment.

1: Run bundler

{% highlight sh %}
bundle install
{% endhighlight %}

2: Create the database and run migrations

{% highlight sh %}
rake duroosi:db:migrate
{% endhighlight %}

3: Load the seed data

{% highlight sh %}
rake db:seed
{% endhighlight %}

This will create the default account(tenant) and the first user based on the information from the secrets file.

4: Reset Redis configurations and translations

{% highlight sh %}
rake duroosi:redis:reset
{% endhighlight %}

**Please note that** steps 2, 3, and 4 can be combined together by running

{% highlight sh %}
rake duroosi:bootstrap
{% endhighlight %}

5: Finally, run Rails server to start the application in development

{% highlight sh %}
rails server
{% endhighlight %}

## Running the Tests
To run the tests, you need to run

{% highlight sh %}
rake spec
{% endhighlight %}
