Ticket 25 – Identify Busiest Client IP from WAF Events
======================================================

Title: “What is the busiest client IP address on CentralRegion-bigip-01 related to WAF events?”
-----------------------------------------------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  The security team is investigating recent WAF activity on
  CentralRegion-bigip-01 and wants to quickly identify which
  client IP address is generating the most WAF-related events.

  Instead of manually filtering dashboards and logs, you will
  use the AI Assistant to query WAF event data and return a
  summary of the busiest client IP address.

  Your task is to use the AI Assistant prompt and review the
  returned results for accuracy and context.


Context
~~~~~~~

  Device Name: CentralRegion-bigip-01

  Data Type: WAF Events

  Time Range: Last 24 Hours


Tasks
~~~~~

  Navigate to:

    AI Assistant

  Use the following prompt:

    Can you tell me what the busiest client ip address is on CentralRegion-bigip-01 related to WAF events?

  Review the AI Assistant response and locate the table:

    Busiest Client IP Address on CentralRegion-bigip-01

  Identify the busiest client IP address and record:

  - Client IP Address
  - Request Count
  - Percentage of total WAF events

  Review the Additional Context section (if shown) and capture:

  - Total WAF events in last 24 hours
  - The policy or application associated (if listed)
  - Any violations detected (count and type)
  - Any attack type detected (if listed)

  Confirm the response includes a note indicating this data is based
  on WAF/security events (not full traffic telemetry).


Deliverables
~~~~~~~~~~~~

  A brief summary including:

  - Busiest client IP address
  - Request count and percentage of total WAF events
  - Total WAF events in the last 24 hours
  - Any violation types observed
  - Any attack type observed (if present)
  - Any additional observations from the AI response


Hints
~~~~~

  - If the response looks incomplete, verify your prompt matches
    the ticket exactly and try again.
  - If the AI returns multiple IPs, focus on the highest request count.
  - If the platform supports it, validate the time window is set to
    the last 24 hours before interpreting results.

This concludes Ticket 25.

---

Go to `Ticket 26 - TBD26 <../lab26/lab26.html>`_

Go to `Overview <../overview.html>`_
