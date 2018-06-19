==================================
OEP-0025: Incremental Improvements
==================================

+-----------------+----------------------------------------------------------+
| OEP             | :doc:`OEP-0025 <oep-0025-proc-incremental-improvements>` |
+-----------------+----------------------------------------------------------+
| Title           | Incremental Improvements                                 |
+-----------------+----------------------------------------------------------+
| Last Modified   | 2018-06-13                                               |
+-----------------+----------------------------------------------------------+
| Authors         | Jeremy Bowman <jbowman@edx.org>                          |
+-----------------+----------------------------------------------------------+
| Arbiter         | Adam Stankiewicz <astankiewicz@edx.org>                  |
+-----------------+----------------------------------------------------------+
| Status          | Draft                                                    |
+-----------------+----------------------------------------------------------+
| Type            | Process                                                  |
+-----------------+----------------------------------------------------------+
| Created         | 2018-06-13                                               |
+-----------------+----------------------------------------------------------+
| `Review Period` | 2018-06-14 - 2018-06-29                                  |
+-----------------+----------------------------------------------------------+
| `Resolution`    |                                                          |
+-----------------+----------------------------------------------------------+

Abstract
========

Proposes a process for achieving large and/or long-term Open edX project goals
via the definition and distributed completion of many small, straightforward
development tasks.

Motivation
==========

There are often relatively straightforward changes to the Open edX codebase
which prove difficult to accomplish due to the sheer amount of code involved.
These are not major new features or complex refactorings of the code, but
rather things like:

* Support a new version of Python or Django
* Replace all uses of certain deprecated code with its preferred replacement
* Find all instances of a particular antipattern and fix them

Such projects can involve changing hundreds of files and thousands of lines of
code...but they are fundamentally composed of dozens of routine, localized
changes which can be made independently and without any particular prior
knowledge of how the Open edX code is structured.  It is very difficult for
any one organization to prioritize tackling one of these projects by itself,
but once broken down into very small pieces, the benefits of distributing
them across the entire community become rapidly apparent.

Specification
=============

The `Incremental Improvements`_ (INCR) JIRA project is home to small,
straightforward tasks which must be finished in order to achieve
larger, long-term objectives of the Open edX community. All tickets in it
should have the following characteristics:

* **Quick to implement.** Ideally no more than 3 hours for a contributor who
  is already familiar with the contribution process to submit a reasonable
  pull request.

* **Small in scope.** Should not affect significantly more than 10 files,
  and not require large amounts of new or refactored code. If a similar change
  needs to be made to dozens or hundreds of files, there should be a separate
  ticket for each small batch of files (and there should ideally be a script
  to automate the change).  This keeps the pull requests easy to review so
  feedback can be provided promptly.

* **No prerequisites.** Each INCR ticket should be doable immediately, without
  waiting for another change to be made.

* **Not urgent.** While all INCR tickets are important, they do not have
  pressing deadlines. A new contributor should have time to become familiar
  with the contribution process and the changes to be made, without feeling
  pressured to submit something quickly.

* **Requires no additional information or clarification.** The ticket
  description should clearly describe exactly what needs to be done.

* **Specifies the required skill(s).** There should be labels on the ticket
  listing any skills required beyond the core ones needed to submit a pull
  request. Typical labels include "javascript", "python", "css", etc.

* **Does not require knowledge of the existing Open edX code.** All INCR
  tickets should be implementable by a contributor with the appropriate
  fundamental skills, and described assuming little or no knowledge of the
  existing Open edX codebase. It can be assumed that the contributor has read
  enough documentation to start a devstack and understand the contribution
  process.

* **Not controversial.** If the instructions in the description are followed,
  it should be feasible to promptly review and merge the changes without
  extended deliberation.

* **Contributes to a larger goal.** Each ticket belongs to an INCR "epic"
  ticket describing a significant improvement to the Open edX codebase which
  depends on this small change being completed.

.. _Incremental Improvements: https://openedx.atlassian.net/projects/INCR/issues/INCR-1?filter=allopenissues

INCR Tickets in Context
-----------------------

Note that it is entirely possible that an epic in the INCR project may not be
achievable purely through the completion of INCR tickets.  There may be
changes required which require more domain knowledge of the existing code,
can't realistically be broken down into small enough tasks, or just aren't
understood well enough to allow writing a sufficiently detailed ticket
description without basically completing the task.  This is all fine; INCR
tickets should only be written for the parts of the project for which they
are appropriate.  The rest of the work can be coordinated in a variety of
ways; examples of such coordination are given later below.

It is also not necessary to immediately detail all of the INCR tickets that
will ultimately belong to an INCR epic when it is first created.  It is
usually sufficient to initially create just a handful of tickets that allow
several developers with any appropriate skill sets to contribute.  More should
be written as the tasks are completed, so there is always something available
to work on for those interested in contributing.  Tasks which depend on other
work being finished first but otherwise qualify as INCR tickets may be created
as such, but should immediately have their status marked as ``Blocked`` and be
linked to the tickets which are blocking progress.

