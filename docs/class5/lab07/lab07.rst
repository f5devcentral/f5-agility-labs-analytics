Ticket 07 – Verify Application Configuration Consistency Across BIG-IPs
========================================================================

Title: “Why Is My Application Not Performing the Same Across Regions?”
----------------------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

An application owner for the app, *web-app-foo*, has observed inconsistent behavior across devices.

They would like the configuration reviewed for any anomalies.

Context
~~~~~~~

**Device Names:** EastRegion-bigip-01, WestRegion-bigip-01

**Virtual Server Name:** web-app-foo

App Servers and Ports:
    * 10.1.20.100:80
    * 10.1.20.101:80
    * 10.1.20.102:80
    * 10.1.20.201:80
    * 10.1.20.202:80

Tasks
~~~~~~~

Use the AI Assistant and enter the following prompt:

  ``Can you check the virtual servers named 'web-app-foo' and their associated objects across all BIG-IPs to verify that the configuration is the same?``

Review the information returned.  Do you see any configuration differences between *EastRegion-bigip-01* and *WestRegion-bigip-01*?

If differences are identified, validate them by navigating to: **Dashboard >> BIG-IP Device >> Device Virtual Server and Dashboard >> BIG-IP Device >> Device Pools**

Compare the configuration of *web-app-foo* on each device:

  Identify and explain the configuration differences that could impact application behavior.

Deliverables
~~~~~~~~~~~~

A brief summary describing the issue found:

  - A list of discrepancies found for *web-app-foo*
  - An explanation of how each discrepancy could impact behavior

Hints
~~~~~

- Pay specific attention to the pool members configured on each device.

This concludes Ticket 7.


Go to `Ticket 08 - Identifying HTTP Versions in Use <../lab08/lab08.html>`_

Go to `Overview <../overview.html>`_
