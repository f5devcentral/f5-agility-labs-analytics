Ticket 26 – Review Top Resource Consumers
============================================================

Title: “What applications have consumed the most resources over the last 30 days?”
------------------------------------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  Leadership is preparing for quarterly capacity planning
  and wants to understand which applications have consumed
  the most system resources over the past 30 days.

  Instead of reviewing individual dashboards, you will use
  the Top N view to identify long-term resource consumers
  across CPU, bandwidth, SSL, and availability metrics.

  Your task is to analyze 30-day Top N data and summarize
  which applications are driving the most sustained load.


Context
~~~~~~~

  Navigation Path:

    BIG-IP >> Device Overview >> Top N

  Time Range: Last 30 Days


Tasks
~~~~~

  Navigate to:

    BIG-IP >> Device Overview >> Top N

  From the Device dropdown at the top of the page,
  select a BIG-IP.

  Change the Time Range (upper-right corner) to:

    Last 30 Days

  Review the following panels:

    Top 10 VIPs By CPU Utilization
    Top 10 VIPs By WAF CPU Utilization
    Top 10 VIPs By Bandwidth
    Top 10 VIPs By SSL TPS Utilization
    Top 10 Pools By Active Connections

  Identify:

  - The VIP with the highest sustained CPU utilization
  - The VIP with the highest sustained bandwidth usage
  - The VIP with the highest SSL TPS utilization
  - Any pools consistently high in active connections

  Review system-level resource panels:

    Top 10 Process By CPU
    Analysis, Control, Data Plane Utilization

  Determine:

  - Whether TMM has been the dominant CPU consumer
  - Whether control plane utilization appears stable
  - Whether any sustained spikes are visible

  Review availability panels:

    Top 10 Virtual Servers By Low Availability [14d]
    Top 10 Pools By Low Availability [14d]

  Determine whether any applications have experienced
  recurring availability degradation.


Deliverables
~~~~~~~~~~~~

  A 30-day operational summary including:

  - The most resource-intensive VIP (CPU)
  - The highest bandwidth consumer
  - The highest SSL TPS consumer
  - Any pool consistently driving high connection volume
  - Any availability concerns over the last 14–30 days
  - Whether overall system utilization appears healthy
    or trending toward capacity concerns


Hints
~~~~~

  - Sustained high CPU is more important than short spikes.
  - High bandwidth does not always correlate with high CPU.
  - Compare SSL-heavy VIPs with CPU-heavy VIPs.
  - Availability trends over 14 days can reveal recurring issues.
  - Look for consistency across panels — the same VIP
    appearing repeatedly is significant.

This concludes Ticket 26.

---

Go to `Ticket 27 - TBD27 <../lab27/lab27.html>`_

Go to `Overview <../overview.html>`_