Who Can Work on INCR Tickets?
-----------------------------

Incremental Improvement tickets are appropriate for many kinds of contributors,
including (but not limited to):

* Developers who have an idea for a larger Open edX contribution, and want to
  practice with a smaller task first

* Students of computer programming who want to work on an important project in
  active use

* New technical employees of edX and other organizations in the Open edX
  community

* Experienced Open edX developers who want to do something productive with a
  small chunk of available time

* Hackathon teams who want to make a burst of progress on a big objective

* Technical writers who want to make gradual small improvements to the Open
  edX documentation.

When enough of an epic is complete that the scope of remaining work
becomes more manageable (or when an external deadline like end of support for
a current dependency approaches), one or more organizations in the community
may decide that it's worth making that epic a higher priority, assigning even
more developers to work on INCR tickets.

How Should Related Non-INCR Work Be Coordinated?
------------------------------------------------

As noted above, it will often be the case that at least some of the work
needed to complete an INCR epic will not be appropriate for INCR tickets.
This proposal will not attempt to dictate how that remaining work should
be done, but here are a few suggestions:

* Capture the remaining work as JIRA tickets outside the INCR project, and
  link them to the related INCR epic.  This is most appropriate if the work
  is likely to be done by edX, as it can be difficult to verify that outside
  contributors have permission to access tickets across various JIRA projects.

* Describe the remaining work in a Confluence document, and link to it from
  the description of the INCR epic.  This document should be updated as tasks
  are fleshed out, started, and completed.

* Coordinate efforts in an appropriate Open edX Slack channel.  This is not
  a substitute for an organized written enumeration of what needs to be and
  has been done, but can help when the pace of progress is rapid or there is
  confusion about what remains to be done.

Rationale
=========

Historically, edX has been relatively poor at pre-emptively completing major
framework upgrades (like Django 1.11 or Python 3).  We have also been somewhat
inefficient in replacing working but problematic code with newer solutions
which have already been demonstrated to work better in other parts of the
code.  A major contributing factor in this is that we have not effectively
enabled the Open edX community to share the burden of doing this maintenance
work.  edX keeps prioritizing work on new features in high demand by partners
in the community, while those partners get frustrated that it isn't clear how
to help and the code is somewhat dated and difficult to work with.  People new
to the project are often eager to contribute, but have no idea where to start
and get little useful guidance in that regard.

The goal of the Incremental Improvements process is to identify, document, and
bring attention to small chunks of work that can be performed by a broad
spectrum of community members and make meaningful progress towards larger
shared objectives.  The hope is that this will enable all of the following:

* Faster progress on large upgrade projects by distributing the work across
  more contributors

* A clearer path for new Open edX contributors to get started making useful
  contributions

* A simpler, cleaner codebase by allowing more developers to make progress
  on cleaning up old messes and deprecated code patterns

Rejected Alternatives
=====================

(Note that in the context of this draft, "rejected" does not mean that the
alternative has been completely ruled out, rather that it seemed implausible
when first considered.)

There are limitations to using an edX-managed JIRA project as the primary
system of coordination for Incremental Improvement tickets.  Contributors
outside of edX have limited ability to update and comment on the tickets,
and the system is not exactly intuitive for users who have not used JIRA
before.  Nevertheless, the other considered options seem to have even
greater obstacles:

* While GitHub Issues are a common choice for many open source projects,
  the distribution of Open edX code across dozens of repositories makes it
  very difficult to find the answers to simple questions like "what
  incremental improvement tasks are available to work on?" and "is there a
  sufficient backlog of tickets for new contributors to choose from?".  Such
  challenges could probably be overcome with automation, but that presents
  a significant barrier to even getting started creating and processing tasks.

* There was a suggestion to use the existing edX JIRA projects and use a label
  to identify incremental improvement tickets, but these projects greatly
  differ in access permissions and workflow.  Trying to find these tickets and
  identify which ones haven't been completed could be very difficult for even
  experienced JIRA users who don't have broad access to the edX JIRA system.

* A system other than the edX JIRA could be used, to make it easier to grant
  write access for contributors throughout the community.  A choice could be
  made which would also be more intuitive for developers who don't already
  have extensive experience with JIRA.  But this would isolate the Incremental
  Improvements work from the tracking system used for other Open edX work, and
  risks leaving the tasks unseen by the core contributors whose participation
  is needed to define and review them.

Other suggestions for handling this more elegantly are welcome, but understand
that there is significant resistance against either adding a second issue
tracker that edX employees would need to routinely use and monitor, or moving
core edX development from JIRA to a different issue tracker.

Change History
==============
