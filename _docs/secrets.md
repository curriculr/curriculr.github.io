---
layout: docs
title: Secrets
side_menu:
  - title: Getting started
    url: docs/index.html
  - title: Installation
    url: docs/installation.html
  - title: Configuration
    url: docs/configuration.html
    active: true
  - title: Contribution
    url: docs/contribution.html
---

<div data-alert class="alert-box warning radius">
  <i class="fa fa-exclamation-triangle"></i> Work in progress
  <a href="#" class="close">&times;</a>
</div>

Before you can deploy Duroosi, certain pieces of information (we call secrets) have to be provided. These secrets defer from one environment to another and from one application instance to another and are stored in a file called `config/secrets.yml`. To help with the creation of this file, Duroosi comes with a `rake` task

{% highlight sh %}
rake duroosi:secrets:generate
{% endhighlight %}

which when run, will create the `secrets.yml` under the `config/` folder, if it does not exit already. Open this file and make the necessary changes. Below is a description of what theses secrets mean.

{% highlight yaml %}
  site:
    su_name: Super User
    su_email: admin@example.com
    su_password: secretive
{% endhighlight %}

These secrets identifies the name, email, and password of the super user of the application. This user is *root-like*, has an `id` = 1, and have full control over everything in the application.

{% highlight yaml %}
  database:
    adapter: postgresql # mysql or postgresql
    name: duroosi
    username: DB_USERNAME
    password: secretive
    socket: /tmp/mysql.sock
{% endhighlight %}

This is where the database is configured. To start, specify the `adapter` which tells whether the database being used is PostgreSQL or MySQL. Both are supported by Duroosi. Following that, you set the name of the database schema, db username and password needed to connect to the database server, and the socket needed for such a connection (in the case of MySQL database server).

{% highlight yaml %}
  storage:
    type: file
    asset_host: 'http://localhost:3000'
{% endhighlight %}

This is how and where we specify how updated course materials are stored. The `type` setting can take one two values: `file` or `fog`. `file` type indicates that uploaded files are stored in the same machine running the application. `fog` type allows Duroosi to upload files into other cloud-based file services such as [Amazon S3](http://aws.amazon.com/s3/), [Rackspace Cloud Files](http://www.rackspace.com/cloud/files/) or [Google Storage](https://cloud.google.com/storage/).

If type is `fog`, the following settings will have to be provided as well.

{% highlight yaml %}
    fog:
      directory: AWS_DIRECTORY
      public: true
      AWS:
        aws_access_key_id: xxx                 # required
        aws_secret_access_key: yyy             # required
        region: eu-west-1                      # optional, defaults to 'us-east-1'
        host: s3.example.com                   # optional, defaults to nil
        endpoint: https://s3.example.com:8080  # optional, defaults to nil
{% endhighlight %}

for Amazon S3,

{% highlight yaml %}
    fog:
      directory: RACKSPACE_DIRECTORY
      public: true
      Rackspace:
        rackspace_username: xxx
        rackspace_api_key: yyy
        rackspace_region: ord                # optional, defaults to dfw
{% endhighlight %}

for Rackspace Cloud Files, and

{% highlight yaml %}
    fog:
      directory: GOOGLE_DIRECTORY
      public: true
      Google:
        google_storage_access_key_id: xxx
        google_storage_secret_access_key: yyy
{% endhighlight %}

for Google Storage.

{% highlight yaml %}
  auth_mailer_sender: admin@example.com
{% endhighlight %}

This is the `from` email used for authentication emails. 

{% highlight yaml %}
  auth: 
    facebook:
      id: AUTH_FACEBOOK_ID
      secret: AUTH_FACEBOOK_SECRET
    google:
      id: AUTH_GOOGLE_ID
      secret: AUTH_GOOGLE_SECRET
{% endhighlight %}

Duroosi allows users with existing `facebook` and `google` accounts to bypass the registration step and sign in. Use the above settings to specify such authentication providers. 

{% highlight yaml %}
  secret_key_base: e0fa05385ec9e9a58b818ec08e...
{% endhighlight %}

This is required by Rails and typically used to generate a secret for cookie sessions. It can be generated be running the `rake` task:

{% highlight sh %}
rake secret
{% endhighlight %}

Finally use proved the specifics and credentials of the mailing service.

{% highlight yaml %}
  mailer:
    host: MAILER_HOST
    port: 587
    domain: MAILER_DOMAIN
    username: MAILER_USERNAME
    password: MAILER_PASSWORD
{% endhighlight %}
