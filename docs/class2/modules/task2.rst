Task 2: Import and configure the F5 Analytics iApp template on the BIG-IP
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Open a new tab in your Chrome browser, and click on the bookmark for **BIGIP\_A** to connect to the BIG-IP GUI

#. Login using the following credentials:

   - Username: ``admin``

   - Password: ``Agility2018``

#. Go to **iApps >> Templates**

#. Click **Import** in the top-right

   |image30|

#. Click **Choose File**

#. Navigate to **Desktop > Analytics Lab Files**, and select the **f5.analytics.v3.7.0.tmpl** file. Click **Open**

   |image31|

#. Click **Upload**

#. Once the file is finished uploading, you should see it listed in the iApp Templates table.

#. Go to **iApps >> Application Services >> Applications**

#. Click **Create** in the top-right

   |image32|

#. For the **Name**, enter ``F5-Analytics``

#. From the **Template** pull-down menu, choose **f5.analytics.v3.7.0**

   |image33|

#. In the template configuration, in the **Welcome to the f5 BIG-IP Analytics iApp Template** section, 
   change the response for the **Do you want to see inline help?** Question to **No, do not show inline help.**

   |image34|

   .. NOTE:: 
        If you are not familiar with what all the different settings refer to, you may want to 
        keep the inline help enabled. For now, we have disabled it just to reduce the amount of 
        additional text on the configuration screen.

#. Under the **Information Sources** section, set the following:

   a) Data Format: **Splunk**

   b) System Statistic: **Yes**

   c) Module High Speed Logging Streams: **Yes**

   d) Local System Logging (syslog): **Yes**

   e) System SNMP Alerts: **No**

   f) iHealth Snapshot Information: **No**

   g) Facility Name: ``F5 Lab``

   h) Default Tenant: ``default``

   i) Role Based Access Controls: **No**

   |image35|

#. Under the **Analytics System Configuration**, enter the following:

   a) IP Address or Hostname: ``10.1.20.252``

   b) Port: ``8088``

   c) Protocol: **HTTPS**

   d) API Key: `<paste the Token Value that you copied from Splunk in the previous task>`

   Leave other settings at their default values

   |image36|

#. Leave all settings under **Module Log Stream Capture** and **Local Logging Capture** sections at their default values

#. Under **Application Mapping**, leave all settings at their default values, *except* in the Mapping Table, enter the following:

   a) Order: ``10``

   b) Type: **App Name**

   c) From: **Virtual Name**

   d. Regex: ``(.*)_HTTP[S]*_VS``

   e. Action: **Map**

   f. AppendPrefix: *<leave blank>*

   g. DirectMapping: *<leave blank>*

   |image37|

#. Click **Finished**

.. NOTE:: 
    It may take up to 10 minutes for the system to start showing data in Splunk.

.. |image30| image:: /_static/images/image30.png

.. |image31| image:: /_static/images/image31.png

.. |image32| image:: /_static/images/image32.png

.. |image33| image:: /_static/images/image33.png

.. |image34| image:: /_static/images/image34.png

.. |image35| image:: /_static/images/image35.png

.. |image36| image:: /_static/images/image36.png

.. |image37| image:: /_static/images/image37.png

