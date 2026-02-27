Ticket 5 – Investigating a slow pool member
===========================================

Title: “Why is one web server so slow?”
---------------------------------------

## Ticket description

    Operations has reported that the application behind web_app_42 feels
    sluggish at times. Initial checks show that one of the pool members
    is responding significantly more slowly than the others.

    You have been asked to investigate the performance of the pool members
    behind web_app_42 and determine why one server is slower than the rest.

## Context

    Device Name: EastRegion-bigip-01

    Virtual server: web_app_42

    Pool: web-pool (attached to web_app_42)

    Symptom: One pool member shows higher response times and/or fewer
    completed requests compared to the others.

## Tasks

    Use the AI Assistant and enter the prompt:
    "Show pool statistics for web-pool on the EastRegion-bigip-01."

    Compare these results to the TMUI interface on EastRegion-bigip-01
    under Local Traffic > Pools > web-pool. Do they match? Does the AI
    need to be prompted again?

    Identify which specific pool member is slower based on the available
    metrics (for example, current connections, total requests, or any
    response-time-related statistics that Insight exposes for this pool).

    In Insight, review any available metrics or attributes for the slow
    member, such as:

    - Error rates or HTTP status codes.
    - Connection counts or resets.
    - Health monitor status and history for that member.

    Based on the data you see, form a hypothesis for why this pool member
    is slower. Consider possibilities such as:

    - Resource constraints on the server (CPU, memory).
    - Application-level issues (slow responses for certain URLs).
    - Network-related issues (packet loss, retransmissions).

    Document the additional checks you would perform (or ask the server
    team to perform) on the backend server itself to confirm your hypothesis.

## Deliverables

    A brief summary describing:

    - Which pool member in web-pool is slower and how you determined this.
    - The key statistics or metrics that led you to this conclusion.
    - Your working hypothesis for the root cause and what you would
      investigate next on the backend server or in the application.

## Hints

    Look at how many connections and requests each pool member is handling,
    and whether one member consistently shows different behavior.

    Health monitor status might be green even when an application on a
    server is slow, so you may need to look beyond simple up/down state.

    Comparing metrics across members is often the fastest way to spot an
    outlier that needs deeper investigation.


This concludes Exercise 5.

---

Go to `Exercise 6 - tbd <../lab6/lab6.html>`_

Go to `Overview <../overview.html>`_