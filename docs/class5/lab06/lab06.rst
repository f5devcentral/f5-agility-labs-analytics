Ticket 06 – CMP demotion caused by iRule globals
===============================================

Title: “Why is this virtual server only using one CPU?”
------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  Operations has reported that the virtual server web-app-https on
  westRegion-bigip-01 appears to be using only a single TMM/CPU, even
  though the device has multiple TMM instances available.

  This behavior is impacting throughput and scalability for this
  application. You have been asked to determine why CMP is demoted on
  this virtual server and what part of the configuration is responsible.

Context
~~~~~~~

  Device Name: westRegion-bigip-01

  Virtual server: web-app-https

  Observation: CMP is demoted for this virtual server, so traffic is
  processed by a single TMM/CPU rather than being spread across all
  available TMM instances.

  For this lab, an iRule intentionally uses a non-static global variable
  (for example, ``::request_count``) attached to web-app-https.

Tasks
~~~~~

  Use the AI Assistant and enter the prompt:
  "Show full configuration details for the web-app-https virtual server on the westRegion-bigip-01, including assigned iRules and CMP state."

  From the returned information and the TMUI on westRegion-bigip-01:

  - Verify the CMP state for the web-app-https virtual server.
  - Identify which iRule(s) are attached to web-app-https.
  - Inspect the iRule code and locate any regular global variables using
    the ``::name`` syntax (for example, ``set ::request_count 0``).

  Explain why using a non-static global variable (``::variable``) in an
  iRule causes CMP to be demoted:

  - Regular global variables are not shared correctly across TMM
    instances.
  - To maintain consistency, BIG-IP forces the virtual server to run on
    a single TMM (single CPU), reducing parallelism.

  Consider the following teaching points as you write your explanation:

  - Regular global variables (``::name``) are not shared across TMM
    instances and therefore force a virtual to be demoted from CMP.
  - CMP demotion reduces a virtual server to a single CPU (single TMM),
    impacting throughput and scalability.
  - Many legacy examples on the internet still use ``::`` globals; in
    modern code they should almost never be used.
  - Mixing CMP-compatible and CMP-incompatible iRules on the same VIP
    still causes demotion of that VIP.

  Describe how you would refactor the iRule to keep it CMP-safe, for
  example:

  - Replace non-static globals with per-connection variables.
  - Use ``static::`` variables only for read-only configuration data.
  - Avoid constructs documented as CMP-incompatible.

Deliverables
~~~~~~~~~~~~

  A brief summary describing:

  - The CMP state of the web-app-https virtual server and how you
    verified it.
  - Which iRule (and which specific lines) are responsible for CMP
    demotion.
  - How you would rewrite the iRule to be CMP-compatible, while
    preserving its intended behavior.

Hints
~~~~~

  Look closely for ``::variable`` usage in the iRule code; even a single
  non-static global variable is enough to demote CMP on the entire
  virtual server.

  Remember that attaching both CMP-safe and CMP-unsafe iRules to the same
  VIP does not “average out” — the CMP-unsafe behavior wins and the VIP
  is still demoted.

  When in doubt about CMP behavior, compare the CMP mode and TMM
  distribution for a virtual server with and without the CMP-unsafe iRule
  attached.

This concludes Ticket 06.

---

Go to `Ticket 07 - Investigating unexpected 4xx responses <../lab7/lab7.html>`_

Go to `Overview <../overview.html>`_