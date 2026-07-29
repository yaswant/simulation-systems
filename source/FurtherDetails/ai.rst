.. -----------------------------------------------------------------------------
    (c) Crown copyright Met Office. All rights reserved.
    The file LICENCE, distributed with this code, contains details of the terms
    under which the code may be used.
   -----------------------------------------------------------------------------

.. _ai:

AI Policy
=========

The primary objective of this policy is to prevent the introduction of
Intellectual Property Rights (IPR) restricted code into our simulation systems.

Core Principles and Tool Restrictions
-------------------------------------

* **Risk of Public-Domain AI**: AI tools trained on public repositories can emit
  code that violates open-source licences or copyrights.
* **No Free-Tier Copilot**: The free tier of GitHub Copilot does not provide IPR
  indemnity or legal protection for generated code. Its use is *strictly
  prohibited* for any contributions to our simulation systems.
* **Contributor Liability**: Under all circumstances, individual *contributors bear
  full legal and professional responsibility* for the integrity of the code they
  generate and submit.
* **Met Office Staff**: Met Office contributors are only authorised to use the
  officially provided *Met Office GitHub Copilot Enterprise* model, which
  includes appropriate corporate guardrails and indemnities.
* **External Contributors**: External partners must operate under their own
  institution's approved AI policies. If no corporate, indemnified AI tool is
  available to you, you must write code manually.

Attribution Requirements
------------------------

If an authorised Generative AI tool is used to assist in writing or refactoring
code, you must provide clear attribution in two places:

#. **the source file header**

   A comment immediately before the module level docstring, for example,

   .. code-block:: fortran

      ! Some of the content of this file has been produced with the assistance of
      ! Met Office GitHub Copilot Enterprise (Claude Sonnet 4.6).

   External collaborators should replace Met Office GitHub Copilot Enterprise
   (Claude Sonnet 4.6) with their own institution's approved Generative AI tool,
   e.g., University of XYZ GitHub Copilot Enterprise (GPT-5.3-Codex), etc.

#. **the commit message**

   Your git commit message must explicitly state which tool was used and what it generated, for example,

   .. code-block:: text

      Refactor spatial interpolation routines to improve performance.

      - Co-authored-by: Met Office GitHub Copilot Enterprise (Claude Sonnet 4.6)
      - Assisted by: Met Office GitHub Copilot Enterprise (Claude Sonnet 4.6)
        for spatial interpolation optimisation.

Code Review Guidelines
----------------------

Reviewers must remember that AI-generated code is not self-authenticating.
The human contributor remains fully responsible for its contents.

Reviewer Checklist Matrix
^^^^^^^^^^^^^^^^^^^^^^^^^

+------+--------------------+------------------------------+------------------------+
| Step | Action             | Pass Criteria                | Fail Action            |
+======+====================+==============================+========================+
| 1    | Check file header  | Explicitly names an approved | Reject immediately if  |
|      | and commit message | enterprise-tier tool         | free/personal tier     |
+------+--------------------+------------------------------+------------------------+
| 2    | Check licence      | Code contains no proprietary | Request rewrite/proof  |
|      | compatibility      | or restrictively licensed    | of origin if           |
|      |                    | snippets                     | copy-paste suspected   |
+------+--------------------+------------------------------+------------------------+
| 3    | Assess Logic and   | Reviewer understands every   | Request revisions for  |
|      | Edge Cases         | line; edge cases are handled | "black box" code       |
+------+--------------------+------------------------------+------------------------+
| 4    | Run Test Suite     | Code passes all unit,        | Block merge until      |
|      |                    | integration, and             | tests pass natively    |
|      |                    | regression tests             |                        |
+------+--------------------+------------------------------+------------------------+
