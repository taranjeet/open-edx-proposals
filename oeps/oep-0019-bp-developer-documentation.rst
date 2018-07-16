#################################
OEP-0019: Developer Documentation
#################################

+-----------------+--------------------------------------------------------+
| OEP             | :doc:`OEP-0019 </oeps/oep-0019>`                       |
+-----------------+--------------------------------------------------------+
| Title           | Developer Documentation                                |
+-----------------+--------------------------------------------------------+
| Last Modified   | 2018-04-26                                             |
+-----------------+--------------------------------------------------------+
| Authors         | Grant Goodman                                          |
|                 | Robert Raposa                                          |
+-----------------+--------------------------------------------------------+
| Arbiter         | Albert (AJ) St. Aubin <astaubin@edx.org>               |
+-----------------+--------------------------------------------------------+
| Status          | Draft                                                  |
+-----------------+--------------------------------------------------------+
| Type            | Best Practice                                          |
+-----------------+--------------------------------------------------------+
| Created         | 2018-03-27                                             |
+-----------------+--------------------------------------------------------+
| `Review Period` | <start - target end dates for review>                  |
+-----------------+--------------------------------------------------------+
| `Resolution`    | <links to any discussions where the final              |
|                 | status was decided>                                    |
+-----------------+--------------------------------------------------------+

.. contents::
   :local:
   :depth: 2

*****************
IN PROGRESS NOTES
*****************

The following section is a set of assorted notes for developing this OEP. This entire section should no longer exist at
some point.  Definitely before accepting, and also potentially before full review.

============================
General Questions / Comments
============================

* This OEP might want to be broken down into more than one rST file.  One section of the OEP could include future ideas
  for the OEP, since we don't know everything, but we want to land what we do know.

   * Note that everything beyond the "IN PROGRESS NOTES" section is still fair game for adjustments. We may not want to
     follow the full initial OEP format for this particular OEP.

* Nimisha has notes on developer documentation in `this slide in the Architecture Onboarding Presentation`_.

    * [Robert] EdX Courses for learning is probably beyond the scope of this first OEP.

* Nate/Nimisha tested exchanging draw.io diagrams via XML and VSDX which are sharable via github.  However, we are
  still using LucidChart. This is an interesting idea that shouldn't get lost, but premature for commitment in this
  OEP.

* From Nate:

   * Idea: use `Algolia`_ to search ALL of these resources including edx-code, openedx-operations  Slack archive
     and Confluence. Algolia is `free for open source projects`_.

      * [Robert] We have no story for documentation discovery and I think this is wildly important, so I'd like to see
        this topic addresses in the OEP, even if it just mentions this as a next step.

   * Issue: http://docs.edx.org/ is missing ecommerce docs. Not for the OEP, but where/how do we track doc issues?

* Where should we host a TOC/Index of our docs?

  * Nate got a `draft TOC started here`_.

  * We discussed having a developer-docs repo, and oeps could move here (and we could remove the open-edx-proposals
    repo).

  * Here is another `Developer Documentation landing page`_ in Confluence.

