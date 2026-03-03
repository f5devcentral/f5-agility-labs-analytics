Ticket 02 – Analyze Traffic Patterns for an Application
========================================================

Title: “When is our application experiencing peak traffic?”
------------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  The application owner for *primary-app-site-1* has requested
  insight into traffic patterns for their HTTPS virtual server.
  They would like to understand when traffic volume is highest
  in order to plan scaling and maintenance windows.

Context
~~~~~~~

**Device Name:** CentralRegion-bigip-01

**Virtual Server Name:** primary-app-site-1-https-vip

**Protocol:** HTTPS (TCP 443)

Tasks
~~~~~

Determine which times of day and which days of the week
show the highest traffic for the virtual server
primary-app-site-1-https-vip on CentralRegion-bigip-01.1.

Navigate to:

  **Dashboards >> BIG-IP Fleet >> Virtual Servers**

.. image:: ./images/image4.png
    :width: 500px
    :alt: Fleet Dashboard navigation

From "Data Center" leave the default value as:
  
  **default**

From "Devices" leave the default value as:

  **bigip/CentralRegion-bigip-01**

From the "Virtual Server" dropdown, verify only below is selected:

  **primary-app-site-1-https-vip**

Click the *"Apply Filters"* button.

Review the following panels:

  - VS Data Rate
  - VS Connection Rate

Use the Time Range dropdown in the upper-right corner
to expand the view to at least the Last 7 Days.

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

This concludes Ticket 2.

Go to `Ticket 03 - Determine Last Application Outage <../lab03/lab03.html>`_

Go to `Overview <../overview.html>`_
