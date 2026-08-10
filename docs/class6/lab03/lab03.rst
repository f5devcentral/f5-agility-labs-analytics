======================================================================
Lab 3: Software Installation Jobs - Orchestrating Fleet Upgrades
======================================================================

Overview
========

In this lab, you will create and execute a **Software Installation Job** in F5 Insight. Software installation jobs install and activate staged software images on target instances across your fleet. You will learn how F5 Insight orchestrates upgrades for both High Availability (HA) pairs and Standalone instances while ensuring zero or minimal traffic disruption.

Objectives
==========

* Understand the differences between **HA Pair** and **Standalone** installation job types.
* Configure an HA Pair installation job with automated failover and Human-In-The-Loop (HITL) pauses.
* Configure a Standalone installation job using Serial (Rolling) or Parallel (Batch) execution.
* Execute, monitor, pause, resume, or abort an active installation job.
* Verify post-installation software version activation and instance metadata refresh.

Prerequisites
=============

* Completion of **Lab 2: Software Distribution Jobs**.
* Target BIG-IP instances with the TMOS ISO image already staged on disk.
* Target HA pair: ``ha-pair-01a.lab.local`` (Active) and ``ha-pair-01b.lab.local`` (Standby).
* Target Standalone instances: ``bigip-01.lab.local`` and ``bigip-02.lab.local``.

Task 1: Understanding Installation Job Types
=============================================

F5 Insight provides specialized installation job types tailored to your architecture:

.. list-table:: Installation Job Types
   :widths: 20 40 40
   :header-rows: 1

   * - Job Type
     - Execution Flow
     - Traffic Impact
   * - **HA Pair**
     - Upgrades Standby instance first -> Verifies health -> Performs controlled failover -> Upgrades formerly Active instance -> Verifies health.
     - **Zero Downtime**: Traffic flows through the Active instance throughout the entire operation.
   * - **Standalone (Serial)**
     - Installs each standalone BIG-IP one at a time sequentially.
     - Individual instance reboot required during volume activation.
   * - **Standalone (Parallel)**
     - Installs multiple standalone BIG-IPs simultaneously in defined batch sizes.
     - Concurrent reboot across batch members; ideal for load-balanced pools.

Task 2: Creating an HA Pair Software Installation Job
======================================================

1. Log into **F5 Insight** and navigate to **Manage** > **Automation** > **Jobs**.
2. Click **Add Job** and select **Software Installation**.
3. In the **Job Name** field, enter:

   .. code-block:: text

      Install_TMOS_17.1.1_HA_Pair_01

4. Select **HA Pair** as the installation job type.
5. Select the target HA pair: ``ha-pair-01a.lab.local / ha-pair-01b.lab.local``.
6. Select the target software image: ``BIGIP-17.1.1-0.0.6.iso``.
7. Under **Target Volume**, select an available volume location (e.g., ``HD1.2``).

Task 3: Configuring Human-In-The-Loop (HITL) Pauses
====================================================

HITL pauses give administrators explicit control to review health metrics before allowing automated failover or proceeding with the second node.

1. Enable **Pause points** in the job configuration:
   * **Pause after Standby installation**: Halts execution after ``ha-pair-01b`` is upgraded, allowing manual health validation before failover.
   * **Pause before failover**: Pauses immediately prior to issuing the HA failover command.
2. Click **Save** to save the job definition or click **Execute Job** to initiate.
3. In the confirmation pop-up, enter Change Request ``CR-98422-INSTALL-HA`` and click **Execute Job**.

Task 4: Monitoring HA Upgrade Workflow and Pauses
=================================================

1. Navigate to **Manage > Automation > Jobs** and click on the executing job.
2. Watch F5 Insight execute the 5-stage HA workflow:
   * **Stage 1**: Identifies ``ha-pair-01a`` as Active and ``ha-pair-01b`` as Standby.
   * **Stage 2**: Installs software on Standby (``ha-pair-01b``) and reboots into new volume ``HD1.2``.
   * **Stage 3**: Job enters **Paused (HITL)** state.
3. Review Standby node metrics, then click **Resume Job**.
4. F5 Insight performs failover (making ``ha-pair-01b`` Active) and proceeds to upgrade ``ha-pair-01a``.
5. Once complete, verify both nodes report healthy status on TMOS version ``17.1.1``.

Task 5: Creating a Standalone Installation Job (Serial or Parallel)
====================================================================

For independent instances not configured in HA:

1. Click **Add Job** > **Software Installation**.
2. Name the job ``Install_TMOS_17.1.1_Standalone_Fleet``.
3. Select **Standalone** as the job type.
4. Select target instances ``bigip-01.lab.local`` and ``bigip-02.lab.local``.
5. Choose execution mode:
   * **Serial (Rolling)**: Upgrades ``bigip-01`` completely before starting ``bigip-02``.
   * **Parallel (Batch)**: Enter **Batch Size** ``2`` to upgrade both simultaneously.
6. Click **Execute Job** and confirm execution.

Task 6: Post-Installation Verification and Metadata Refresh
===========================================================

1. After the installation job completes, F5 Insight automatically triggers an instance metadata refresh to update its inventory database.
2. To manually trigger a metadata refresh via API or UI:
   * Navigate to **Manage > Devices**.
   * Select the upgraded instances and click **Refresh Metadata**.
3. Verify that the **Software Version** column for all updated instances reflects **17.1.1**.

Verification Checkpoint
=======================

* Confirm the installation job state shows **Completed Successfully**.
* Confirm ``ha-pair-01a.lab.local`` and ``ha-pair-01b.lab.local`` are running TMOS ``17.1.1`` in HA synchronized state.
* Confirm standalone instances reflect TMOS ``17.1.1``.


Go to `Ticket 04 - Review Connection Count Standard Deviation <../lab04/lab04.html>`_

Go to `Overview <../overview.html>`_