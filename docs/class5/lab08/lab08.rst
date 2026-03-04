Ticket 08 – Identifying HTTP Versions in Use
============================================

Title: “What HTTP version is this app really using?”
----------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  Operations wants to better understand the HTTP versions in use
  across the environment. They suspect that the Backup_app service
  is still using HTTP/1.0, which might impact connection behavior
  and troubleshooting.

  You have been asked to confirm what HTTP version is actually being
  used between clients and BIG-IP, and between BIG-IP and the pool
  members.


Context
~~~~~~~

  **Device Name:** CentralRegion-bigip-01

  **Virtual Server:** Backup_app

  **Pool:** app-1

  **Expectation:** Most of the lab environment is using HTTP/1.0,
  but this needs to be verified rather than assumed.


Tasks
~~~~~

  Use the AI Assistant and enter the following prompt:

    ``Show configuration details for the Backup_app virtual server on CentralRegion-bigip-01, including attached profiles.``

  From the returned information and the TMUI on **CentralRegion-bigip-01:**

    - Identify which HTTP profile is attached to the Backup_app
      virtual server (if any).
    - Note any HTTP profile settings that influence protocol versions
      (for example, HTTP/1.0 vs HTTP/1.1 behavior, keep-alive settings).

  In Insight, review any available HTTP-related metrics or attributes
  for Backup_app and its pool app-1 that indicate HTTP protocol behavior
  (for example, headers, connection reuse, or profile details).  This can be done by going to: **Dashboards >> BIG-IP Device >> LTM-Profile** and select the **EastRegion-bigip-01** and **/common/http**

  Using the charts on that page summarize whether *Backup_app* is effectively using HTTP/1.0 or a newer
  version on the client side, and whether server-side connections to the
  app-1 pool members behave differently.


Deliverables
~~~~~~~~~~~~

  Briefly answer the following:
  
    - Your conclusion about the HTTP version behavior from the client
      to the Backup_app virtual server.

  Review the following for additional information and trends:

    - The HTTP profile attached to Backup_app.
    - Your conclusion about the HTTP version behavior from the client
      to the Backup_app virtual server.
    - Any observations about server-side HTTP behavior to the app-1
      pool members, is the application traffic healthy?


Hints
~~~~~

- Look at which HTTP profile is attached and whether it is a custom profile or the default http profile.

- Use the charts, Luke!

- Virtual Server HTTP Response Rate By Status

This concludes Ticket 08.

Go to `Ticket 09 - Investigating APM Session Activity Across Devices <../lab09/lab09.html>`_

Go to `Overview <../overview.html>`_