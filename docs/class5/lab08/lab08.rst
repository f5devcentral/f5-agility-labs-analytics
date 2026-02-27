Ticket 08 – Identifying orphaned objects
=======================================

Title: “What are these unused pools and nodes?”
-----------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  During a routine review of the Centralregion-bigip-01 configuration,
  operations suspects there may be unused (orphaned) objects left over
  from previous testing or decommissioned applications.

  You have been asked to identify any orphaned pools and nodes on
  Centralregion-bigip-01 so they can be documented and, if appropriate,
  cleaned up later.

Context
~~~~~~~

  Device Name: Centralregion-bigip-01

  These objects are believed not to be referenced by any active virtual
  servers.

Tasks
~~~~~

  Use the AI Assistant and enter the prompt:
  "Show all pools and nodes on the Centralregion-bigip-01, and indicate which ones are not referenced by any virtual server."

  From the returned information and the TMUI on Centralregion-bigip-01:

  - Navigate to **Local Traffic > Pools > Pool List** and confirm
    whether bruce_wayne and oliver_twist appear in the configuration.
  - Check whether either of these pools is assigned as the default pool
    (or used in a policy) on any virtual server.

  Next, navigate to **Local Traffic > Nodes > Node List** and:

  - Confirm whether clark_kent and harry_potter appear in the node list.
  - Verify whether any pool members reference these nodes, or whether
    they are completely unused.

  Summarize which of the above pools and nodes are truly orphaned
  (that is, not referenced by any virtual server or pool).

  Do **not** delete anything as part of this exercise; the goal is only
  to locate and document orphaned objects.

Deliverables
~~~~~~~~~~~~

  A brief summary describing:

  - A clear list of which objects are confirmed to be orphaned on
    Centralregion-bigip-01.

Hints
~~~~~

  A pool is usually considered orphaned if no virtual server uses it
  as a default pool and it is not referenced by other configuration
  objects such as policies or iRules.

  A node is considered orphaned if no pool member points to it.

  Comparing object references (who uses what) is a key step when
  cleaning up legacy configuration on BIG-IP devices.

  Suspected orphaned objects:

  - Pools: bruce_wayne, oliver_twist
  - Nodes: clark_kent, harry_potter


This concludes Ticket 08.

---

Go to `Ticket 09 - WAF false positives on file uploads <../lab9/lab9.html>`_

Go to `Overview <../overview.html>`_