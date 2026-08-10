.. _top:

===============
Getting Started
===============

Lab Environment Prerequisites
=============================

Before starting the software upgrade walkthrough labs, ensure you have access to the following lab components:

* **F5 Insight Management Console**: Version 1.2.1 or later.
* **Administrative Credentials**: Role permissions granting full software file and job orchestration privileges.
* **Target BIG-IP Instances**:
  * ``bigip-01.lab.local`` (Standalone / Active)
  * ``bigip-02.lab.local`` (Standalone / Standby)
  * ``ha-pair-01a.lab.local`` & ``ha-pair-01b.lab.local`` (Configured High Availability Pair)
* **Downloaded Software Packages**:
  * Base TMOS ISO image: ``BIGIP-17.1.1-0.0.6.iso``
  * Public Certificate: ``BIGIP-17.1.1-0.0.6.iso.pem``
  * Digital Signature: ``BIGIP-17.1.1-0.0.6.iso.sig``

Workflow Summary
================

.. list-table:: Software Upgrade Lifecycle Steps
   :widths: 10 30 60
   :header-rows: 1

   * - Step
     - Phase
     - Objective
   * - 1
     - Image Management
     - Centralize and validate ISO software images, signatures, and certificates in F5 Insight.
   * - 2
     - Software Distribution
     - Pre-stage ISO files onto managed BIG-IP target instances before maintenance windows.
   * - 3
     - Software Installation
     - Perform orchestrated rolling or parallel software upgrades with health checks and optional human-in-the-loop pauses.


Go to `Introduction <./introduction.html>`_

`Back to Top <top_>`_