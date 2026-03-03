Ticket 10 – Investigating a Slow Pool Member
============================================

Title: “Why is one web server so slow?”
---------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  Operations has reported that the application behind *web_app_42*
  feels sluggish at times. Initial checks indicate that one of
  the pool members is responding significantly more slowly than
  the others.

  You have been asked to investigate the performance of the
  pool members behind *web_app_42* and determine why one server
  appears slower than the rest.


Context
~~~~~~~

  **Device Name:** EastRegion-bigip-01

  **Virtual Server:** web_app_42

  **Pool:** web-pool (attached to web_app_42)

  **Symptom:** One pool member shows higher response times and/or
  fewer completed requests compared to the others.


Tasks
~~~~~

Use the AI Assistant and enter the following prompt:

  ``Show pool statistics for web-pool on EastRegion-bigip-01.``

Compare these results to the TMUI interface on EastRegion-bigip-01
under:

  **Local Traffic >> Pools >> web-pool**

Determine whether the AI results match the TMUI data.
If necessary, refine the prompt.

Identify which specific pool member appears slower based on
available metrics (for example, current connections, total
requests, or response-time-related statistics exposed in Insight).

In Insight, review additional metrics for the slower member,
such as:

- Error rates or HTTP status codes
- Connection counts or resets
- Health monitor status and history

Based on the data observed, form a hypothesis for why this
pool member is slower. Consider possibilities such as:

- Resource constraints on the server (CPU, memory)
- Application-level issues (slow responses for certain URLs)
- Network-related issues (packet loss, retransmissions)

Document the additional checks you would perform (or request
from the server team) on the backend server to validate your hypothesis.


Deliverables
~~~~~~~~~~~~

  A brief summary describing:

  - Which pool member in web-pool is slower and how you determined this
  - The key statistics or metrics that led to your conclusion
  - Your working hypothesis for the root cause
  - What you would investigate next on the backend server or application


Hints
~~~~~

  - Compare connections and request counts across pool members.
  - Health monitor status may remain green even if an application
    is responding slowly.
  - Identifying an outlier is often the first step in troubleshooting.


This concludes Ticket 10.


Go to `Ticket 11 - Uneven Load Balancing Due to OneConnect <../lab11/lab11.html>`_

Go to `Overview <../overview.html>`_