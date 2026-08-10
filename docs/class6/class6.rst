========================================================================
Insight Fleet Mgmt Lab: Software Upgrades, Updates, and Patching
========================================================================

Welcome to the **Insight Fleet Mgmt Lab**. This lab series guides you through the end-to-end workflow for managing, distributing, and installing TMOS software upgrades across an enterprise fleet of BIG-IP instances using F5 Insight.

Lab Overview
============

Software installations (upgrades, updates, and patching) in F5 Insight follow a streamlined three-step operational workflow designed to minimize downtime during change windows:
1. **Upload & Validate**: Upload software images and cryptographic validation files (`.pem`, `.sig`) into the centralized F5 Insight image store.
2. **Distribute**: Stage software images onto target fleet instances prior to the maintenance window.
3. **Install & Activate**: Execute orchestrated software installation jobs across High Availability (HA) pairs or Standalone fleet instances.

Expected Completion Time: **1 Hour**

.. toctree::
   :maxdepth: 2
   :caption: Walkthrough Labs:

   overview
   introduction
   lab1
   lab2
   lab3