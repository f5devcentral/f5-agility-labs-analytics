Lab 2: Configuring the BIG-IP to send analytics data to Splunk
--------------------------------------------------------------

In order to simplify the configuration of your BIG-IP to send Analytics
data to remote sources (including Splunk and/or BIG-IQ), F5 has created
an iApp that simplifies the process. Additionally, there is also a
deployment guide that walks you through the steps needed to configure
the iApp. Details about the iApp and deployment guide can be found on
the Ask F5 Support site here:

`https://support.f5.com/csp/article/K07859431 <https://support.f5.com/csp/article/K07859431>`__

Note that the F5 Analytics iApp template itself does not ship with the
product, but can be downloaded from the F5 downloads site
(https://downloads.f5.com).

For your convenience, we have already downloaded the iApp template on
the Windows jump box, so we can just import it into our BIG-IP.

Task 1: Import and configure the F5 Analytics iApp template on the BIG-IP
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Open a new tab in your Chrome browser, and click on the bookmark for
   **BIGIP\_A** to connect to the BIG-IP GUI

#. Login using the following credentials:

   Username: ``admin``

   Password: ``AgilityLab17``

#. Go to **iApps > Templates**

#. Click **Import** in the top-right

   |image27|

#. Click **Choose File**

#. Navigate to **Desktop > Analytics Lab Files**, and select the
   ``f5.analytics.v3.7.0.tmpl`` file. Click **Open**

   |image28|

#. Click **Upload**

#. Once the file is finished uploading, you should see it listed in the
   iApp Templates table.

#. Go to **iApps > Application Services > Applications**

#. Click **Create** in the top-right

   |image29|

#. For the **Name**, enter ``F5-Analytics``

#. From the **Template** pull-down menu, choose ``f5.analytics.v3.7.0``

   |image30|

#. In the template configuration, in the **Welcome to the f5 BIG-IP
   Analytics iApp Template** section, change the response for the 
   ``Do you want to see inline help?`` Question to 
   ``No, do not show inline help.``

   |image31|

   .. NOTE:: If you are not familiar with what all the different settings
      refer to, you may want to keep the inline help enabled. For now, we
      have disabled it just to reduce the amount of additional text on the
      configuration screen.

#. Under the **Information Sources** section, set the following:

   - Data Format: ``Splunk``

   - System Statistic: ``Yes``

   - Module High Speed Logging Streams: ``Yes``

   - Local System Logging (syslog): ``Yes``

   - System SNMP Alerts: ``No``

   - iHealth Snapshot Information: ``No``

   - Facility Name: ``F5 Lab``

   - Default Tenant: ``default``

   - Role Based Access Controls: ``No``

   |image32|

#. Under the **Analytics System Configuration**, enter the following:

   - IP Address or Hostname: ``10.1.20.252``

   - Port: ``8088``

   - Protocol: ``HTTPS``

   - API Key: *<paste the Token Value that you copied from Splunk>*

   Leave other settings at their default values

   |image33|

#. Leave all settings under **Module Log Stream Capture** and **Local
   Logging Capture** sections at their default values

#. Under **Application Mapping**, leave all settings at their default
   values, *except* in the Mapping Table, enter the following:

   - Order: ``10``

   - Type: ``App Name``

   - From: ``Virtual Name``

   - Regex: ``(.*)_HTTP[S]*_VS``

   - Action: ``Map``

   - AppendPrefix: *<leave blank>*

   - DirectMapping: *<leave blank>*

   |image34|

#. Click **Finished**

Task 2 – Generate some traffic for your applications
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Minimize the Chrome browser window, and launch **JMeter** from the
   Desktop shortcut

#. Once the Apache JMeter window opens, go to **File > Open**, and open
   the ``F5_Analytics_Demo.jmx`` file

   |image35|

#. From the JMeter menu bar, click **Run > Start**

.. |image27| image:: /_static/class1/image29.png
   :width: 5.07708in
   :height: 1.54716in
.. |image28| image:: /_static/class1/image30.png
   :width: 4.23681in
   :height: 2.97674in
.. |image29| image:: /_static/class1/image31.png
   :width: 5.00069in
   :height: 0.94376in
.. |image30| image:: /_static/class1/image32.png
   :width: 3.21326in
   :height: 2.01554in
.. |image31| image:: /_static/class1/image33.png
   :width: 4.81743in
   :height: 1.33194in
.. |image32| image:: /_static/class1/image34.png
   :width: 3.59521in
   :height: 2.29461in
.. |image33| image:: /_static/class1/image35.png
   :width: 4.35910in
   :height: 1.54102in
.. |image34| image:: /_static/class1/image36.png
   :width: 5.30972in
   :height: 1.86250in
.. |image35| image:: /_static/class1/image7.png
   :width: 2.93819in
   :height: 2.07318in
