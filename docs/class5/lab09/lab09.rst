Ticket 09 – Investigating APM Session Activity Across Devices
==============================================================

Title: “Which BIG-IPs Are Actively Handling APM Sessions?”
-----------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  The APM dashboard displays session activity across multiple BIG-IP devices.
  You have been asked to determine which BIG-IPs are actively processing
  APM access sessions and whether the observed session behavior is expected.

  Specifically, review the "Current APM Access Sessions by State" panel
  and identify which devices are showing active or established sessions.


Context
~~~~~~~

  Dashboard: APM Overview

  **Device Name:**
    - CentralRegion-bigip-01
    - EastRegion-bigip-01
    - SecurityRegion1-bigip-01
    - WestRegion-bigip-01

  Panel of Interest:
    - Current APM Access Sessions by State


Tasks
~~~~~

  Navigate to:

    **Dashboards >> BIG-IP Fleet >> APM Sessions**

  Review the "Current APM Access Sessions by State" panel.

  Identify which BIG-IP device(s) are showing:

    - Active sessions
    - Established sessions

  Identify which BIG-IP device(s) are processing any APM sessions.

  Observe the timeline and determine:
    - Did session counts fluctuate?
    - Did sessions drop to zero at any point?
    - If so, at approximately what time?

Deliverables
~~~~~~~~~~~~

  Briefly answer the following:
    - Which devices are actively handling APM sessions?
    - Which devices show no session activity?

  Review the following for additional information and trends:
    
    - Is APM traffic evenly distributed across devices?
    - Does one device appear to be the primary session handler?
    - Is there evidence of a restart, timeout, or session clearing event?

Hints
~~~~~

  - Use the filter to select all BIG-IPs.
  - Adjust the Time Range to view a larger activity window.
  - Compare active vs established session lines carefully.


 This concludes Ticket 09.

Go to `Ticket 10 - Investigating a Slow Pool Member <../lab10/lab10.html>`_

Go to `Overview <../overview.html>`_