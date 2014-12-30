---
layout: docs
title: Configuration
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

Beside secrets, there are three other kinds of configurations that can be used to change the behavior of Duroosi. These configurations are stored in Redis and can be changed by an admin user once the application is up and running. These kinds form a hierarchy such that certain configuration like `locale` defined in a lower level overrides the same configuration defined at a higher level. From the top down, these configurations are site settings, account settings, and course settings.

## Site settings 

These are configurations that apply to the whole Duroosi site. An example of these configurations is the `supported_locales` which lists all the locales recognized and supported by the site. These settings are:

{% highlight yaml %}
site:
  supported_locales:
    ar: العربية
    en: English
{% endhighlight %}

Lists all the locales supported by the site. Any new locale must be added to this list.

{% highlight yaml %}
  default_account: main
{% endhighlight %}

Identifies the name/slug of the default account(tenant) of the site. This is the account that is typically associated with the domain example.com or the www subdomain. Even if multitenancy is not used, the site must still have a default account.

{% highlight yaml %}
  sublimevideo_site_id: abc81for
{% endhighlight %}

For a superb video watching experience, Duroosi uses SublimeVideo player which requires that the admin of the site signs in to [SublimeVideo](https://my.sublimevideo.net) and add a site. Adding a site is free and upon doing that you'll get a token which should be entered here.

{% highlight yaml %}
  code_editor_style: tomorrow
  syntax_highlighter_style: colorful
  markdown_summary_delimiter: "~------\r?\n"
{% endhighlight %}

Duroosi uses the [Ace](http://ace.c9.io/) code editor for editing HTML pages. you can change the `code_editor_style` to any valid Ace theme.

Similarly Duroosi uses [Pygments](http://pygments.org/) for syntax highlighting. Any valid [pygments style](http://pygments.org/docs/styles) can replace the value of `syntax_highlighter_style`

Finally Duroosi uses Markdown for all rich text editing. `markdown_summary_delimiter` contains the value the the Duroosi Markdown editor uses to separate between a summary of a page and its body.

{% highlight yaml %}
  analytics:
    tracking_id: 'UA-11122233-3'
    domain: 'example.com'
{% endhighlight %}

Duroosi uses [Google Analytics](http://www.google.com/analytics/) to collecting site traffic statistics. This where you put your specific Google Analytics information. 

{% highlight yaml %}
  auto_generated_pages:
    about: About
    help: Help
    privacy: Privacy
    services: Services
    terms: Terms of service
    front: Front mattter
{% endhighlight %}

These are the list of pages the gets created automatically for you when first set up Duroosi. No need to change. Typically these are the pages to which you see in the site footer.

{% highlight yaml %}
  role:
    - admin
    - faculty
    - team
    - console
    - partner
{% endhighlight %}

These are the roles that Duroosi can assign to users. 

- `admin`: Indicates administrator access which allows the user to do anything and everything within the account.
- `faculty`: Gives user the ability to create courses.
- `team`: Indicates that the user is a one the sites administration team. NOT IN USE YET
- `console`: Allows the user to generate an secret API KEY that can be used to talk to Duroosi site using an RESTful API. NOT IN USE YET
- `partner`: Indicates that user is a representative of a business partner of the site. NOT IN USE YET

Notice that we don't have a specific role for students as any user save administrators can enroll in classes and act as students.

{% highlight yaml %}
  majors:
    - arts
    - sciences

  levels:
    - primary
    - secondary
    - higher

  subjects:
    - arabic
    - english
    - math
    - humanities
    - physics
    - biology
    - chemistry
    - computer
    - statistics

  filter_classes_by:
    language: true
    major: true
    level: true
    subject: true
{% endhighlight %}

These settings control how courses are tagged/classified and searched for. The default majors, levels, and subjects can changed here and their use in filtering classes can be turned on and off.

## Account settings
These configurations apply only to a certain account (or tenant). Example of these configurations is the `theme` configuration which apply a specific theme to only the account being configured. An example of such settings is:

{% highlight yaml %}
account:
  title: Example Duroosi Site
{% endhighlight %}

The site's title.

{% highlight yaml %}
  locale: en
  time_zone: "Mountain Time (US & Canada)"
{% endhighlight %}

The default locale and time_zone of the account. The locale value must be one of the supported locales under the Site Settings. You can run `rake time:zones:all` to get a list of valid time zones.

{% highlight yaml %}
  theme: 
    name: bootstrap
    fluid: false
    flavor: vanilla
{% endhighlight %}

This setting determines the theme used by the account. Out of the box, Duroosi comes with a theme based on Twitter Bootstrap 3. This theme is called `bootstrap`(no suprise here) and it can be configured to use fixed (default) or fluid layout. It also comes id 4 different flavored or colors: `vanilla`(default), `red`, `blue`, and `green`.

{% highlight yaml %}
  logo: "/images/logo/%{dark_or_light}-%{flavor}.%{locale}.png"
{% endhighlight %}

This tells Duroosi how to find the site logo and it depends on theme being used.

{% highlight yaml %} 
  allow_file_upload: true
{% endhighlight %}

This indicates whether to allow course instructors to upload files. If it is set to `false`, the instructors will only be able to user external links.

{% highlight yaml %}
  allow_user_student_dependents: false
{% endhighlight %}

In Duroosi, a user (a person with a name, an email and a password) can enroll in classes and be a student herself or can enroll other non-user students in these classes (think of a parent -the user- enrolling her 6 and 8 year-old kids an a class). This can only happen if this setting is set to `true`.

{% highlight yaml %}
  use_gravatar: true
{% endhighlight %}

As the name implies, this tells Duroosi whether to use [Gravatar](http://en.gravatar.com/) images in displaying the avatars of users who did not upload a photo to their profile.

{% highlight yaml %}
  require_admin_approval_of_classes: true
{% endhighlight %}

Before a class is made available to students, it has to be approved. It this setting is set to `true` then an admin user must approve the class. Otherwise, the instructor himself can approve his class when he thinks is ready to be released to students.

{% highlight yaml %}
  require_admin_approval_of_blogs: true
{% endhighlight %}

Clicking the `Blogs` menu at the top list all published and public blog posts. If this setting is set to `true`, an admin user will have make the post public before it can be accessible by people other thatn the author user. It set to `false`, the author user can do that herself.

{% highlight yaml %}
  mailer:
    from: admin@example.com
    to: admin@example.com
    noreply: noreply@example.com
{% endhighlight %}

The first emails is the one from which all emails sent by Duroosi in this account will be coming from. The second `to` email is the one users use when they try to contact you. The last `noreply` emails is the another from email indicating that users should not try to reply to the emails sent to them by Duroosi.

{% highlight yaml %}
  social: 
    facebook:
      app_id: "111111111111111"
      page: https://www.facebook.com/examle
    twitter:
      page: https://twitter.com/examle
    google-plus:
      page: https://plus.google.com/123123123123123123123
{% endhighlight %}

In the site footer to the left there are three links to the account related facebook, twitter, and google plus pages. Use these settings to point these links to right place.

## Course settings
These configurations apply to the course being configured and include configurations such as `grade_distribution`. An example of such settings is:

{% highlight yaml %}
course:
  grading:
    distribution:
      assessments:
        course:
           mid-term: 15.0
           final: 20.0
        unit:
          quiz: 10.0
          problem: 15.0
        lecture:
          quiz: 15.0
      attendance: 10.0
      participation: 15.0
{% endhighlight %}

This is where the course's 100 points are divided among three categories: `assessments`, `attendance`, and `participation`. The `assessments` category is further divided into three levels: assessments at the `lecture` level, assessments at the `unit` level (a unit contains many lectures), assessments at the `course` level (a course contains many units). The values under each assessment level can be changed to whatever makes more sense to the instructor. One instructor might choose only one final exam and no mid-term exam at the `course` level and a invideo quizzes at the lecture level and nothing under the unit level, while another might choose to have configuration similar to the one above. Regardless of what grading distribution across all categories and levels is like, the sum of all points must be 100.

{% highlight yaml %}
    letters:
      A: 90
      B: 80
      C: 75
      D: 60
      F: 0
    passing_grade: 75
{% endhighlight %}

This tells how points are mapped to letter grade. Setting `C: 75` should be read as *C is 75 or above*. Similarly `B: 80` should be read as *B is 80 or above* and so on. The `passing_grade` setting as the name implies specifies the grade at or above which the student is said to have **passed** the class.

{% highlight yaml %}
  discussion:
    forums:  
      - general
      - study_groups
      - assessments
    
    post_deletion_by:
      admin: true
      faculty: true
      author: false
{% endhighlight %}

Every class comes with its own discussion forums. What forums are they is determine by the `forums` list here which could be changed to the instructor's liking. Under these forums, the `post_deletion_by` settings indicte who is able to delete and post(or a reply) if it has not been commented on before. In the above setting, both the admin and instructor(faculty) are able to delete posts; the author isn't.

{% highlight yaml %}
  staff:
    - instructor
    - assistant
    - technician
{% endhighlight %}

This are the kinds of course staff that Duroosi supports. More can be added but they will be treated the same as `assistant`. In these kinds:

- `instructor` represents the main instructor(s) of the course which is typically a user with a `faculty` role. Instructors will be able to do anything and everything within the course.
- `assistant` can be any user and will be able to do anything and everything within the course. Assistants cannot create new courses unless they themselves are `faculty` users.
- `technician` similar to `assistant` with the exception that their names are not listed under the 'Instructor' section of the class.

{% highlight yaml %}
  question_banks:
    - main
    - survey
{% endhighlight %}

Duroosi uses question banks to organized course questions. The list above specifies the banks supported by this course and can be changes to fit the course needs. The `main` question bank is the default bank that a newly created question will be assigned to unless another bank is selected. Notice that Duroosi provides a special `survey` bank to house the questions that are to be used in course surveys.

{% highlight yaml %}  
  allow_user_student_dependents: false
{% endhighlight %}

In conjunction with the identically named `allow_user_student_dependents` account setting, this setting allows a user (a person with a name, an email and a password) to enroll other non-user students in classes of this course classes. This can only happen if this setting is set to `true`.

{% highlight yaml %}
  allow_access_to:
    syllabus: true
    lectures: true
    forums: true
    assessments: true
    reports: true
{% endhighlight %}

This setting controls what class section the students are allowed to access. By default all of the listed sections are accessible to enrolled students.