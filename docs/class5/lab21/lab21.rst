Ticket 21 – Analyze Traffic Patterns for an Application
========================================================

Title: “When is our application experiencing peak traffic?”
------------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  The application owner for primary-app-site-1 has requested
  insight into traffic patterns for their HTTPS virtual server.
  They would like to understand when traffic volume is highest
  in order to plan scaling and maintenance windows.

Context
~~~~~~~

  Device Name: CentralRegion-bigip-01

  Virtual Server Name: primary-app-site-1-https-vip

  Protocol: HTTPS (TCP 443)

Tasks
~~~~~

  Determine what times of day and days of the week show the most
  traffic for the virtual server primary-app-site-1-https-vip
  on CentralRegion-bigip-01.

  Navigate to:

  BIG-IP Fleet >> Virtual Servers >> 

  From the virtual server dropdown, select:

    primary-app-site-1-https-vip

  Review the following panels:

  - VS Data Rate
  - VS Connection Rate

  Analyze connection and throughput patterns over time
  to determine peak usage periods.

  After reviewing the data, answer the following:

  - What are the peak hours of the day?
  - What are the peak days of the week?
  - Are the traffic patterns consistent or highly variable?

Deliverables
~~~~~~~~~~~~

  A brief summary describing the traffic trends:

  - Peak time(s) of day
  - Peak day(s) of week
  - Observed traffic behavior (weekday spikes, weekend drops, steady patterns, etc.)
  - Recommended maintenance window based on traffic analysis

Hints
~~~~~

  Pay close attention to:

  - Request rate trends
  - Throughput (bps)
  - Connection counts
  - Historical time-based views

This concludes Ticket 21.

---

Go to `Ticket 22 - TBD22 <../lab22/lab22.html>`_

Go to `Overview <../overview.html>`_
