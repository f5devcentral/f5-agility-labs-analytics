.. _top:

F5 BD OTel Introductory Lab
============================================================================

This self-guided lab is intended to provide a hands-on introduction to Open Telemetry (OTel) concepts and their implementation.  During this lab, attendees will utilize a [UDF](https://udf.f5.com) blueprint deploy the lab infrastructure shown below to:
 * Gain insight into how applications are instrumented utilizing the Open Telemetry sdk

 * Configure telemetry streaming of metrics from F5 BIG-IP utilizing the OTel collector gateway 

.. image:: ../images/labenviron.png

As illustrated above, the lab environment consists of the following:
   * **F5 BIG-IP(s)** providing L4/L7 ADC Services and utilizing **F5 Telemetry Streaming** (TS) to stream telemetry data to an OTel collector gateway

   * **NGINX Plus** providing L4/L7 ADC Services and utilizing Open Telemetry to stream telemetry data to an OTel collector gateway

   * **Sample Application** consisting of a simple python frontend application and a Redis backend database

   * **Open Telemetry Collector** configured to receive and proxy telemetry from both the BIG-IP and sample applications to the observability platforms

   * **Jaeger** providing visibility for application tracing

   * **Prometheus** providing visibility for BIG-IP metrics
---
Go to `Exercise 1 - App instrumentation walk-through and troubleshooting <./lab1/lab1.html>`_

Go to `Exercise 2 - Exporting NGINX Plus spans and metrics using Open Telemetry <./lab2/lab2.html>`_

Go to `Exercise 3 - Exporting BIG-IP metrics using the OTel consumer <./lab3/lab3.html>`_

`Back to Top <top_>`_