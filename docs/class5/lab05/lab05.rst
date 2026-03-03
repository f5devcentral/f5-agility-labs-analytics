Ticket 05 – Review Pool Availability Ratio Deviation
=====================================================

Title: “Are any application pools experiencing availability degradation?”
---------------------------------------------------------------------------

Ticket Description
~~~~~~~~~~~~~~~~~~

The operations team wants to verify that application pools
are maintaining expected availability levels.  An anomaly category exists for *Pool Availability Ratio
Deviation* under *Anomaly Detection*.

Before escalating any potential issue, the team needs a
clear understanding of current pool health and whether
any pools have deviated from expected availability ratios.

Your task is to review the Pool Availability dashboard
and determine if any pools are outside expected thresholds.


Context
~~~~~~~

**Location:** Home Dashboard

**Section:** System Report Cards

**Category:** Anomaly Detection

**Metric:** Pool Availability Ratio Deviation


Tasks
~~~~~

1. Navigate to: **Home >> System Report Cards**

2. Locate the card: **Anomaly Detection**

3. Click on: **Anomaly Detection**

4. Within the expanded panel, locate: **Pool Availability Deviation**

5. Click: **View Details**

6. Scroll down to the **Pools** table.

7. Review each Pool and identify:

  - Status (Critical, Warning, Good)
  - Expected Availability Ratio
  - Current Availability Ratio
  - Deviation value and percentage

8. Pay attention to severity coloring:

  - Red indicates Critical deviation
  - Yellow indicates Warning
  - Green indicates Normal/Good

9. Select any *Pool* from the list.  The graph above will update based on your selection.

10. Review the *Pool Availability Ratio Deviation Analysis* graph.
11. Observe:

  - Actual availability ratio
  - Expected availability ratio
  - Upper threshold
  - Lower threshold

12. Determine whether the actual value crossed either threshold.

13. Use the time range selector (1h, 6h, 1d, 1w) in the upper-right corner of the dashboard to review different time windows.


Deliverables
~~~~~~~~~~~~

A brief summary including:

  - The total number of Pools listed
  - How many are Critical
  - How many are Warning
  - How many are Good
  - Whether any pool crossed defined thresholds
  - Any patterns you observe in availability trends


Hints
~~~~~

- If all pools show 1.00 availability, verify that no deviation exists.
- Hover over graph points to see exact values.
- Try expanding the time range to confirm stability over time.
- Compare Expected vs Actual lines carefully.

This concludes Ticket 5.


Go to `Ticket 06 - Identifying Orphaned Objects <../lab06/lab06.html>`_

Go to `Overview <../overview.html>`_
