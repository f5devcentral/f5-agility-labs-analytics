.. _top:

Getting Started
===============

Please follow the instructions provided by the instructor to start your
lab and access your jump host.

.. NOTE::
	 All work for this lab will be performed exclusively from your web browser. No installation or interaction with your local system is
	 required.

Lab Topology
------------

The following components have been included in your lab environment:

- 4 x F5 BIG-IP VE (v17.5 and v21.0)
- 1 x F5 Insight
- 1 x Ubuntu Noble - NGINX web services and Traffic Generation

Lab Components
--------------

The following table lists VLANS, IP Addresses and Credentials for all
components:

.. list-table::
    :widths: 20 40 40
    :header-rows: 1
    :stub-columns: 1

    * - **Component**
      - **VLAN/IP Address(es)**
      - **Credentials**
    * - F5 Insight
      - - **Management:** 10.1.1.4
        - **FrontEnd:** 10.1.10.0/24
        - **BackEnd:** 10.1.20.0/24
      - ``admin``/``HelloUDF``



Overview
--------------

This lab is intended to provide a hands-on introduction to F5 Insight for ADSP.  During this lab, attendees will utilize a `UDF <https://udf.f5.com>`_ blueprint deploy the lab infrastructure shown below to:
 * Discover how applications are operating

 * Discover how to improve application health
  
 * Troubleshoot application health and propose solutions

As illustrated above, the lab environment consists of the following:
   * **F5 BIG-IP(s)** providing L4/L7 ADC Services 

   * **NGINX Plus** providing web services

   * **Traffic Generator** configured to generate application traffic simulating users

Deploy blueprint and connect to jumpbox
---------------------------------------

From the `UDF <https://udf.f5.com/blueprints>`_ console, search for and deploy the blueprint entitled *AppWorld 2026 - F5 Insight for ADSP*. 
Once the blueprint has finished deploying, access F5 Insight by selecting the GUI access link, (*see below*).  Credentials for this lab can be viewed by accessing the guest(s) **DOCUMENTATION** tab.

.. image:: ../images/Picture1.png
   :width: 750px
   :alt: Image 1

Upon successful login to F5 Insight, you will arrive at the home page, (see below).

.. image:: ../images/Picture2.png
   :width: 650px
   :alt: Image 2

---

Go to `Introduction <./introduction.html>`_

`Back to Top <top_>`_