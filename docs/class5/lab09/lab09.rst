Ticket 09 – Investigating Unexpected 4xx Responses
==================================================

Title: “Why is accounts_receivable returning 4xx errors?”
---------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

Users of the accounts receivable application are intermittently
receiving HTTP 4xx errors when accessing the service. Some users
report seeing 400, 401, 403, or 404 responses at different times.

You have been asked to investigate why the
accounts_receivable_https_vs virtual server is returning
these 4xx status codes and determine whether this behavior
is expected for the lab scenario.


Context
~~~~~~~

**Device Name:** EastRegion-bigip-01

**Virtual Server:** accounts_receivable_https_vs

**Pool:** app-3

**Observed Behavior:**

  - Traffic that hits any pool member listening on port 8080
    generates an HTTP 403 response.
  - Traffic that hits the paths /401, /403, /404, or /400
    returns the corresponding 4xx status code.
  - A traffic script rotates through those paths to generate
    a variety of 4xx responses.


Tasks
~~~~~

Use the AI Assistant and enter the following prompt:

  ``Show configuration details for the accounts_receivable_https_vs virtual server on EastRegion-bigip-01, including its default pool and any attached profiles or iRules.``

From the returned information and the TMUI on EastRegion-bigip-01:

- Confirm that the default pool for
  *accounts_receivable_https_vs* is *app-3.*
- Identify which port(s) the app-3 pool members are
  listening on (for example, 8080).
- Check whether any iRules, local traffic policies,
  or WAF policies attached to the virtual server
  could influence HTTP status codes.

In Insight, review available HTTP metrics or logs
associated with accounts_receivable_https_vs and app-3
that show:

  - The distribution of 4xx status codes.
  - Whether certain paths are consistently associated with specific 4xx responses.

Based on this information, determine:

  - Which 4xx responses are expected behavior due to
    the backend configuration and rotating traffic script.
  - Whether any 4xx responses indicate a real issue,
    or are intentionally generated for this lab exercise.


Deliverables
~~~~~~~~~~~~

A brief summary describing:

  - How the accounts_receivable_https_vs virtual server and app-3 pool are configured to return 4xx responses
  - Which 4xx codes and paths are intentionally generated (for example, /401 → 401, /403 → 403, /404 → 404, /400 → 400, and 403 for port 8080) 
  - Your conclusion on whether the observed 4xx errors are expected (lab-driven) or indicative of a misconfiguration


Hints
~~~~~

- Review how the backend application on port 8080 is configured to respond to different paths.
- If a traffic script rotates through /401, /403, /404, and /400, seeing those 4xx codes in logs is likely expected behavior.
- Distinguishing between expected and unexpected 4xx responses is an important troubleshooting skill.


This concludes Ticket 09.


Go to `Ticket 10 - Investigating a Slow Pool Member <../lab10/lab10.html>`_

Go to `Overview <../overview.html>`_