Ticket 06 – Identifying Orphaned Objects
========================================

Title: “What are these unused pools and nodes?”
-----------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

  During a routine review of the CentralRegion-bigip-01 configuration,
  operations suspects there may be unused (orphaned) objects left over
  from previous testing or decommissioned applications.

  You have been asked to identify any orphaned pools and nodes on
  CentralRegion-bigip-01 so they can be documented and, if appropriate,
  cleaned up later.


Context
~~~~~~~

  Device Name: CentralRegion-bigip-01

  These objects are believed not to be referenced by any active
  virtual servers.


Tasks
~~~~~

  Use the AI Assistant and enter the following prompt:

    Show all pools and nodes on CentralRegion-bigip-01,
    and indicate which ones are not referenced by any
    virtual server.

  From the returned information and the TMUI on CentralRegion-bigip-01:

  - Navigate to:

      Local Traffic >> Pools >> Pool List

    Confirm whether bruce_wayne and oliver_twist
    appear in the configuration.

  - Verify whether either pool is assigned as a default pool
    (or referenced in a policy) on any virtual server.

  Next, navigate to:

      Local Traffic >> Nodes >> Node List

  - Confirm whether clark_kent and harry_potter
    appear in the node list.
  - Verify whether any pool members reference these nodes,
    or whether they are completely unused.

  Summarize which of the above pools and nodes are truly
  orphaned (that is, not referenced by any virtual server
  or pool).

  Do not delete anything as part of this exercise.
  The goal is only to locate and document orphaned objects.


Deliverables
~~~~~~~~~~~~

  A brief summary describing:

  - A clear list of which objects are confirmed to be
    orphaned on CentralRegion-bigip-01


Hints
~~~~~

  - A pool is considered orphaned if no virtual server
    uses it as a default pool and it is not referenced
    by policies or iRules.
  - A node is considered orphaned if no pool member
    references it.
  - Comparing object references (who uses what) is a key
    step when cleaning up legacy configuration.

  Suspected orphaned objects:

  - Pools: bruce_wayne, oliver_twist
  - Nodes: clark_kent, harry_potter


This concludes Ticket 08.
---

Go to `Ticket 07 - Verify Application Configuration Consistency Across BIG-IPs <../lab07/lab07.html>`_

Go to `Overview <../overview.html>`_