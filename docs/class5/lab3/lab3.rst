Ticket 3 – Identifying HTTP versions in use
===========================================

Title: “What HTTP version is this app really using?”
----------------------------------------------------

## Ticket description

    Operations wants to better understand the HTTP versions in use across
    the environment. They suspect that the Backup_app service is still using
    HTTP/1.0, which might impact connection behavior and troubleshooting.

    You have been asked to confirm what HTTP version is actually being used
    between clients and BIG-IP, and between BIG-IP and the pool members.

## Context

    Device Name: CentralRegion-bigip-01

    Virtual server: Backup_app

    Pool: app-1

    Expectation: Most of the lab environment is using HTTP/1.0, but this
    needs to be verified rather than assumed.

## Tasks

    Use the AI Assistant and enter the prompt:
    "Show configuration details for the Backup_app virtual server on the CentralRegion-bigip-01, including attached profiles."

    From the returned information and the TMUI on CentralRegion-bigip-01:

    - Identify which HTTP profile is attached to the Backup_app virtual
      server (if any).
    - Note any HTTP profile settings that influence protocol versions
      (for example, HTTP/1.0 vs HTTP/1.1 behavior, keep-alive settings).

    In Insight, review any available HTTP-related metrics or attributes
    for Backup_app and its pool app-1 that indicate HTTP protocol behavior
    (for example, headers, connection reuse, or profile details).

    Summarize whether Backup_app is effectively using HTTP/1.0 or a newer
    version on the client side, and whether server-side connections to the
    app-1 pool members behave differently.

## Deliverables

    A brief summary describing:

    - The HTTP profile attached to Backup_app, and any relevant settings
      that affect HTTP version behavior.
    - Your conclusion about the HTTP version behavior from the client to
      the Backup_app virtual server.
    - Any observations about server-side HTTP behavior to the app-1 pool
      members (for example, whether it appears to be HTTP/1.0-style
      request/response without reuse, or if keep-alive is used).

## Hints

    Look at which HTTP profile is attached and whether it is a custom
    profile or the default http profile.

    Some HTTP/1.0-style behavior can be inferred from how connections are
    opened and closed, and whether keep-alive is in use.

    Comparing what BIG-IP is configured to do on both client and server
    sides will help you understand where the HTTP version behavior is
    coming from.


This concludes Exercise 3.

---

Go to `Exercise 3 - Exporting BIG-IP metrics using the OTel consumer <../lab3/lab3.html>`_

Go to `Overview <../overview.html>`_