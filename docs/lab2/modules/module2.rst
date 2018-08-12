Configuring the BIG-IP to send analytics data to Splunk
-------------------------------------------------------

F5 has created an iApp that simplifies the process of configuring your BIG-IP 
to send Analytics data to remote sources (including Splunk and/or BIG-IQ). 
There is also a deployment guide that walks you through the steps needed to 
configure the iApp. 

- Details about the iApp and deployment guide can be found on the Ask F5 Support 
  site here: https://support.f5.com/csp/article/K07859431

- You can also find a high-level overview of the iApp, as well as some additional 
  resources (including demo videos of the Splunk integration) on the following `F5 DevCentral <https://devcentral.f5.com>`__ page: 
  https://devcentral.f5.com/codeshare/f5-analytics-iapp 

.. NOTE:: 
    The F5 Analytics iApp template itself does not ship with the product, but 
    can be downloaded from the F5 downloads site (https://downloads.f5.com).

    For your convenience, we have already downloaded the iApp template on the 
    Windows jump box, so we can just import it into our BIG-IP.

.. toctree::
   :maxdepth: 1
   :glob:

   task2

