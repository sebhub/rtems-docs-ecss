.. SPDX-License-Identifier: CC-BY-SA-4.0

.. Copyright (C) 2021, 2026 embedded brains GmbH & Co. KG

.. _SoftwareOverview:

Software overview
*****************

Function and purpose
====================

The Real-Time Executive for Multiprocessor Systems (${/glossary/rtems:/term})
is a multi-threaded, single address-space, real-time operating system with no
kernel-space/user-space separation.  RTEMS is a reusable software component.
Its purpose is to provide an ${/glossary/api:/term} to make services of an
real-time operating system available to application developers.  The
pre-qualified feature set of RTEMS provided by the ${/glossary/qdp:/term} is
only a subset of features provided by mainline RTEMS.

The pre-qualified feature set of RTEMS provided by the QDP is mostly limited to
services of the Classic API, see
${/ref/rtems/c-user:/cite-long}.  The programming languages ${/glossary/c11:/term}
and ${/glossary/cxx14:/term} are supported, however, not all functions of the
corresponding standard libraries are available.  In general, third-party
libraries are not covered by the pre-qualification activity.

The following features are provided by the pre-qualified RTEMS of the QDP:

- Thread synchronization and communication

    - Mutexes with and without locking protocols

    - Counting semaphores

    - Binary semaphores

    - Events

    - Message queues

    - Barriers

    - ${/glossary/futex:/term} (used by ${/glossary/openmp:/term} barriers)

- Locking protocols

    - Transitive Priority Inheritance

    - ${/glossary/omip:/term} (SMP feature)

    - Priority Ceiling

    - ${/glossary/mrsp:/term} (SMP feature)

- Scalable timer and timeout support

- Lock-free timestamps (FreeBSD timecounters)

- Responsive interrupt management

- C11/C++11 ${/glossary/tls:/term}

- Link-time configurable schedulers

    - Fixed-priority

    - Job-level fixed-priority (${/glossary/edf:/term})

- Clustered scheduling (SMP feature)

    - Flexible link-time configuration

    - Job-level fixed-priority scheduler (${/glossary/edf:/term}) with support
      for one-to-one and one-to-all thread to processor affinities (default SMP
      scheduler)

    - Fixed-priority scheduler

- Focus on link-time application-specific configuration

- Linker-set based initialization (similar to global C++ constructors)

- Operating system uses fine-grained locking (SMP feature)

- Thread pinning (SMP feature)

- Dynamic memory allocator

    - First-fit allocation, **no deallocation**

- Clock driver

- Serial input/output driver for test programs

- Application runs in kernel-space and can access hardware directly

Environmental considerations
============================

The execution environment is defined by the ${/glossary/target:/term} and the
boot loader which started the executable.  The executable consists of the
application and the RTEMS services used by the application.

Relation to other systems
=========================

In the Technical Specification the relation of RTEMS components to other
systems is defined by interfaces in interface domains.  The main interface
domain is the Application Programming Interface.  It contains all interfaces
which an application developer may use to access services provided by RTEMS.
Other interface domains are used by the API (implementation, devices, compiler
extensions) or alter the API (user-provided defines, build options).  RTEMS
implements interfaces specified externally, for example ${/glossary/c11:/term}
and ${/glossary/posix:/term}.  The interface domains are specified in the
Interface Control Document.

.. _Constraints:

Constraints
===========

The constraints in using RTEMS belong to roughly four categories:

* The application developer using RTEMS needs a host computer to run the
  software development tools.  It is recommended to do the software development
  on a modern Linux distribution.  For the details, see the
  ${/pkg/deployment/doc-package-manual:/cite-long}.

* The executable consisting of the application and the used RTEMS services must
  fit into the memory provided by the ${/glossary/target:/term} system, for
  example the GR712RC ${/ref/soc/gaisler/gr712rc/um-2-13:/cite} or the GR740
  ${/ref/soc/gaisler/gr740/um-ds-2-4:/cite}.  For an overview of the memory
  usage of RTEMS components, see the
  ${/pkg/deployment/doc-package-manual:/cite-long}.

* The runtime performance of the RTMES services used by the application must
  meet the application performance requirements.  For an overview of
  performance characteristics of RTEMS services, see the ${doc-djf-svr:/cite-long}.

* The application developer must meet the usage constraints of the API.

.. include:: ../include/constraints.rst
