Ticket 20 – Verify Application configuration consistency across BIG-IPs
=======================================================================

Title: “Why is my application not performing the same across regions?”
----------------------------------------------------------------------

Ticket description
~~~~~~~~~~~~~~~~~~

  An application owner for the App, web-app-foo, has observed
  inconsistent behavior with his application across all devices.
  They would like the configuration reviewed for any anomolies. 

Context
~~~~~~~

  Device Names: EastRegion-bigip-01, WestRegion-bigip-01

  Virtual Server name: web-app-foo

  App Servers and ports:
    - 10.1.20.100:80
    - 10.1.20.101:80
    - 10.1.20.102:80
    - 10.1.20.201:80
    - 10.1.20.202:80

Tasks
~~~~~

    Use the AI Assistant and enter the prompt:
    "Can you check the virtual servers with the name "web-app-foo" and associated objects across all BIG-IPs to verify the configuration is the same?"

    Review the information returned, do you see any differences?  What did the AI agent tell you?

Deliverables
~~~~~~~~~~~~

    A brief summary describing the issue found:

    - A list of discrepencies found for web-app-foo

Hints
~~~~~

    Pay specific attention to the pool members configured on each device

This concludes Ticket 20.

---

Go to `Ticket 21 - TBD21 <../lab21/lab21.html>`_

Go to `Overview <../overview.html>`_