============
Introduction
============

Welcome to **Insight Fleet Mgmt Lab**. This course provides an in-depth, hands-on walkthrough of managing software lifecycles across an enterprise fleet of BIG-IP instances using F5 Insight.

What is F5 Insight?
===================

**F5 Insight** is a centralized management, observability, and fleet orchestration platform designed to streamline Day 2 operations for BIG-IP deployments. F5 Insight provides real-time visibility into application performance, security telemetry, configuration consistency, and automated software maintenance across high-density enterprise environments.

Key Fleet Management Capabilities
=================================

* **Centralized Image Repository**: Store, organize, and cryptographically validate TMOS software packages (`.iso`), public certificates (`.pem`), and signatures (`.sig`).
* **Pre-Staged Image Distribution**: Stage large software images to managed BIG-IP instances prior to change windows, minimizing maintenance downtime.
* **Orchestrated Software Upgrades**: Execute zero-downtime upgrades across High Availability (HA) pairs and controlled rolling or batch upgrades across Standalone instances.
* **Space-Aware Disk Checks**: Automatically evaluate storage on target instances before file transfer to prevent mid-job space exhaustion.
* **Human-In-The-Loop (HITL) Controls**: Pause upgrade jobs at critical milestones (e.g., post-Standby upgrade or pre-failover) for administrative health verification.
* **Audit & Compliance Integration**: Attach Change Request tracking numbers (`CR-XXXXX`) to job executions for compliance logging.

Lab Architecture & Topology
===========================

During this lab, you will interact with an F5 Insight management node orchestrating upgrades across a representative enterprise fleet:

.. code-block:: text

   +---------------------------------------------------------------------------------+
   |                           F5 Insight Management Node                            |
   |                       (Software Store & Job Orchestration)                      |
   +---------------------------------------------------------------------------------+
                                         |
            +----------------------------+----------------------------+
            |                                                         |
   +-----------------------+                                 +-----------------------+
   |   HA Pair 01 Cluster  |                                 |   Standalone Fleet    |
   |                       |                                 |                       |
   | ha-pair-01a (Active)  |                                 |   bigip-01.lab.local  |
   | ha-pair-01b (Standby) |                                 |   bigip-02.lab.local  |
   +-----------------------+                                 +-----------------------+

Lab Objectives
==============

By completing this walkthrough, you will learn how to:

1. Upload and cryptographically validate TMOS images in F5 Insight (**Lab 1**).
2. Validate target disk space and pre-stage software images to fleet devices (**Lab 2**).
3. Execute automated, zero-downtime software installations across HA pairs and Standalone instances (**Lab 3**).


Go to `Ticket 1 <./lab01/lab01.html>`_
