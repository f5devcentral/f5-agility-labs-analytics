Ticket 12 – CMP Demotion Caused by iRule Globals
=================================================

Title: “Why is this virtual server only using one CPU?”
-------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  Operations has reported that the virtual server web-app-https on
  WestRegion-bigip-01 appears to be using only a single TMM/CPU,
  even though the device has multiple TMM instances available.

  This behavior is impacting throughput and scalability.
  You have been asked to determine why CMP is demoted on this
  virtual server and which configuration element is responsible.


Context
~~~~~~~

  **Device Name:** WestRegion-bigip-01

  **Virtual Server:** web-app-https

  **Observation:** CMP is demoted for this virtual server, so traffic
  is processed by a single TMM/CPU rather than being distributed
  across available TMM instances.

  For this lab, an iRule intentionally uses a non-static global
  variable (for example, ``::request_count``) attached to
  web-app-https.


Tasks
~~~~~

Use the AI Assistant and enter the following prompt:

  ``Show full configuration details for the web-app-https
  virtual server on WestRegion-bigip-01, including
  assigned iRules and CMP state.``

From the returned information and the TMUI on **WestRegion-bigip-01:**

- Verify the CMP state for the web-app-https virtual server.
- Identify which iRule(s) are attached.
- Inspect the iRule code and locate any regular global variables
  using the ``::name`` syntax (for example,
  ``set ::request_count 0``).

Explain why using a non-static global variable (``::variable``)
in an iRule causes CMP to be demoted:

- Regular global variables are not shared correctly across TMM instances.
- To maintain consistency, BIG-IP forces the virtual server to run
  on a single TMM, reducing parallelism.

As part of your explanation, consider:

- Regular global variables (``::name``) are not shared across TMM instances.
- CMP demotion reduces a virtual server to a single TMM/CPU.
- Mixing CMP-compatible and CMP-incompatible iRules on the same
  virtual server still results in demotion.

Describe how you would refactor the iRule to keep it CMP-safe,
for example:

- Replace non-static globals with per-connection variables.
- Use ``static::`` variables only for read-only configuration data.
- Avoid constructs documented as CMP-incompatible.


Deliverables
~~~~~~~~~~~~

A brief summary describing:

- The CMP state of web-app-https and how you verified it
- Which iRule (and which specific lines) are responsible
  for CMP demotion
- How you would rewrite the iRule to be CMP-compatible
  while preserving its intended behavior


Hints
~~~~~

- Even a single ``::variable`` usage is enough to demote CMP.
- Attaching both CMP-safe and CMP-unsafe iRules to the same
  virtual server does not “average out” — the CMP-unsafe behavior
  still causes demotion.
- Compare CMP mode and TMM distribution before and after
  removing the CMP-unsafe iRule.


This concludes Ticket 12.


Go to `Ticket 13 - WAF Blocking a Known Apache Struts-Like Probe <../lab13/lab13.html>`_

Go to `Overview <../overview.html>`_