# Course Awards Vote plugin for Moodle 2.x

Course Awards: A quick and easy way of getting a course's rating from students, awarding courses medals based on score, and reporting on courses Moodle-wide.

This '[vote](https://github.com/vaughany/moodle-block_courseawards_vote)' block: Used to collect a user's vote, and optionally a brief textual note, about the course.

> **See also:** the '[medal](https://github.com/vaughany/moodle-block_courseawards_medal)' block and the [report](https://github.com/vaughany/moodle-report_courseawards).

## News: Highlighted in May 2012 OFSTED Good Practice report

The Course Awards plugins have been highlighted in a May 2012 OFSTED Good Practice report into South Devon College, alongside Moodle itself. (Look out for 'Moodle Medals' as it's known locally.)

* [OFSTED web page](http://www.ofsted.gov.uk/resources/good-practice-resource-making-most-of-information-and-communication-technology-south-devon-college)
* [PDF](http://www.ofsted.gov.uk/sites/default/files/documents/surveys-and-good-practice/s/South%20Devon%20College%20-%20Good%20practice%20example.pdf)

## Introduction

The Course Awards plug-in system consists of two blocks ('Vote' and 'Medal') and a report. Its purpose is to easily collect user feedback about a course with appropriate back-end reporting.

It is probably a good idea to fully read through this readme before embarking on any installation or bug reporting.

## Licence

Course Awards Vote block for Moodle 2, &copy; 2013 Paul Vaughan.

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.

## Purpose

The Course Awards blocks and report form part of a much larger Moodle course rating system (called Moodle Medals) which is used to recognise good practice on Moodle courses and also provide targets for course development. Learner feedback is used to inform medals awarded, however a course must also meet or exceed other criteria to gain a medal. The Bronze medal has basic criteria which must be met, the Silver medal has moderate criteria and the Gold medal has quite strict criteria.  The criteria themselves and how they are judged is performed by staff manually: this plugin is used to inform one aspect of that process.

Irrespective of this, the blocks and report can still be used to gain useful feedback from students about Moodle courses.

## The Vote Block

![Student's view of the Vote block](http://commoodle.southdevon.ac.uk/file.php/2/course_awards_images/vote-student.png "Student's view of the Vote block") ![Student's view of the Vote block in the standard Moodle theme](http://commoodle.southdevon.ac.uk/file.php/2/course_awards_images/vote-student-basetheme.png "Student's view of the Vote block in the standard Moodle theme") ![Student's view of the Vote block once they have voted](http://commoodle.southdevon.ac.uk/file.php/2/course_awards_images/vote-student-voted.png "Student's view of the Vote block once they have voted")

**Students** get to vote by clicking on a coloured star (with tool-tip explanation of what each star means). As default, the student can also add in a brief note (this can be turned off if required).

Once a student has voted, the block changes to show them their vote and, if they left one, their note, as well as average score so far and number of votes. As default they are prevented from removing their vote and voting again for a period of one day, but this is configurable from 'immediately' to 'never', depending on preference.

![Teacher's view of the Vote block](http://commoodle.southdevon.ac.uk/file.php/2/course_awards_images/vote-teacher.png "Teacher's view of the Vote block")

**Teachers** see a summary of votes cast and notes left, but not who voted and what notes they left. Teachers cannot vote, or manage votes or notes in any way. (Note that if a person has the Teacher role in one course and the Student role in another, they can vote for the course for which they have the Student role.)

![Admin view of the Vote block](http://commoodle.southdevon.ac.uk/file.php/2/course_awards_images/vote-admin.png "Admin view of the Vote block") ![Admin view of the Vote block, expanded to show all information](http://commoodle.southdevon.ac.uk/file.php/2/course_awards_images/vote-admin-live.png "Admin view of the Vote block, expanded to show all information")

**Administrators** cannot vote, but can see and manage all votes and notes for all courses, including the history of deleted votes and notes in summary. Admins also get a direct link to the report for that course, as well as a link to the report's index page.

Once the Vote block is added to a course (by anyone with permission to do so), anyone with the role of Student can vote using a system of stars (using the UK's Ofsted grades of Outstanding, Good, Satisfactory or Poor) and can optionally write a note too.

*Note:* Only users with the role of *Student* can vote, but anyone can see the average score so far and number of votes.

### Important

Remember that one person can have different roles (e.g. student, teacher, non-editing teacher) in different courses. Simon Student may have the role of Student on course 1 but may be a Teacher on course 2, therefore will be allowed to vote on course 1 only.  This is customisable using Moodle's roles and capabilities: see the section on *Changing who can Vote* for more information.

## Installation

Installation is a matter of copying files to the correct locations within your Moodle installation, but it is always wise to test new plugins in a sandbox environment first, and have the ability to roll back changes.

Download the archive and extract the files, or [clone the repository from GitHub](https://github.com/vaughany/moodle-courseawards/). You should see the following files and structure:

    courseawards_vote/
    |-- block_courseawards_vote.php
    |-- db
    |   |-- access.php
    |   `-- install.xml
    |-- gpl-3.0.txt
    |-- img
    |   |-- 0.png
    |   |-- 1.png
    |   |-- 2.png
    |   |-- 3.png
    |   |-- d.png
    |   `-- p.png
    |-- lang
    |   `-- en
    |       `-- block_courseawards_vote.php
    |-- libvote.php
    |-- pix
    |   `-- icon.png
    |-- readme.md
    |-- settings.php
    |-- styles.css
    |-- unvote.php
    |-- version.php
    `-- vote.php

* Create a folder in your Moodle's '**blocks**' folder called '**courseawards_vote**' and place the above files into it. Do not create subfolders.

* Log in to your Moodle as Admin and click on Notifications on the Admin menu.

* The block should successfully install. If you receive any error messages, please [raise an issue on GitHub](https://github.com/vaughany/moodle-courseawards/issues).

## Using the Vote Block

* Go to a course as Teacher role or better.
* Turn on editing and add the 'Course Award - Vote' block and move it where you wish. At this time you can only add one per course.
* Students can now vote on that course. Teachers can see the number of votes and average score so far and Admins can also jump to the report.
* Delete the block in the usual manner.

> **Note:** If you remove the block, the data is retained. Simply re-add the block to get the data back.

## Configuration of the Vote block

The Vote block configuration options can only be changed by a site Admin, and affect the block throughout the whole site.

Either:

* on the Admin block, click *Site Administration &rarr; Plugins &rarr; Blocks &rarr; Course Awards - Vote*

...or:

* from the Manage Blocks screen, click on *Settings* to the right of *Course Award - Vote*.

### Vote timeout

This drop-down menu specifies how much time should pass before the voter can remove their vote and (potentially) vote again. The current range is 'no delay' to 'never'.

### Collect Notes?

As default, the block presents a small text box through which the user may write a note or comment about the course being voted on. (In reality, this will store several pages of text but the box is presented small to try to keep notes brief and concise.)

It can be turned off if notes are not required (although any already collected will be saved): simply un-tick the checkbox. Students will be presented with the same block but without the textbox.

## Changing who can Vote and Administrate the block

Installing the block gives Moodle two new capabilities:

* Administer the *Course Awards Vote* block: `block/courseawards_vote:admin`
* Vote in the *Course Awards Vote* block: `block/courseawards_vote:vote`

> **Note:** Think of capabilities as rules which govern how Moodle decides who can do things.

Also, the capabilities were specifically assigned to these roles:

* The 'administer' capability is assigned to the *Administrator* role.
* The 'vote' capability is assigned to the *Student* role.
* *Teachers* and *Non-Editing Teachers* are specifically prevented from being allowed to vote.

So when you install the block, Admins can administrate the blocks and Students can vote. This works well as a default, but you can make changes if you wish.

> ***Important:*** Teachers can still add and remove the Vote block, just as they can with any block, however this does not mean that the votes already cast will be lost. If a Vote block is removed, just add it again, and all votes will reappear.

> **Note:** *Uninstalling* the plugin drops the database tables and removes all the votes and notes for good.

### Assigning Capabilities to Roles

If you want to change the defaults for who (or more correctly, which role) can do what (has which capabilities), this is how.

* Log in to your Moodle as Administrator
* On the Admin block, click *Site Administration &rarr; Users &rarr; Permissions &rarr; Define Roles*
* Click the role you want to change. For the purposes of example, we have a role called 'School Pupil' we want to allow to vote on courses.
* Click the Edit icon (hand-and-pen) next to the role to be edited.
* Find the correct permission. This is a big list so use your browser's search function and locate '*course award*'.
* Change the permission for '*Vote in the Course Awards Vote block*' to Allow: place a tick in the checkbox.
* Scroll to the bottom of the page and click *Save*.

You should now find that anyone with the role you modified can now vote. Remember this will affect all users with that role.

> **Caution:** Caution should be exercised when assigning permissions to roles generally.

## Code and Image Changes

Some aspects of the block can be changed but this cannot be achieved though configuration, and will require changes to the code. A good code management and versioning system, such as Git, is highly recommended.

### Replacing the Images

It is quite possible to replace the default images with those of your own choosing:

* In '*blocks/coursewards_vote/*' there is an '*img/*' folder containing images.
* Replace these images with your chosen images.
* To avoid having to change the code, save new images over the existing images. Do not use new names.

> **Note:** You may want to make copies of the images before you change them so you can restore them later.

> **Caution:** The code does not specify any widths or heights for images, so that you can use your own and they do not have to be the same size as the default images. However, it is not recommended to go too much wider than the default images as you may start experiencing layout problems with your columns. Experiment.

## Known Issues

* Report:
  * Issue with [MSSQL not having a 'LIMIT' clause](https://github.com/vaughany/moodle-courseawards/issues/2).

Should you find a bug, please [log an issue in the tracker](https://github.com/vaughany/moodle-courseawards/issues) or fork the repo, fix the problem and submit a pull request.

## To Do

* Currently the reports are available to Admins only. Moodle now differentiates between site reports and course reports, so a teacher-accessible course report is on the agenda for the next version.
* Looking at the old Mods and Plugins database entry for 'Course Awards for Moodle 1.9', someone commented that clicking on a star image may not be the most accessible way of using the block, citing issues with colour-blindness and the colours potentially lacking meaning to some. The commenter also suggested some improvements so I will look into this for the next release.
* Some of the larger language string references use underscores (`admin_error`) and others use dashes (`admin-error`). For less future headaches, this should be changed. Preference is underscores.
* Logging of use of the admin reports was around in the 1.9 version, so I should probably add it back in again. For completeness' sake, if nothing else.

Suggestions for features or submissions of non-en language packs are most welcome.

## History

**January 25th 2013 - Blocks**

* Version bump for Moodle 2.4
* Build 2013012500

Tested successfully against Moodle 2.4.1.
Added the capability 'addinstance' to both blocks.

**October 11th 2012**

* Version bump for Moodle 2.x
* Build 2012101100

No major changes, just added icons and a copy of the GPL 3.0, and version bump.

**May 17th 2012 - Vote Block**

* Version 2.0.2 for Moodle 2.x
* Build 2012051700

Fixed an issue whereby a variable double-quoted in a SQL snippet failed in MS SQL and was considered a column name.

Also, changed code where required to meet Moodle's coding guidelines (using the local Codechecker) but no changes to how the code works.

**March 19th 2012 - Medal Block**

* Version 2.0.1 for Moodle 2.x
* Build 2012031900

Fixed some errors with the Medal block, added two new features:

* Fixed a redirect bug when awarding a medal (it would redirect to the main page)
* Added 'Awarded on' and date when a medal is awarded
* Added admin option to change size of pictures between regular (the default at 100px high) and small (50px high)
    * ...which necessitated adding smaller versions of the default images and an admin config page

**February 8th 2012 - Whole System**

* Version 2.0 for Moodle 2.x
* Build 2012020800
