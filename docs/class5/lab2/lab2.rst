Ticket 2 – Uneven load balancing due to OneConnect
==================================================

Title: “One pool member is overloaded”
--------------------------------------

## Ticket description

    Operations has noticed that one application server in the pool
    ``/Common/web-pool`` has far more connections and traffic than the other
    members. Users are reporting intermittent slowness and occasional timeouts
    when accessing the application.

## Context

    Device Name: East

    Virtual server: /Common/web_app_42

    Service: HTTPS (port 443)

    SNAT: Automap

    OneConnect profile: /Common/max_reuse_1500 with a wide source mask
    and high maximum reuse

    Pool: /Common/web-pool with multiple application servers

## Tasks

    Traditionally we would examine current connection and request distribution
    for the pool members using the BIG-IP GUI and the CLI (for example,
    ``tmsh show ltm pool /Common/web-pool members``).

    For this lab please use the AI Assistant and enter the prompt:
    "Show pool statistics for app-1 pool on the CentralRegion-bigip-01"

    Compare these results to the TMUI interface on the CentralRegion-bigip-01
    under Local Traffic > Pools > app-1. Do they match? Does the AI need
    to be prompted again?

    In Insight go to Device Virtual Server under BIG-IP Device and from the
    top select the device name and virtual server.

    Inspect the profiles assigned to /Common/web_app_42 and identify:

    - Which OneConnect profile is in use.
    - The source mask and maximum reuse settings on that OneConnect profile.
    - The SNAT configuration (Automap vs SNAT pool).

    Explain why the combination of SNAT Automap and a OneConnect source mask
    of 0.0.0.0 (or an equivalent wide mask) with a high reuse value can
    result in very uneven load distribution across pool members.

    Implement a configuration change to improve load distribution. Possible
    approaches include, but are not limited to:

    - Adjusting the OneConnect source mask to a more specific value.
    - Using a SNAT pool with multiple addresses instead of Automap.
    - Tuning maximum reuse if appropriate for the application.

    After making the change, verify that traffic is distributed more evenly:

    - Reset statistics as needed.
    - Generate test traffic.
    - Re-run ``tmsh show ltm pool /Common/web-pool members`` (or equivalent)
      to confirm improved balance.

## Deliverables

    Pre-change evidence of skewed member usage (for example, a screenshot
    or CLI output showing connection and request counts per member).

    Post-change evidence of more even load distribution.

    A brief written explanation (2–3 sentences) describing:

    - The root cause of the uneven distribution.
    - How the chosen configuration change addressed the issue.

## Hints

    Consider what the application servers see as the client IP address when
    SNAT Automap is enabled.

    Review how the OneConnect source mask groups connections for reuse.

    Remember that with a wide mask and SNAT Automap, many clients can appear
    as a single source from the servers' perspective, leading to heavy reuse
    of a small number of server-side connections.
