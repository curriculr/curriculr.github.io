---
layout: docs
title: Introduction
side_menu_docs:
  - title: Home
    url: docs/index.html
  - title: Installation
    url: docs/installation.html
  - title: Configuration
    url: docs/configuration.html
side_menu_tutorials:
  - title: Introduction
    url: tutorials/introduction.html
    active: true
  #- title: For administrators
  #  url: tutorials/administrator.html
  - title: For instructors
    url: tutorials/instructor.html
  - title: For students
    url: tutorials/student.html
---

<div data-alert class="alert-box warning radius">
  Work in progress
  <a href="#" class="close">&times;</a>
</div>

Curriculr is an open and interactive learning platform that supports both MOOCs (Massive Online Open Courses) and courses with limited-audiences. Whether your course is public or private, for arts or mathematics, literature or technology, instruction or training, Curriculr provides a simple and powerful platform for all.

## Administrators, faculty and students
Curriculr supports three kinds of users: administrators, faculty, and students. Administrators oversee the site and have access to everything in it. Faculty users create and manage courses. Students browse available classes and can enroll in any class they choose. Once enrolled in a class, they'll be able to attend lectures, attempt assessments, take surveys, read documents, watch videos, participate in class discussions, and track their progress.y

An administrator is any user with the role of `admin`. Similarly a faculty user is any user with the role of `faculty`. These two roles are assigned manually to users by an existing administrator. A student, on the other hand, is any non-administrator user with at least one enrolled class.

## Course vs class
You might have noticed that we use the term `course(s)` when we talk about instructors and the term `class(es)` when we talk about students. This is because in Curriculr courses and classes are different things, and it's imperative to understand
the difference between these two terms.

![Course vs class]({{ site.baseurl }}/images/tutorial-intro-fig01.png)

As indicated in the figure above, courses are created and managed be instructors. They encompass both content (syllabus, units, lectures, questions, assessments, surveys, pages) and organization (how units are laid out, what lectures are under what units, and so on).

Students do not interact with courses directly. Instead, they are made available to students through classes. These classes carry the courses names and inherit their contents and organizations. They, however, have begin and ends dates making them more like time windows through which students can briefly peek into courses and consume/interact with their contents. In other words, a class is like a session of the course. All student interactions and activities such as assessment attempts, lecture attendance, and discussion participation are all tied to the class and not directly to the course.

In addition, to publish a course is to create a class with a begin and an end dates. Once this class is approved, it shows up under the top main `Classes` menu, and interested students will be able to enroll in it. 

In Curriculr, such separation between courses and classes serves two main purposes:

- It allows great flexibility in that a course can have multiple separate classes open at different times or at the same time to the same or different audiences.
- It separates the static from the dynamic; course content and organization are more static in nature while class activities, discussions, are updates are more dynamic and timely. Separating between these two allows for reusing the course content (without copying) over and over again by means of classes.

Finally as you'll notice later on, any instructor's guide or tutorial will be concerned with courses while any student's guide or tutorial is concerned with classes.
