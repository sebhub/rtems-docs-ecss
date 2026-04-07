.. SPDX-License-Identifier: CC-BY-SA-4.0

.. Copyright (C) 2021 embedded brains GmbH & Co. KG

.. include:: ../include/abbreviations.rst

.. _Introduction:

Introduction
************

The Software Validation Specification (with respect to the Technical
Specification) is a part of the Design Justification File (DJF) as required by
ECSS-E-ST-40C ${/ref/ecss/e-st-40c:/cite} and ECSS-Q-ST-80C Rev.1
${/ref/ecss/q-st-80c-r1:/cite}.  The document is intended to be used by reviewers and
qualification authorities.  For users of the ${/glossary/qdp:/term} and
${/glossary/rtems:/term} it is recommended to get started by reading the
Software Configuration File ${/pkg/deployment/doc-package-manual:/cite}.  For using RTEMS in general,
please refer to the RTEMS User Manual ${/ref/rtems/user:/cite} and the RTEMS
Classic API Guide ${/ref/rtems/c-user:/cite}.

The specification of RTEMS is done using so called specification items.  For an
overview of the specification approach see the
`Software Requirements Engineering <${.:/component/deployment-directory}/doc/rtems/eng/req/index.html>`_
chapter in |RSE| manual ${/ref/rtems/eng:/cite}.  The test suites and test cases
presented in this document are specified using specification items.  The items
contain source code fragments which are used to generate source files for test
suites and test cases.
