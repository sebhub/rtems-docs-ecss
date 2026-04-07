.. SPDX-License-Identifier: CC-BY-SA-4.0

.. Copyright (C) 2021 embedded brains GmbH & Co. KG

.. include:: ../include/abbreviations.rst

.. _Introduction:

Introduction
************

The Software Requirements Specification together with the Interface Control
Document ${doc-ts-icd:/cite} forms the Technical Specification as required by
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
chapter in |RSE| manual ${/ref/rtems/eng:/cite}.  It is recommended to read this
chapter.  The constraints and requirements presented in the current document
are specified using specification items.

RTEMS is a reusable software component those main purpose is to provide an
Application Programming Interface (${/glossary/api:/term}) to real-time
operating system services.  The component should implement the API and nothing
more.  The interfaces of RTEMS are specified in the Interface Control Document
${doc-ts-icd:/cite}.  Most requirements of the SRS, the current document, specify
functions of the interfaces.  In general, the operating system services are not
active on their own.  The services are used event-driven by the application.
Exceptions are the clock interrupt and device drivers.  So, the vast majority
of functional requirements are a combination of state-driven and event-driven
requirements formulated in ${/glossary/ears:/term} notation.

One problem of EARS is that it may lead to a lot of atomic requirements.  This
problem is addressed by the RTEMS specification through a table-based approach.
The state-driven and event-driven requirements are specified in so called
action requirement specification items which contain pre-conditions, a trigger,
and post-conditions as the system response.  For example, the functional
requirements for :ref:`rtems_signal_send() <SpecRtemsSignalReqSend>` are
stated with five pre-conditions, the call to :c:func:`rtems_signal_send` as the
trigger, and three post-conditions as the system response.  This results in 48
atomic requirements.  Each of the atomic requirements is validated using code
embedded in the specification item.  An example of an atomic requirement for a
call to :c:func:`rtems_signal_send` is:

    While the ``id`` parameter is associated with the calling task,
    while the ``signal_set`` parameter is non-zero,
    while the target task has a valid ASR handler installed,
    while the target task has ASR processing enabled,
    while the target task processes an asynchronous signal,

    **when rtems_signal_send() is called**,

    the return status of :c:func:`rtems_signal_send` shall be
    ``RTEMS_SUCCESSUFL``,
    the ASR handler shall be called during the :c:func:`rtems_signal_send` call,
    the ASR handler shall be called recursively.
