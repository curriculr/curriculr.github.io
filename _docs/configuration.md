---
layout: docs
title: Configuration
side_menu_docs:
  - title: Home
    url: docs/index.html
  - title: Installation
    url: docs/installation.html
  - title: Configuration
    url: docs/configuration.html
    active: true
side_menu_tutorials:
  - title: Introduction
    url: tutorials/introduction.html
  #- title: For administrators
  #  url: tutorials/administrator.html
  - title: For instructors
    url: tutorials/instructor.html
  - title: For students
    url: tutorials/student.html
---

Beside application secrets, there are three kinds of configurations that can be used to change the behavior of Curriculr. These configurations are stored in Redis and can be changed through the application itself given the proper authorization. They are from the top down as follows.

## Site settings 
Managed by the site's super user, these configurations apply across accounts to the whole Curriculr site. These settings are accessible by clicking the `Site settings` link under home page of the super user and look like :

![Site settings]({{ site.baseurl }}/images/config-fig01.png)

### Default Account(Tenant)
{% highlight yaml %}
default_account: main
{% endhighlight %}

This setting identifies the name/slug of the default account(tenant) of the site. This is the account that is typically associated with the main domain example.com or the www subdomain. The site must have a default account even if multitenancy is not used.

### Supported locales
{% highlight yaml %}
site:
  supported_locales:
    ar: العربية
    en: English
{% endhighlight %}

This lists all the locales supported by the site. Out of the box, Curriculr supports two locales: `en` (English) and `ar` (Arabic). Any new locale must be added to this list to be recognized.

### Available themes
{% highlight yaml %}
available_themes:
  bootstrap:
    parent:
    about: The default theme; based on Bootstrap 3.
{% endhighlight %}

This defines the themes Curriculr can use. Out of the box, Curriculr comes with a theme based Twitter Bootstrap 3 (thus the name `bootstrap`). Each defined theme can have a parent setting that points to the another theme it inherits from. The absence of such a setting indicates that the theme does not inherit from any other other.

### Google Analytics
{% highlight yaml %}
analytics:
  tracking_id: 'UA-11122233-3'
  domain: 'example.com'
{% endhighlight %}

