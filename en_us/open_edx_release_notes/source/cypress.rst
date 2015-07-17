####################################
Open edX Cypress Release
####################################

This page lists the highlights of the Cypress release.

.. contents::
 :depth: 1
 :local:

************************************************
More Information on Cypress Release Changes
************************************************

The `edX Release Notes`_ contain a list of weekly changes that are deployed to
edx.org. Those changes are part of the master branch of the edX Platform in
GitHub.

You can also find `release announcements`_ on open.edx.org, which list changes
in each release on edx.org. You can subscribe to have release announcements
sent to your email account.

Changes listed on July 17, 2015 and before are included in the Cypress release
of Open edX.

.. Confirm date 

**************
New Features
**************

.. contents::
 :depth: 1
 :local:

======================================
Single Sign-On
======================================

TBP

======================================
LTI Provider
======================================

TBP

======================================
Feedback and Hints in Common Problems
======================================

You can now add feedback, hints, or both to the following problem types.

* Checkbox
* Dropdown
* Multiple choice
* Numerical input
* Text input

In Studio, you can use new templates to add sample problems that use the
feedback and hint syntax.

For more information, see `Adding Feedback and Hints to a Problem`_ in
*Building and Running an Open edX Course*.

=====================
Poll and Survey Tools
=====================

You can now include two new types of components in your courses.

* Use the Poll tool to pose a question to learners and have them select an
  answer from a set list.

  For more information, see `Poll Tool`_ in *Building and Running an Open edX
  Course*.

* Use the Survey tool to pose multiple questions to learners and have them
  select an answer for each question from a set list.

  For more information, see `Survey Tool`_ in *Building and Running an Open edX
  Course*.

When you include polls and surveys in a course, you can analyze the responses
and also choose whether to let learners see the aggregate answers for the
class.

=====================
Custom Courses
=====================

You can create a custom course in the edX platform (CCX) to reuse course content. By using a CCX, you can run some or all of an existing course for a group of students on a new schedule.

For information on enabling CCX in your instance, see `Enabling Custom
Courses`_ in *Installing, Configuring and Running the Open edX Platform*.

For information on using CCX, see `Creating a Custom Course`_ in *Building and
Running an Open edX Course*.

=====================
Creative Commons
=====================

Course teams can now specify either "All Rights Reserved" or a Creative Commons license for course content as a whole as well as for each individual video in the course. 

For more information, see the following documentation:

* For configuring your Open edX instance, see `Enabling Course and Video
  Licensing`_ in *Installing, Configuring, and Running the Open edX Platform*.

* For licensing course content, see `Licensing a Course`_ in *Building and
  Running an Open edX Course*.

* For licensing information for learners, see `Course and Video Licenses`_ in
  the *Open edX Learner's Guide*.

==========================
Randomized Content Blocks
==========================

Course teams can now include a new type of component, a randomized content
block, in their courses. These components randomly draw problems from a
predefined library of components and present them to learners.

You create and maintain libraries of components separately from courses. All of
an organization’s course teams can work collaboratively to develop the problems
that the libraries contain. Each library can then be referenced by randomized
content blocks in any of that organization’s courses. 

For more information, see `Working with Libraries`_ *Building and Running an
Open edX Course*.

=====================
User Profiles
=====================

With the new Open edX User Profile, you can share information about yourself
with your learning community. Your profile can include an image that identifies
you on the Open edX site as well as your location and other biographical
information. Course teams and other learners in your courses can view your
profile.

For more information, see `Exploring the Profile Page`_ in *Building and
Running an Open edX Course* and `Exploring the Profile Page for Learners`_ in
the *Open edX Learner's Guide*.

*************************************
Changes for Course Staff and Learners
*************************************

=========
Cohorts
=========

Cohort creation and management has moved from the **Advanced Settings** page in
Studio to the Instructor Dashboard in the LMS. Course teams can use the new
Cohorts tab there to add and rename cohorts, change a cohort’s assignment
method, associate cohorts with content groups, and specify whether course-wide
and content-specific discussions are divided by cohort.

For more information, see `Including Learner Cohorts`_ in *Building and Running
an Open edX Course*.

