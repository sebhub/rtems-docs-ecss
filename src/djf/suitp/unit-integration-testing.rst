.. SPDX-License-Identifier: CC-BY-SA-4.0

.. Copyright (C) 2021 embedded brains GmbH & Co. KG

.. include:: ../include/abbreviations.rst

.. _UnitIntegrationTesting:

Software unit testing and software integration testing
******************************************************

Organization
============

The strategy performed was to identify tests at TS level, that due to the
modularity of the software could be used to cover for some unit testing.
Unit and integration testing will be done only if code coverage cannot be
achieved through validation tests.  In some rare cases it is practically
infeasible to tailor individual RTEMS source files so that they only contain
code for the pre-qualified feature set.  In this case unit and integration
tests will be added to achieve the code coverage goal.

Master schedule
===============

There is no master schedule.  Unit and integration tests will be done on demand
and ad hoc.

Resource summary
================

Unit and integration testing will be done by the software engineers working for
the project.  The time of unit and integration testing is included in the
normal engineering hours.

Responsibilities
================

The software engineers working for the project are responsible for the unit and
integration testing.

Tools, techniques, and methods
==============================

The unit and integration test plan and implementation is done using
specification times and the qualification tools.

Personnel and personnel training requirements
=============================================

Software engineers which fulfill the overall project training requirements are
required to do the unit and integration testing.

Risks and contingencies
=======================

The general lack of unit and integration tests may result in undiscovered bugs
and could reduce the development productivity.  However, RTEMS is a mature
piece of software spanning a development time frame of over 30 years.  The
thorough validation tests compensate the lack of unit and integration tests.
