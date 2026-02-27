Ticket 20 – Verify Application Configuration Consistency Across BIG-IPs
========================================================================

Title: “Why Is My Application Not Performing the Same Across Regions?”
----------------------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  An application owner for the app, web-app-foo, has observed
  inconsistent behavior across devices.
  They would like the configuration reviewed for any anomalies.

Context
~~~~~~~

  Device Names: EastRegion-bigip-01, WestRegion-bigip-01

  Virtual Server Name: web-app-foo

  App Servers and Ports:

  * 10.1.20.100:80
  * 10.1.20.101:80
  * 10.1.20.102:80
  * 10.1.20.201:80
  * 10.1.20.202:80

Tasks
~~~~~

  Use the AI Assistant and enter the prompt:

  "Can you check the virtual servers named 'web-app-foo' and their associated objects across all BIG-IPs to verify that the configuration is the same?"

  Review the information returned. Do you see any differences?
  What did the AI agent tell you?

Deliverables
~~~~~~~~~~~~

  A brief summary describing the issue found:

  - A list of discrepancies found for web-app-foo

Hints
~~~~~

  Pay specific attention to the pool members configured on each device.

This concludes Ticket 20.

---

Go to `Ticket 21 - TBD21 <../lab21/lab21.html>`_

Go to `Overview <../overview.html>`_