==========================
Course Certificates
==========================

You can now create one certificate configuration per course to serve as the
template for certificates issued for all of the enrollment tracks available for
your course (such as "honor code" or "verified"). Honor code certificates use
the organization logo and signatory information, but do not include signature
images, which are used only for verified certificates.

For more information, see `Setting Up Course Certificates`_ in *Building and Running an Open edX Course*.

==========================
HTML Spell Check in Studio
==========================

When you edit an HTML component in Studio, an automated spell checker indicates
any misspelled words. The spell checker automatically uses the dictionary that
is set for your browser.

======================================
Problem Appearance Changes
======================================

To make the edX LMS easier to use on mobile devices, the appearance of common
problem types has changes. For example, a border surrounds options for multiple
choice and checkbox problems, making it easier for learners to select an
option.

==========================
Problem Grade Report
==========================

For any course, you can now calculate grades for problems and generate a report
that can be downloaded from the instructor dashboard. This new report includes,
for each graded problem, a learner’s earned and possible points, and their
total score, expressed as a decimal. 

For more information, see `Generate a Problem Grade Report for Enrolled
Students`_ in *Building and Running an Open edX Course*.

====================================================
Grade Report Enhancements
====================================================

The grade report now includes new columns with certificate status and
enrollment track information. When course teams generate the grade report from
the Instructor Dashboard, they can see the following additional information for
each learner.

* Enrollment track: honor, verified, or professional education. Verification
  status, to identify learners in the verified or professional track who have
  completed identity verification with edX.

* Certificate eligibility status, to identify learners who have earned the
  passing grade in the course at the time of the grade report generation.

* Certificate delivery status, to identify learners who have received their
  certificates. The type of certificate, for learners who are eligible to
  receive a certificate.

For more information, see `Interpret the Grade Report`_ in *Building and
Running an Open edX Course*.

====================================================
Report for Not-Yet Enrolled Students
====================================================

Course teams for invitation-only courses can now track enrollment status from
the Instructor Dashboard. The Data Download page of the Instructor Dashboard
now includes a downloadable report of learners who have been invited to enroll
in a course, but who have not yet done so.
`
For more information, see the `Enrollment`_ section in *Building and Running an
Open edX Course*.

======================================================
Original Open Response Assessment Problems Depracated
======================================================

When you access a course that contains an open response assessment created
using the original version of this assignment type (ORA 1), Studio now displays
the message, “This course uses features that are no longer supported.”

A newer version of the open response assessments feature (ORA 2) was released
over a year ago, and the ability to add ORA 1 problems was removed from Studio
in May 2014.

For information about adding ORA 2 problems to a course, see `Open Response
Assessments`_.

==========================
New Studio Templates
==========================

This release includes new templates for HTML and problem components. These
templates provide updated guidelines and examples, accessibility information,
and links to documentation.

************************************************
Accessibility Updates to Studio and the LMS
************************************************

.. add summary list

************************
Changes to edX Insights
************************

.. contents::
 :depth: 1
 :local:

====================================================
Graded and Ungraded Problems in edX Insights
====================================================

.. check http://edx.readthedocs.org/projects/edx-release-notes/en/latest/2015/04-09-2015.html

====================================================
Insights - All problem parts now combined
====================================================

.. check http://edx.readthedocs.org/projects/edx-release-notes/en/latest/2015/06-23-2015.html#all-problem-parts-now-combined

====================================================
Insights - Per Problem Performance Data
====================================================

.. check http://edx.readthedocs.org/projects/edx-release-notes/en/latest/2015/06-23-2015.html#all-problem-parts-now-combined

*************
New Events
*************

.. add summary list

*****************
REST API Changes
*****************

.. check Course structure:  http://edx.readthedocs.org/projects/edx-release-notes/en/latest/2015/04-15-2015.html

.. check Video data: http://edx.readthedocs.org/projects/edx-release-notes/en/latest/2015/05-19-2015.html#edx-data-analytics-api

.. check Profile images:  http://edx.readthedocs.org/projects/edx-release-notes/en/latest/2015/06-10-2015.html#edx-platform-apis
   

.. include:: links.rst