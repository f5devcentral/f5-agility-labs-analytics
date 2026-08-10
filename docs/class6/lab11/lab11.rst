Ticket 11 – Uneven Load Balancing 
===================================================

Title: “Are My Profiles Well?”
---------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  Operations has noticed that one application server in
  */Common/web-pool* has significantly more connections and
  traffic than the other members. Users are reporting
  occasional timeouts when accessing the application.

  You have been asked to investigate why load distribution
  is uneven and determine which configuration elements
  may be contributing to the issue.  While this is the same VS, it is a different issue than ticket 10.  


Context
~~~~~~~

  **Device Name:** EastRegion-bigip-01

  **Virtual Server:** /Common/web_app_42

  **Service:** HTTPS (port 443)

  **SNAT:** Automap

  **OneConnect Profile:** /Common/max_reuse_1500

  **Pool:** /Common/web-pool (multiple application servers)


Tasks
~~~~~

  Traditionally, you would examine connection and request distribution using the BIG-IP GUI or CLI, for example:

    ``tmsh show ltm pool /Common/web-pool members``

  For this lab, use the AI Assistant and enter the following prompt:

    ``Show pool statistics for /Common/web-pool on EastRegion-bigip-01.``

  Compare these results to the TMUI interface on
  EastRegion-bigip-01 under:

    **Local Traffic >> Pools >> web-pool**

  Determine whether the AI results match the TMUI data.  In Insight, navigate to:

    **BIG-IP Device >> Device Virtual Server**

    Select the appropriate device and virtual server
    */Common/web_app_42*.

    Inspect the assigned profiles and identify:

    - Which OneConnect profile is in use
    - The source mask and maximum reuse settings
    - The SNAT configuration (Automap vs SNAT pool)

    Explain why the combination of SNAT Automap and a
    OneConnect source mask of 0.0.0.0 (or an equivalently
    wide mask) with a high reuse value can result in uneven
    load distribution across pool members.

Deliverables
~~~~~~~~~~~~

  Briefly answer the following:
  
    - What do you believe is the root cause of the uneven distribution?

  Review the following for additional information and trends:

    - Evidence of skewed member usage
      (for example, screenshot or CLI output)
    - Proposed solution covering:

        - The root cause of the uneven distribution?
        - What configuration change could resolve the issue?

Hints
~~~~~

  - Consider what the application servers see as the
    client IP address when SNAT Automap is enabled.
  - Review how the OneConnect source mask groups
    connections for reuse.
  - With a wide mask and SNAT Automap, many clients
    can appear as a single source, leading to heavy
    reuse of a small number of server-side connections.

This concludes Ticket 11.

Go to `Exercise 12 - CMP Demotion Caused by iRule Globals <../lab12/lab12.html>`_

Go to `Overview <../overview.html>`_