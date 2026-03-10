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

  **Device Name:** EastRegion1-bigip-01

  **VIP:** /Common/web_app_42

  **Policy:** /Common/my_afm_policy (Java/Struts signatures enabled)

  **Application URL:** /upload.action

Tasks
~~~~~

  Navigate to:

    **udf.f5.com GUI >> Deployment >> F5 Insight >> ACCESS >> WEB SHELL**

  Send the following Struts-style test request:

  .. code-block:: bash

      curl -k -v \
        "https://ast66.demo.f5/upload.action" \
        -H 'Content-Type: ${(#_="multipart/form-data").(#context["com.opensymphony.xwork2.dispatcher.HttpServletResponse"].addHeader("X-Struts-POC","1"))}' \
        --data-binary 'test'

  Review the information returned from that request:
    - IP address of FQDN "ast66.demo.f5" (Can be found near the top of output)
    - Response code of 200
    - Response html that says "Request Rejected"
    - Support ID in response (Can be found in the html of the response)

  Use the AI Assistant and enter the following prompt:

    ``Have there been any WAF related events from 10.1.1.4 on EastRegion-bigip-01 over the last 14 days?``

  Review the returned information.

Deliverables
~~~~~~~~~~~~
  
  Briefly answer the following:
  
    - Provide the "Incident Type" and number of "Requests Blocked"

  Review the following for additional information and trends:

  - Summary of WAF-related events for that source IP
  - Key findings summary provided by the AI agent


Hints
~~~~~

  - Review the table provided by the AI assistant


This concludes Ticket 13.


Go to `Ticket 14 - Identify Busiest Client IP from WAF Events <../lab14/lab14.html>`_

Go to `Overview <../overview.html>`_