Ticket 15 - Upload and Validate TMOS Software Images
======================================================


Title: “How do I upload and validate TMOS software images in F5 Insight for later distribution?”
-----------------------------------------------------------------------------------------------


Ticket Description
~~~~~~~~~~~~~~~~~~



  The operations team wants to centralize BIG-IP TMOS images in F5 Insight so that future
  software distribution and installation jobs can pull from a single, validated image store.

  Instead of uploading images directly to individual BIG-IP devices, you will use F5 Insight’s
  Software image management to upload base TMOS `.iso` files.

  Your task is to locate the Software Images screen, upload one or more images with their
  validation files, and confirm that F5 Insight has successfully validated and stored them.

Context
~~~~~~~

Feature: Software Image Management

Platform: F5 Insight v1.2 or later

Software type: TMOS .iso images for BIG-IP

Validation files required: .md5, .pem, and .sig for each .iso image


Tasks
~~~~~



  Navigate to the Software Images view:

  - Go to the **Manage** section in the left toolbar.
  - Select **Software**.
  - Select **Images**.

  Upload software images and validation files:

  - Select **Upload** to open the upload drawer.
  - Select **Upload File** to open the file selection dialog on your jump host.
  - Choose at least one TMOS `.iso` image and its three validation files:
    - `<image>.iso`
    - `<image>.md5`
    - `<image>.pem`
    - `<image>.sig`
  - Confirm the selection so that F5 Insight begins uploading all selected files in the background.

  Observe background upload behavior:

  - While uploads are in progress, leave the upload drawer and navigate to another page.
  - Note the **upload in progress** banner that appears at the top of the UI.
  - Select the banner to return to the upload details and verify per-file progress.

  Validate that images are accepted:

  - After the upload completes, confirm that the `.iso` image now appears in the **Images** table.
  - Verify that the status or validation indicator shows that the image and its validation files
    have passed authenticity and integrity checks.
  - If an image is rejected, note any error message related to missing or invalid `.md5`, `.pem`,
    or `.sig` files.

Deliverables
~~~~~~~~~~~~

Briefly answer the following:

- Which TMOS software image(s) did you successfully upload (file name and version)?
- Did F5 Insight report successful validation for the uploaded image(s)?
- What happens in the UI when you leave the upload drawer while uploads are still in progress?
- How does F5 Insight behave when you cancel a single file within a multi-file upload?

Review the following for additional observations:

- How many files can you upload in a single operation (as indicated in the UI or docs)?
- What validation files are required before an image can be distributed or installed?

Hints
~~~~~

  - Remember that **all three validation files** (`.md5`, `.pem`, `.sig`) must be uploaded
    alongside each `.iso` image for validation to succeed.
  - If an image does not appear as **validated**, double-check that the validation file names
    match the image name and that you selected all required files together.
  - You can upload multiple images and their validation files at once; F5 Insight queues them
    and uploads them in the background.
  - If you are unsure whether an upload is still in progress, look for the upload banner at the
    top of the UI and select it to view details.
  - Use the **Delete** action on the Images table if you need to remove a test image from the
    centralized image store; this does not remove software already installed on BIG-IP devices.

This concludes Ticket 15 – Upload and Validate TMOS Software Images in F5 Insight.

Thank you for taking our lab!


Go to `Overview <../overview.html>`_