This sets up Curriculr with [Google Analytics](http://www.google.com/analytics/) for collecting site traffic statistics.

### Editor/Syntax highlighting
{% highlight yaml %}
code_editor_style: tomorrow
syntax_highlighter_style: colorful
{% endhighlight %}

Curriculr uses the [Ace](http://ace.c9.io/) code editor for editing HTML pages. you can change the `code_editor_style` to any valid Ace theme.

Similarly Curriculr uses [Pygments](http://pygments.org/) for syntax highlighting. Any valid [pygments style](http://pygments.org/docs/styles) can replace the value of `syntax_highlighter_style`

### Class filters
{% highlight yaml %}
filter_classes_by:
  language: true
  level: true
  category: true
{% endhighlight %}

Curriculr supports three ways of filtering classes: by language(Arabic, English, ...), level(basic, intermediate, advanced, ...), and by category (Arts, literature, mathematics, ...). By default all these filters are turned on. This is where you can turn some of all of them off (by replacing the value `true` with `false`).

## Account settings
Managed by the account administrator, these configurations apply only to the account (or tenant) being configured. These settings are accessible by clicking the `Account settings` link under home page of the account user and look like :

![Account settings]({{ site.baseurl }}/images/config-fig02.png)

### Account title
{% highlight yaml %}
account:
  title: Example Curriculr Site
{% endhighlight %}

This setting is used as the fallback site title.

### Default locale and time zone
{% highlight yaml %}
locale: en
time_zone: "Mountain Time (US & Canada)"
{% endhighlight %}

The default locale and time_zone of the account. The locale value must be one of the supported locales we say under the Site Settings. You can run `rake time:zones:all` to get a list of valid time zones.

### Default theme
{% highlight yaml %}
theme: 
  name: bootstrap
  fluid: false
  flavor: vanilla
  logo: true
{% endhighlight %}

This setting determines the theme used by the account. The name must match one of the available themes defined earlier in Site Settings. The other settings are theme-dependent. The `bootstrap` theme that Curriculr comes with can be configured to use fixed (default) or fluid layout. It also comes id 4 different flavors or colors: `vanilla`(default), `red`, `blue`, and `green`.

### Important emails
{% highlight yaml %}
mailer:
  send_from: admin@example.com
  contact_us_at: admin@example.com
  noreply: noreply@example.com
{% endhighlight %}

The `send_from` email specifies the email from which all emails sent by Curriculr under this account will be coming from. The second `contact_us_at` email is the email users use when they try to contact the site administrator. The last `noreply` emails is another from email indicating that users should not try to reply to the emails sent to them by Curriculr.

### Social pages
{% highlight yaml %}
social_pages: 
  facebook: https://www.facebook.com/getcurriculr
  twitter: https://twitter.com/curriculr
  google-plus: https://plus.google.com/101434561769243560321
  youtube:
  linkedin:
  github:
{% endhighlight %}

This specifies the urls to the social pages that should show up under the site footer. An empty value means not to show link.

### Uploaded file types
{% highlight yaml %} 
allowed_file_types:
  image:
    - png
    - jpg
    - jpeg
  video:
    - mp4
  audio:
    - mp3
  document:
    - pdf
  other:
    - txt
    - csv
    - dat
{% endhighlight %}

This tells Curriculr what file formats are allowed for file upload per kind. Curriculr classifies files into five categories (or kinds): images, videos, audios, documents and others.

### Permitions
{% highlight yaml %} 
  allow_file_upload: true
{% endhighlight %}

This indicates whether to allow course instructors to upload files. If it is set to `false`, the instructors will only be able to user external links.

{% highlight yaml %}
  allow_user_student_dependents: false
{% endhighlight %}

In Curriculr, a user (a person with a name, an email and a password) can enroll in classes and be a student herself or can enroll other non-user students in these classes (think of a parent -the user- enrolling her 6 and 8 year-old kids an a class). This can only happen if this setting is set to `true`.

{% highlight yaml %}
  use_gravatar: true
{% endhighlight %}

As the name implies, this tells Curriculr whether to use [Gravatar](http://en.gravatar.com/) images in displaying the avatars of users who did not upload a photo to their profile.

{% highlight yaml %}
  require_admin_approval_of_classes: true
{% endhighlight %}

Before a class is made available to students, it has to be approved. It this setting is set to `true` then an admin user must approve the class. Otherwise, the instructor himself can approve his class when he thinks is ready to be released to students.

{% highlight yaml %}
  require_admin_approval_of_blogs: true
{% endhighlight %}

If this setting is set to `true`, an admin user will have to make the post public before it can be accessible by people other thatn the author user. If set to `false`, the author user can do that herself.

## Course settings
Managed by the course instructor, these configurations apply to the course being configured. These settings are accessible by clicking the `Settings` link in the course side menue and look like :

![Course settings]({{ site.baseurl }}/images/config-fig03.png)

### Grade distribution
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

This is where the course's 100 points are divided among three categories: `assessments`, `attendance`, and `participation`. The `assessments` category is further divided into three levels: assessments at the `lecture` level, assessments at the `unit` level (a unit contains many lectures), assessments at the `course` level (a course contains many units). 

The values under each assessment level can be changed to whatever makes sense to the instructor. One instructor might choose only one final exam and no mid-term exam(s) at the `course` level, an invideo quizzes at the lecture level and nothing under the unit level, Another instructor might choose to have a distribution similar to the one above. Regardless of what distribution is adopted, the sum of all points under all categories and levels must be 100.

{% highlight yaml %}
letters:
  A: 90
  B: 80
  C: 75
  D: 60
  F: 0
passing_grade: 75
{% endhighlight %}

This tells Curriculr how points are mapped to letter grade. Setting `C: 75` means *C is 75 or above*. Similarly `B: 80` means *B is 80 or above* and so on. The `passing_grade` setting  specifies the grade at or above which the student is said to have **passed** the class.

### Default class forums
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

Every class has its own discussion forums. This is where you can specify what forums are created automatically for you when you create a new class. Under these forums, the `post_deletion_by` setting indictes who is able to delete an post (or a reply) if it has not been commented on before. In the above setting, both the admininstrator and instructor(faculty) are able to delete posts; the author isn't.

### Instructor roles
{% highlight yaml %}
staff:
  - instructor
  - assistant
  - technician
{% endhighlight %}

Courses can have multiple instructor each with a different role. These are the instructor roles that Curriculr supports. Additional roles can be added but they will be treated the same as `assistant`.

- `instructor` represents the main instructor(s) of the course which is typically a user with a `faculty` role. Instructors will be able to do anything and everything within the course.
- `assistant` can be any user and will be able to do anything and everything within the course. Assistants cannot create new courses unless they themselves are `faculty` users.
- `technician` similar to `assistant` with the exception that their names are not listed under the 'Instructor' section of the class.

### Question banks
{% highlight yaml %}
  question_banks:
    - main
    - survey
{% endhighlight %}

Curriculr organizes questions into banks. The list above specifies the banks supported by this course and can be changes to fit the course needs. The `main` question bank is the default bank that a newly created question will be assigned to unless another bank is selected. Notice that Curriculr provides a special `survey` bank to house the questions that are to be used in course surveys.

### Uploaded file types
{% highlight yaml %} 
allowed_file_types:
  image:
    - png
    - jpg
    - jpeg
  video:
    - mp4
  audio:
    - mp3
  document:
    - pdf
  other:
    - txt
    - csv
    - dat
{% endhighlight %}

This tells Curriculr what file formats are allowed for file upload per kind for this course. As mentioned begore, Curriculr classifies files into five categories (or kinds): images, videos, audios, documents and others. These settings will override the `allowed_file_types` account settings for this course.

### Permitions
{% highlight yaml %} 
allow_file_upload: true
{% endhighlight %}

This indicates whether to allow course instructors to upload files. If it is set to `false`, the instructors will only be able to user external links.

{% highlight yaml %}  
allow_user_student_dependents: false
{% endhighlight %}

This setting overrides the identically named `allow_user_student_dependents` account setting for this course and is used to allow (or prevent) a user (a person with a name, an email and a password) to enroll other non-user students in classes of this course. Think of a parent enrolling his underaged children in a klass.

{% highlight yaml %}
allow_access_to:
  syllabus: true
  lectures: true
  forums: true
  assessments: true
  reports: true
{% endhighlight %}

This setting controls what class section the students are allowed to access. By default all of the listed sections are accessible to enrolled students.


