===================================================================
Lab 2: Software Distribution Jobs - Staging Images to Fleet Instances
===================================================================

Overview
========

In this lab, you will create and execute a **Software Distribution Job** in F5 Insight. Software distribution jobs copy software images from the F5 Insight repository onto target BIG-IP instances prior to an active maintenance window. Staging large ISO files ahead of time significantly reduces maintenance window duration and risk.

Objectives
==========

* Create a new Software Distribution Job in F5 Insight.
* Target specific fleet instances and select software images.
* Perform pre-distribution disk space validation checks.
* Configure execution parameters (Serial vs. Parallel Batch execution).
* Execute the job with Change Request tracking and monitor progress.

Prerequisites
=============

* Completion of **Lab 1: Software Image Management**.
* Valid TMOS ISO image (``BIGIP-17.1.1-0.0.6.iso``) uploaded to F5 Insight.
* Managed target instances (``bigip-01.lab.local`` and ``bigip-02.lab.local``) registered and online.

Task 1: Creating a Software Distribution Job
==============================================

1. Log into the **F5 Insight** console.
2. Navigate to **Manage** > **Automation** > **Jobs**.
3. Click **Add Job** in the top action bar.
4. From the job type selector, select **Software Distribution**.

Task 2: Configuring Job Parameters and Target Selection
========================================================

1. In the **Job Name** field, enter a descriptive name:

   .. code-block:: text

      Stage_TMOS_17.1.1_Prod_Fleet

2. In the **Description** field (optional), enter:

   .. code-block:: text

      Pre-staging TMOS 17.1.1 ISO to production standalone BIG-IP instances prior to maintenance window.

3. Under **Select Instances**, search for and select your target instances:
   * Select ``bigip-01.lab.local``
   * Select ``bigip-02.lab.local``
4. Under **Select Images**, check the box for ``BIGIP-17.1.1-0.0.6.iso``.

Task 3: Performing Pre-Distribution Space Checks
=================================================

F5 Insight automatically evaluates disk space on target instances before transferring large installation files.

1. Click **Check Instances**.
2. Observe the disk space evaluation results table:
   * Instances with sufficient disk space in ``/shared/images/`` are marked as **Ready**.
   * Instances with insufficient disk space display an alert indicating the required vs. available storage.
3. If an instance indicates low disk space, clean up old images on the target BIG-IP or select **Re-check Instances** after freeing space.

Task 4: Configuring Distribution Execution Parameters
=====================================================

Choose between **Serial** or **Parallel** distribution depending on network bandwidth and target volume:

1. Under **Execution Type**, review the available options:
   * **Serial (Rolling Execution)**: Transfers software to one BIG-IP instance at a time.
   * **Parallel (Batch Execution)**: Transfers software to multiple instances concurrently.
2. Select **Parallel (Batch Execution)**.
3. Set the **Batch Size** to ``2`` (allowing both test instances to receive the image simultaneously).

.. note::
   F5 Insight scale limits support up to 100 instances per distribution job, with a maximum parallel batch size of 20 instances.

Task 5: Executing and Monitoring the Distribution Job
=====================================================

1. To run the distribution immediately, click **Execute Job**.
2. In the confirmation modal:
   * Enter a **Change Request #** (e.g., ``CR-98421-TMOS``) for audit compliance.
   * Click **Execute Job**.
3. To monitor job progress:
   * Locate the job in the **Jobs** list under **Manage > Automation > Jobs**.
   * Click on the value in the **Executing** or **Executions** column.
   * Review per-instance transfer status, transfer speed, and completion progress.

Troubleshooting Tip
===================

For detailed distribution transfer logs, SSH to the F5 Insight host CLI and inspect:

.. code-block:: bash

   tail -f /opt/f5insight/logs/provisioning.log

Verification Checkpoint
=======================

* Verify the distribution job status updates to **Completed**.
* Log into ``bigip-01.lab.local`` TMOS CLI or Web utility and confirm ``BIGIP-17.1.1-0.0.6.iso`` is present in the software image list.


Go to `Ticket 03 - Determine Last Application Outage <../lab03/lab03.html>`_

Go to `Overview <../overview.html>`_
