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
  - title: For administrators
    url: tutorials/administrator.html
  - title: For instructors
    url: tutorials/instructor.html
  - title: For students
    url: tutorials/student.html
---

<div data-alert class="alert-box warning radius">
  Work in progress
  <a href="#" class="close">&times;</a>
</div>

At its core, Curriculr is an online learning management system. It can be used with MOOCs (Massive Online Open Courses) as well as with courses with limited-audience. Whether the course if for Arts or Mathematics, Literature or Techonologe, Instruction or training Curriculr provides a simple and powerfull platform for all.

Curriculr users or of three kinds: administrators, faculty, and students. Administrators oversee the site and have access to everthing in it. Faculty users create and build courses. Students see available classes and can enroll on any class they choose. Once enrolled in a class, they'll be able to attend lectures, attempt assessments, read documents, watch videos, and participate in class discussions. 

It's imperative to understand how Curriculr separates courses and classes. As indicated in the figure below, courses are created and managed be instructors. They encompass everything form the syllabus to the videos to the questions and assessments. The represent the learning content and how it's organized. Students don't see courses directly at all.

![Course vs class]({{ site.baseurl }}/images/tutorial-intro-fig01.png)

Courses are made avialable to students through classes. These classes carry the courses names and are open to students for a given period of time. In a sense, classes are windows through which students can briefly peek into courses and consume/interact with its materials. 

In Curriculr, to publish a course is to create a class with begin and end dates. Once the class is approved, it shows up under the main `Classes` menu and intersted students can enroll in it. In a way class is like a session of the course. All students interations such as assessments attempts, lecture attendance, and discussion participation are tied to the class and not directly to course.

Curriculr takes this approach as oppopsed to publish the course directly for two main reasons:
- To allow course contents and materials to be re-used (without copying) in multiple classes. 
- To allow flexiblity int he since that a course can have multiple classes open at different times or at the same time to the same or different audiences.
- A class in this sense, represent an interval in the life of a course which can continue to be developed and fine tuned with each class. It represents a version or snapshot of the course at one point of time.

The importance of the distinction between courses and classes is paramound in Curriculr and evident in how Curriculr is desinged and implemented and how its components are presents the different kinds of users.