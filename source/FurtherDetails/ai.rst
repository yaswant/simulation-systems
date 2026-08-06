.. -----------------------------------------------------------------------------
    (c) Crown copyright Met Office. All rights reserved.
    The file LICENCE, distributed with this code, contains details of the terms
    under which the code may be used.
   -----------------------------------------------------------------------------

.. _ai:

AI Policy
=========

The primary objective of this policy is to prevent introduction of
Intellectual Property Rights (IPR) restricted code into the simulation systems.

This policy is written so it can be reused across open source repositories
using the BSD-3-Clause licence, which does not define requirements for
AI-assisted contributions.

Scope
-----

This policy applies to AI-assisted contributions in:

* source code
* tests
* scripts and configuration
* documentation files containing code examples

For this policy, AI-assisted means content generated, completed, or
substantially refactored by a Generative AI tool.

Core Principles and Tool Restrictions
-------------------------------------

* **Risk of Public-Domain AI**: AI tools trained on public repositories can emit
  code that violates open-source licences or copyrights.
* **No Free/Personal-Tier Tools**: Use of free or personal-tier AI coding tools
  is *strictly prohibited* for project contributions.
* **Approved Enterprise-Tier Tools Only**: Contributors may only use
  enterprise-tier AI tools approved by their employing organisation or the
  repository maintainers.
* **Contributor Responsibility**: The human contributor is responsible for all
  submitted content, including correctness, licensing checks, and project
  standards compliance.

Approved enterprise-tier tools
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

An approved tool must satisfy all of the following:

* enterprise-tier licence with auditable terms of use
* terms that allow open source contribution workflows
* explicit organisational approval by employer or project maintainers
* controls appropriate to institutional IPR and data handling requirements

If a contributor cannot use an approved enterprise-tier tool, code must be
written manually.

Legal framing and BSD-3-Clause compatibility
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This policy adds process controls for AI use. It does not alter the
BSD-3-Clause licence terms, warranties, or disclaimers.

Attribution and review requirements in this policy are mandatory contribution
conditions for the simulation systems repositories.

Attribution Requirements
------------------------

If an approved Generative AI tool is used, you must provide attribution in two
places:

**1. the source file header**

Add a comment near the top of the file. Use the native comment style for the
language, for example:

.. tab-set::

   .. tab-item:: Fortran

      .. code-block:: f90

         ! Some content in this file was generated or refactored with assistance
         ! from [Tool Name] ([Model/Version]) on [YYYY-MM-DD].

   .. tab-item:: Python

      .. code-block:: python

         # Some content in this file was generated or refactored with assistance
         # from [Tool Name] ([Model/Version]) on [YYYY-MM-DD].

   .. tab-item:: C++

      .. code-block:: cpp

         // Some content in this file was generated or refactored with assistance
         // from [Tool Name] ([Model/Version]) on [YYYY-MM-DD].

**2. the commit message**

Your git commit message must identify the tool and what it assisted with, for
example:

.. code-block:: text

  Refactor spatial interpolation routines to improve performance.

  - Co-authored-by: [Tool Name] ([Model/Version])
  - Assisted-by: [Tool Name] ([Model/Version])
    for spatial interpolation optimisation.

Attribution must be specific enough for later audit. Include tool name,
model/version where available, and date in the source file header.

Internal example (non-normative)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For Met Office contributors, the following is an acceptable example tool
identifier:

* Met Office GitHub Copilot Enterprise (Claude Sonnet 4.6)

This example is provided for convenience. It does not change the requirement
that only approved enterprise-tier tools may be used.

Code Review Guidelines
----------------------

Reviewers must remember that AI-generated code is not self-authenticating.
The human contributor remains fully responsible for its contents.

Reviewer Checklist Matrix
^^^^^^^^^^^^^^^^^^^^^^^^^

+------+--------------------+------------------------------+------------------------+
| Step | Action             | Pass Criteria                | Fail Action            |
+======+====================+==============================+========================+
| 1    | Check file header  | Explicitly names approved    | Block merge if         |
|      | and commit message | enterprise-tier tool and     | free/personal tier     |
|      |                    | includes required attribution| is used                |
+------+--------------------+------------------------------+------------------------+
| 2    | Check licence      | No obvious proprietary or    | Pause merge and        |
|      | compatibility      | or restrictively licensed    | request proof of       |
|      |                    | copy-pasted snippets         | origin/provenance      |
+------+--------------------+------------------------------+------------------------+
| 3    | Assess Logic and   | Reviewer understands every   | Request revisions for  |
|      | Edge Cases         | line; edge cases are handled | "black box" code       |
+------+--------------------+------------------------------+------------------------+
| 4    | Run Test Suite     | Code passes all unit,        | Block merge until      |
|      |                    | integration, and             | tests pass natively    |
|      |                    | regression tests             |                        |
+------+--------------------+------------------------------+------------------------+

Enforcement and Remediation
---------------------------

The enforcement model is corrective-first, except where banned tools or
unresolved IPR risk is involved.

* Missing attribution: request correction before merge.
* Free/personal-tier AI use: block merge until replaced with compliant
  contribution.
* Suspected licence/IPR conflict: pause review, request provenance, and escalate
  to maintainers.

If an IPR issue is discovered after merge, maintainers should choose one of:

* revert the change
* rewrite affected code
* retain with verified, compatible attribution where legally valid
