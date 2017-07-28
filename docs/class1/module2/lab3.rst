Lab 3: Understanding the setup
------------------------------

While you wait for the traffic to be generated and sent to the BIG-IPs,
and for Splunk to gather and analyze the data, let us explore the setup
for this lab.

F5.analytics iApp on BIG-IP
~~~~~~~~~~~~~~~~~~~~~~~~~~~

This iApp template is designed to gather a large number of statistics
and event information from a variety of different sources, and export
the data to different kinds of data collectors / SIEM systems. The
sources of information that the iApp gathers include system performance
metrics (CPU, memory usage, throughput, connection rates, etc.), tmstats
(statistics collected by the Traffic Management Microkernel / TMM
regarding the traffic that is being handled/processed by TMM), event
logs (from the /var/log directory), SNMP trap-related information, and
AVR data. The options in the iApp allow the user fine-grained control on
what data will be collected and bundled up to be sent to external
receivers. Further, the iApp also provides the ability to customize the
output format for different receivers, including F5 BIG-IQ, Splunk, as
well as other 3\ :sup:`rd`-party systems. Lastly, the iApp provides for
options to group together and/or map different pieces of information
(Virtual Servers and their associated objects, etc.) into Facilities
(e.g. data centers), tenants (for multi-tenant environments), and
applications, where a single application could consist of multiple
virtual servers (for example, a web application could consist of both,
an HTTP and an HTTPS virtual server that serve the host the same
application). This application mapping can also be applied across
multiple BIG-IPs so that the same application hosted in different
locations can be grouped together under a single application name. For
more details on the iApp, please see the iApp Deployment Guide, which
can be found here:

`https://www.f5.com/pdf/deployment-guides/f5-analytics-dg.pdf <https://www.f5.com/pdf/deployment-guides/f5-analytics-dg.pdf>`__

F5 Networks Splunk App for Splunk
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Splunk is a very popular Security Information and Event Management
(SIEM) system that has the ability to accept statistics and event data
from a large variety of sources, and visualize and display it in a
meaningful way to allow an end-user to be able to view events and
metrics across multiple devices from a single-pane-of-glass view.
Additionally, Splunk allows add-on applications to be integrated into
the Splunk deployment in order to allow customized processing and
display of data from various sources. The F5 Networks Splunk app is just
such an add-on that was created by F5 to allow customized processing of
data from F5 BIG-IP devices, and to produce easy-to-use dashboards that
analyze and present the data in meaningful charts and graphs.

The data presented in the F5 Networks Splunk app includes a lot of data
that cannot be easily visualized on a BIG-IP, such as tmstats
information, virtual server and pool member health stats, system
performance information, and even syslog event information.
Additionally, this app provides the ability to collate and present data
across multiple BIG-IP devices, even BIG-IPs in different locations,
allowing a user to view all their devices and their data in one single
central location, rather than having to view it separately on each
individual BIG-IP device.

Configuration options for F5.analytics iApp and F5 Networks Splunk app
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Note that this lab guide walks you through some simple setup options for
both, the Splunk app as well as the iApp, in order to help you get
up-and-running quickly. However, these configuration options are by no
means the only way to configure these. To get a better understanding of
all the configuration options we ask that you refer to the F5 analytics
iApp deployment guide referenced earlier which also has a section on
configuring the Splunk app.
