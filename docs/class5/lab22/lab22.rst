Ticket 22 – Determine Last Application Outage
=============================================

Title: “When was the last outage for this new web server?”
-----------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  The team is evaluating a newer version of the web server
  running on node 10.1.20.201. This node is a member of the
  web_servers_pool pool on WestRegion-bigip-01.

  Before moving forward with broader deployment, the team
  wants to understand the stability of this node.

  How long has it been since this application experienced an outage?

Context
~~~~~~~

  Device Name: WestRegion-bigip-01

  Pool Name: web_servers_pool

  Pool Member: 10.1.20.201:80

Tasks
~~~~~

  Navigate to:

    BIG-IP Device >> Device Pools

  From the Device dropdown, select:

    WestRegion-bigip-01

  From the Pool dropdown, select:

    web_servers_pool

  Locate the panel:

    Pool Member State – isAvailable

  Use the Time Range dropdown in the upper-right corner of the dashboard
  to review historical availability data.

  Try adjusting the range to broader views such as:

  - Last 7 Days
  - Last 30 Days
  - Last 90 Days

  Expand the time range until you can clearly identify the most recent outage.

  Identify:

  - The most recent time the pool member 10.1.20.201:80 was not available
  - The duration of the outage (if visible)
  - How long it has been since that outage occurred


Deliverables
~~~~~~~~~~~~

  A brief summary including:

  - Date and time of the last outage
  - Approximate duration of the outage
  - Time elapsed since the outage
  - Any observations about stability trends

Hints
~~~~~

  - Try expanding the time range (Last 24 Hours, 7 Days, 30 Days).
  - Look for state transitions from isAvailable to unavailable.
  - Zoom in on the graph if necessary to see shorter outages.

This concludes Ticket 22.

---

Go to `Ticket 23 - Review Connection Count Standard Deviation (VS) <../lab23/lab23.html>`_

Go to `Overview <../overview.html>`_