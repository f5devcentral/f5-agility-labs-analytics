Ticket 9 – WAF false positives on file uploads
==============================================

Investigate enrollment upload blocking in WAF
---------------------------------------------

The enrollment application on Eastregion-bigip-01 is seeing repeated
WAF alerts and blocked requests in the logs. A script is automatically
running and generating uploads to the application, and the security
team has noticed frequent "Attack signature detected" violations
associated with these uploads.

You have been asked to investigate why these enrollment uploads are
being blocked by the WAF and determine whether they represent real
attacks or false positives.

Review application and WAF behavior
-----------------------------------

App behavior
^^^^^^^^^^^^

- Application URL: ``POST /enrollment/upload``
- Host: ``asmupload.demo.f5:8888``
- Form field: ``attachment`` (multipart/form-data file field)
- Users upload txt files containing enrollment data (names, addresses).
- These files are expected to be treated as arbitrary documents by the
  application.

Review WAF events
-----------------

Use the AI Assistant and enter the prompt:

``Show recent ASM/AWAF events for POST /enrollment/upload on the EastRegion-bigip-01, including violations and parameters involved.``

From the returned information and the ASM/AWAF logs in TMUI:

- Locate one or more blocked requests for ``POST /enrollment/upload``.
- Identify:

  - Which parameter is flagged (for example, ``attachment`` or a body parameter).
  - Which attack signatures are triggered (SQL injection, XSS, or others).
  - The violation contexts (for example, request/body).

Review the security policy configuration
----------------------------------------

Open the security policy for this application and check:

- How the ``attachment`` parameter is defined (if at all) under **Parameters**.
- Whether ``attachment`` is configured as:

  - A simple parameter (with attack signatures enabled), or
  - A File Upload parameter with different handling.

- Whether attack signatures and metacharacter checks are enabled on this parameter.

Perform the following steps:

1. In the BIG-IP UI, navigate to:

   **Security > Application Security > Parameters > Parameters List**

2. Locate the parameter named ``attachment``:

   - If it is not present, note that it is currently being treated
     implicitly and not explicitly defined in the policy.

3. If ``attachment`` exists, click on it to open its settings and verify:

   - The **Parameter Type** (for example, *Explicit*, *Wildcard*).
   - The **Data Type** (for example, *Alpha-Numeric*, *Binary*, etc.).
   - Whether **Check attack signatures** is enabled.
   - Whether **Check for mandatory** or other value checks are configured.

4. Check whether ``attachment`` is configured as a **File Upload** parameter:

   - In the parameter settings, look for options that indicate file-upload
     handling (for example, *File types*, *Maximum file size*).
   - If it is not configured as a File Upload parameter, note that ASM is
     likely inspecting the raw content as normal parameter data.

5. Confirm whether any attack signatures or metacharacter checks are
   specifically disabled or enabled for ``attachment``:

   - Review the **Attack Signatures** section within the parameter settings.
   - Note any per-parameter signature overrides or staging settings that
     affect how this parameter is inspected.

Deliverables
------------

Provide a brief summary describing:

- Which parameter and signatures are causing the uploads to be blocked.
- Why these detections are considered false positives in the context of the
  enrollment upload use case.
- The specific policy change(s) you recommend to reduce these false positives
  while maintaining appropriate security for the application.

Hints
-----

- Look carefully at the parameter type for ``attachment`` and whether it is
  treated as a normal parameter or as a File Upload parameter.
- If ASM sees example SQL or XSS strings inside a document and treats them as
  live input, it will naturally trigger attack signatures, even when the app
  only stores or forwards the file.
- Distinguishing between "data that will be executed" and "data that is just
  stored in a file" is critical when tuning WAF policies for upload endpoints.

WAF behavior
^^^^^^^^^^^^

- The parameter ``attachment`` is not explicitly configured as a File
  Upload parameter in the ASM/AWAF policy.
- ASM treats the body as generic parameter data and runs full attack
  signature and metacharacter checks on the raw file content.
- Resulting violations include:

  - Attack signature detected (context: request/body).
  - Possibly "Illegal metacharacter in value".
- Requests are blocked, even though the uploaded file content is benign
  and only contains test strings.

Propose one or more safe mitigation strategies for this lab scenario, such as:

- Configuring ``attachment`` as a File Upload parameter and disabling attack
  signatures on its raw content while still enforcing size and type limitations.
- Narrowing the scope of attack signatures to exclude file-upload bodies for
  this specific URL/parameter.
- Using additional security controls (for example, out-of-band malware scanning)
  instead of relying on inline WAF signatures for file content.
----

Go to `Exercise 10 - One pool member is overloaded <../lab10/lab10.html>`_

Go to `Overview <../overview.html>`_