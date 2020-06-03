Class 1 - Introduction to AVR
=============================

The **Application Visibility and Reporting (AVR)** module provides detailed charts 
and graphs to give you more insight into the performance of web applications, with 
detailed views on HTTP and TCP stats, as well as system performance (CPU, memory, etc.). 
You can use this module to visualize the traffic being processed by your BIG-IP device, 
and gain a better understanding of where the traffic is originating from (client IP 
addresses / subnets as well as geographical regions), the nature and volume of request 
and response traffic (Total Transactions as well as Average and Max Transactions/sec), 
the most commonly requested URLs, Server Latency and Page Load times, Virtual Server 
and Pool member performance, and many more metrics. 

This lab will give you an introduction on how to setup the AVR module to generate 
these charts / reports and how to visualize them on your BIG-IP.


.. NOTE::
    The AVR module is a built-in module that is included at no charge with all 
    BIG-IP licenses for software versions 11.x and higher. However, this module
    is not enabled by default since it consumes additional resources. Hence you 
    must make the conscious decision to provision the module and enable analytics 
    data collection on the Virtual Servers of interest. In your own production 
    environment, you may want to start with enabling analytics data collection on 
    a handful of virtual servers and observe the impact to system performance before 
    enabling it on a larger number of virtual servers.



.. toctree::
   :maxdepth: 2
   :glob:

   intro
   modules/module*
