Ticket 13 – WAF Blocking a Known Apache Struts-Like Probe
==========================================================

Title: “Security test shows WAF blocks Struts exploit attempt”
---------------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

The security team wants confirmation that the WAF is capable
of detecting Apache Struts exploit attempts.

You have been asked to run a safe test request and demonstrate
that the WAF properly detects and blocks the attack.


Context
~~~~~~~

**VIP:** /Common/sslo.demo.f5

**Policy:** /Common/my_sslo_app_waf_policy (Java/Struts signatures enabled)

**Application URL:** /upload.action


Tasks
~~~~~

Navigate to:

  **udf.f5.com GUI >> Deployment >> F5 Insight >> ACCESS >> WEB SHELL**

Send the following Struts-style test request:

.. code-block:: bash

    curl -k -v \
      "https://sslo.demo.f5/upload.action" \
      -H 'Content-Type: ${(#_="multipart/form-data").(#context["com.opensymphony.xwork2.dispatcher.HttpServletResponse"].addHeader("X-Struts-POC","1"))}' \
      --data-binary 'test'

Gather and record the following information from that request:
  - IP address of FQDN "sslo.demo.f5" (Can be found near the top of output)
  - Support ID in response (Can be found in the html of the response)

Verify that the request is blocked and logged by ASM/AWAF
as a Java/Struts/OGNL RCE attempt.  In the WAF event logs, identify:

  - The attack signature ID
  - The attack type
  - The severity
  - Whether the request was blocked


Deliverables
~~~~~~~~~~~~
  
  Briefly answer the following:
  
    - Provide the source IP address found in the WAF event

  Review the following for additional information and trends:

  - Screenshot of the specific WAF request log entry
    (showing attack signature, severity, and blocking status).
  - Prepare a short explanation suitable for a non-F5 security audience describing what occurred.


Hints
~~~~~

- Security BIG-IP
- Filter events by URL ``/upload.action`` and your test client IP.
- Review the “Attack Type” field in the event details.
- Confirm that the policy pol_java_asm has relevant
  Java/Struts signatures enabled.


This concludes Ticket 13.


Go to `Ticket 14 - Identify Busiest Client IP from WAF Events <../lab14/lab14.html>`_

Go to `Overview <../overview.html>`_