* Where should documentation live?

   * Possible docs directory per Django App (in addition to per repository).  This was used for oauth_dispatch decisions
     in edx-platform. This may need some automation/tooling to make this more useful (automated publishing, etc.)

   * OEP vs decision doc.  Just differs in scope?

   * Do we need a README.rst for each Django App? Does it need to live in the root (my preference).  Does it just point
     to the docs directory when needed?  Do docs directories need a README as well?  An index?

   * Can someone add general docs to an __init__.py file?  Should this be moved to a README ([Robert's] preference).

* Searching for `Developer Documentation in Confluence`_, what should be migrated to this OEP or discussed in this OEP?

   * Example is `Documentation Best Practices page`_ in Confluence.

   * There is a child page in Confluence tracking a `Best Practices and Docs TODO List`_.

      * Should we document a process for tracking missing docs? How do we track doc issues that have come up? Examples:

         * OLX docs are out of date and inaccurate. Could we get automate the process of updating these?

         * In ReadTheDocs, the theme used does not make the current version (named release) of the documentation clear
           enough. It is hard to tell when you are looking at the wrong version.

         * Is there an issue with ReadTheDocs devstack documentation vs the devstack repo document?

* Is Ops Documentation a special case that should not be covered by this OEP, or gets special coverage?

   * When there is a new project, ensure there are docs on how to run it.

* Swagger for API Documentation. Needs more automation. Could we have a staging environment against which the docs could
  function and give you access to more than you might be able to in Production?

* Community needs: How to open issues? How to update docs?

.. _this slide in the Architecture Onboarding Presentation: https://docs.google.com/presentation/d/1X3QaSw4sqPLvkXBhC8phoFA7j8dhsL08MCZWwIDMIBE/edit#slide=id.g2f682183f6_0_0
.. _Algolia: http://algolia.com/
.. _free for open source projects: https://www.algolia.com/for-open-source
.. _draft TOC started here: https://docs.google.com/document/d/11xm7JbBr0Q5MrX1lIClyOTqI-_9sqB2h_gJOfCXo9s8/edit?usp=sharing
.. _Developer Documentation landing page: https://openedx.atlassian.net/wiki/spaces/OpenDev/pages/159881063/Developer+Documentation
.. _Developer Documentation in Confluence: https://openedx.atlassian.net/wiki/dosearchsite.action?queryString=deverloper%20documentation
.. _Documentation Best Practices page: https://openedx.atlassian.net/wiki/spaces/OpenDev/pages/297861141/Documentation+Best+Practices
.. _Best Practices and Docs TODO List: https://openedx.atlassian.net/wiki/spaces/OpenDev/pages/161888472/Best+Practices+and+Docs+TODO+List

========================
rST Questions / Comments
========================

* rST Formatting Questions:

   * [Robert] I like the header format that Nimisha uses elsewhere that just uses an underline, rather than a line above
      and below. I think it has more overhead to do above and below, but I think the doc team uses this. Could we update
      templates to match our preference?

   * Do we need to keep to 80 characters per line? What tools will make this easy?

      * Could try `Insert Break After Wrapping Width 80 characters in Sublime Text 3`_

* What tools can help with rST?

   * PyCharm under development will have features, but it is broken for other reasons.

   * Nimisha uses VisualStudio Code - `Restructured Text Previewer`_.

   * `Online reStructured Text editor`_

   * `Online table generator`_ (supports multiple formats)

   * `Pandoc`_ (a universal document converter).  This can be used to convert between many formats, like Google Doc to
      rST.

     code::

         pandoc example_source.docx -f docx -t rst -s -o example_output.rst

   * Note: It looks like I got a section like this started below.

.. _Insert Break After Wrapping Width 80 characters in Sublime Text 3: https://stackoverflow.com/questions/32362277/insert-break-after-wrapping-width-80-characters-in-sublime-text-3
.. _Restructured Text Previewer: https://marketplace.visualstudio.com/items?itemName=tht13.rst-vscode
.. _Online reStructured Text editor: http://rst.ninjs.org/
.. _Online table generator: http://truben.no/table/
.. _Pandoc: https://pandoc.org/

********
Abstract
********

Developers who work on the Open edX platform, both inside and outside of edX,
need accurate and current documentation about platform architecture, APIs, and
development best practices.

**********
Motivation
**********

Developer documentation has been inconsistently and in some cases poorly
maintained. Documents exist on ReadTheDocs (RTD), in repositories on GitHub,
in Confluence, and in Google Docs. Documents are also difficult to find.

*************
Specification
*************

===========================
Documentation Format in rST
===========================

Documentation that is added to a Git repository will use the reStructuredText
(rST) format.

=======================
rST Tools and Resources
=======================

* `reStructuredText (rST) Primer`_

* `Online rST editor`_

* `Pandoc: a command line converter to and from rST`_

* Blog post about `why rST over Markdown for documentation`_.

`reStructuredText (rST) Primer`: http://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html
`Online rST editor`: http://rst.ninjs.org/
`Pandoc: a command line converter to and from rST`: https://pandoc.org/
`why rST over Markdown for documentation`: http://ericholscher.com/blog/2016/mar/15/dont-use-markdown-for-technical-docs/

======================
Types of Documentation
======================

We should distinguish between documentation that is strictly internal to edX
operations and documentation that is helpful for any Open edX platform
developers. Documentation for the Open edX platform should be maintained in the
relevant Git repository, in RST format.

==========================================
Index of Developer Documentation Resources
==========================================

Create a document that indexes all available documentation resources for
developers. This will help users discover what's available and also help edX
maintain and control the resources. Much of the information that would be
included is on the Confluence
`Developer Documentation<https://openedx.atlassian.net/wiki/spaces/OpenDev/pages/159881063/Developer+Documentation>`
page.

======================================
Developer Best Practices Documentation
======================================

Some developer best practices documentation is maintained in a RTD
documentation titled
:ref:`Open edX Developer’s Guide<http://edx.readthedocs.io/projects/edx-developer-guide/en/latest/>`.
We need to determine the best location for this content and locate other
related topics currently in Confluence that we should add to this
documentation.

==============
API references
==============

API reference documentation should be generated from code and maintained in the
related repository. We need to determine the best method for generating and
publishing API reference docs in the near future. At this point, it seems
likely that using Swagger and publishing the API reference docs within the
related repository will be the best approach.

*********
Rationale
*********

Developer documentation should aim to meet the following requirements.

   * **Discoverable**. Users must be able to find the documentation that is
     relevant to their needs.
   * **Maintainable**. Writers, editors, and reviewers should be able to
     create and modify documentation without too much effort. Anyone, inside
     or outside of edX, should have the ability to contribute to documentation.
   * **Version Controlled**. Documentation should be maintained under version
     control, which also promotes orderly review of documentation.

**********************
Backward Compatibility
**********************

We will need to migrate content from deprecated sources such as Confluence. As
part of the migration, we will need to establish a timetable for deleting
migrated content and determine a method for redirecting users to the new
location of the content.

We will need to provide resources and other support so that everyone who needs
to write documentation using RST is comfortable doing so. We have an existing
document, the :ref:`edX Style Guide<http://draft-edx-style-
guide.readthedocs.io/en/latest/index.html>`, which includes a complete
reference to using RST in the context of documentation produced by the Docs
team and published on RTD. We can produce a document based on this Style Guide
that is aimed at users outside the Docs team, and also an RST quick reference.

We should also provide standards and procedures for testing documentation.

*************************
Reference Implementations
*************************



======================
Swagger Implementation
======================

There is a
`test implementation<https://stage-edx-analyticsapi.edx.org/docs/>`_ of
Swagger for the Analytics API.

*********************
Rejected Alternatives
*********************

This statement describes any alternative designs or implementations that were
considered and rejected, and why they were not chosen.
