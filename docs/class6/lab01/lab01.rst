==============================================================
Lab 1: Software Image Management - Uploading and Validating
==============================================================

Overview
========

In this lab, you will walk through managing software images within F5 Insight. Centralized software image management allows administrators to store, validate, and organize TMOS installation files before distributing them to BIG-IP devices across the fleet.

Objectives
==========

* Access the Software Image Management repository in F5 Insight.
* Upload a base TMOS software image (``.iso``) alongside its required validation files (``.pem`` and ``.sig``).
* Monitor background upload progress and verify image integrity.
* Understand scale limits and bulk image management practices.

Prerequisites
=============

* Local access to downloaded TMOS software files:
  * ``BIGIP-17.1.1-0.0.6.iso``
  * ``BIGIP-17.1.1-0.0.6.iso.pem``
  * ``BIGIP-17.1.1-0.0.6.iso.sig``

Task 1: Accessing the Software Image Store
===========================================

1. Open a web browser and log into the **F5 Insight** management console.
2. In the left-hand navigation menu, expand **Manage**.
3. Select **Software**.
4. Select **Images**.

.. note::
   The **Software Images** table displays all previously uploaded TMOS software packages, file sizes, upload timestamps, and signature validation statuses.

Task 2: Uploading TMOS Software Images and Validation Files
============================================================

To ensure software images are authentic and uncorrupted, F5 Insight validates each ``.iso`` image against its accompanying public certificate (``.pem``) and cryptographic signature (``.sig``).

1. On the upper-right corner of the **Software Images** page, click **Upload**. The upload drawer will expand from the right.
2. Click **Upload File** to open your local system's file picker.
3. Select all three required files simultaneously:
   * ``BIGIP-17.1.1-0.0.6.iso``
   * ``BIGIP-17.1.1-0.0.6.iso.pem``
   * ``BIGIP-17.1.1-0.0.6.iso.sig``
4. Click **Open** (or **Confirm**) to initiate the upload process.

.. important::
   Both validation files (``.pem`` certificate and ``.sig`` signature) must be uploaded alongside the ``.iso`` image. F5 Insight uses these files to verify image authenticity according to F5 security guidelines (K24341140).

Task 3: Monitoring Background Uploads
======================================

F5 Insight supports background file transfers, enabling administrators to navigate to other UI sections without interrupting active uploads.

1. Once the upload starts, observe the per-file upload progress bars in the upload drawer.
2. Close the upload drawer by clicking outside or selecting the **X** icon.
3. Notice the blue notification banner appearing at the top of the screen:

   .. code-block:: text

      Upload in progress: 1 or more file uploads are currently active. Click here to view details.

4. Click the banner at any time to return to the upload drawer and review progress.
5. Once complete, verify that ``BIGIP-17.1.1-0.0.6.iso`` appears in the **Software Images** list with a status of **Ready**.

Task 4: Managing Stored Software Files
======================================

1. To view scale limits, note the following capacity thresholds for F5 Insight:
   * Maximum 10 GB total file size per upload operation.
   * Maximum 10 files per single upload session.
   * Total storage quota of 50 GB across all uploaded software packages in F5 Insight.
2. To remove outdated or unneeded images:
   * Select the checkbox next to the software file you wish to delete.
   * Click **Delete** on the right side of the action bar.
   * Confirm the deletion when prompted in the modal dialog.

.. note::
   Deleting a software image from F5 Insight removes it from the central F5 Insight store. It does **not** delete files already distributed to or installed on managed BIG-IP instances.

Verification Checkpoint
=======================

* Verify ``BIGIP-17.1.1-0.0.6.iso`` is listed under **Manage > Software > Images**.
* Confirm that the image status shows as **Validated / Ready**.



Go to `Ticket 02 - Analyze Traffic Patterns for an Application <../lab02/lab02.html>`_

Go to `Overview <../overview.html>`_