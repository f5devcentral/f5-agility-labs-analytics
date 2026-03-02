Ticket 13 – WAF Blocking a Known Apache Struts-Like Probe
==========================================================

Title: “Security test shows WAF blocks Struts exploit attempt”
---------------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  The security team wants confirmation that the WAF is capable
  of detecting Apache Struts / OGNL-based exploit attempts.

  You have been asked to run a safe test request and demonstrate
  that the WAF properly detects and blocks the attack.


Context
~~~~~~~

  VIP: /Common/sslo.demo.f5

  Policy: /Common/pol_java_asm (Java/Struts signatures enabled)

  Application URL: /upload.action


Tasks
~~~~~

  From the jumphost (or using the provided lab script), send
  the following Struts-style test request:

  .. code-block:: bash

      curl -k -v \
        "https://sslo.demo.f5/upload.action" \
        -H 'Content-Type: ${(#_="multipart/form-data").(#context["com.opensymphony.xwork2.dispatcher.HttpServletResponse"].addHeader("X-Struts-POC","1"))}' \
        --data-binary 'test'

  Verify that the request is blocked and logged by ASM/AWAF
  as a Java/Struts/OGNL RCE attempt.

  In the WAF event logs, identify:

  - The attack signature ID
  - The attack type
  - The severity
  - Whether the request was blocked

  Prepare a short explanation suitable for a non-F5
  security audience describing what occurred.


Deliverables
~~~~~~~~~~~~

  - Screenshot of the specific WAF request log entry
    (showing attack signature, severity, and blocking status).
  - Short explanation of what type of attack was detected
    and how the WAF mitigated it.


Hints
~~~~~

  - Filter events by URL /upload.action and your test client IP.
  - Review the “Attack Type” field in the event details.
  - Confirm that the policy pol_java_asm has relevant
    Java/Struts signatures enabled.


This concludes Ticket 04.

---

Go to `Ticket 14 - Identify Busiest Client IP from WAF Events <../lab14/lab14.html>`_

Go to `Overview <../overview.html>`_