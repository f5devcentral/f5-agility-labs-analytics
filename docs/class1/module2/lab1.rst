Lab 1: Configuring Splunk to use the F5 Splunk app 
--------------------------------------------------

In order to get Splunk to process and display Analytics data from your
BIG-IPs, you need to configure it to accept this data, parse and process
it, and display it in a meaningful way for you to get the most out of
it. In order to help with this, F5 has written a Splunk app that is
available as a free add-on to your Splunk deployment. This F5 Analytics
Splunk app can be downloaded from the Splunkbase web-site here:

`https://splunkbase.splunk.com/app/3161/ <https://splunkbase.splunk.com/app/3161/>`__

For your convenience, we have already downloaded this Splunk app onto
the Windows jump box, so we can just go ahead and install it within our
Splunk instance.

Task 1: Install the F5 Splunk app in Splunk
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. In the Chrome browser on your Windows jump box, click the bookmark
   for **Splunk** to launch the Splunk web UI

#. On the Splunk Enterprise splash page, click **Skip update**

#. In the Splunk Web GUI, click on the settings button next to **Apps**
   (on the left) to **Manage Apps**

   |image11|

#. Click **Install app from file**

   |image12|

#. Click **Choose File**

#. In the file browser window, navigate to **Desktop > Analytics Lab
   Files,** and choose the **f5-networks-analytics-new\_100.tgz file**
   and click **Open**

   |image13|

#. Click **Upload** |image14|

#. Once the upload is complete, you should see the **F5 Networks** app
   listed in the Apps table, with the Status set to **Enabled**

   |image15|

#. Click the **Splunk** logo in the top-left to go to the start page.
   You should now see the **F5 Networks** app listed on the left

   |image16|

#. Now click the **Settings** menu in the top-right, and choose **Data
   inputs**

   |image17|

#. Click on **HTTP Event Collector**

   |image18|

#. Click on **Global Settings** in the top-right

   |image19|

#. In the Edit Global Settings window:

   #. Click on **Enabled** for **All Tokens**

   #. Ensure that **Enable SSL** is checked

   #. Ensure that **HTTP Port Number** is set to **8088**

   #. Click **Save**

   |image20|

#. Click **New Token** in the top-right

#. For the Name, enter **F5-Analytics**, and then Click **Next >** at
   the top

#. On the **Input Settings** page, scroll down till you see **Default
   Index**, and then click the **Create a new index** link

   |image21|

#. In the **New Index** window, enter **f5-default** for the **Index
   Name**, and click **Save**

   |image22|

#. In the **Select Allowed Indexes** table, click **f5-default** to move
   it to **Selected item(s)**

   |image23|

#. Click **Review** at the Top |image24|

#. Ensure your settings match those shown in the screenshot below, then
   click Submit

   |image25|

#. Once your token has been created, highlight the **Token Value** for
   the newly created Token, and copy it to your clipboard (**Ctrl-C** or
   **Right-click > Copy**). We will use this later.

   |image26|

   .. NOTE:: Your token value will be different from the one shown above

#. Click on the **Splunk** logo in the top-left to go back to the Splunk
   start page.

.. |image11| image:: /_static/class1/image13.png
   :width: 1.85325in
   :height: 1.59242in
.. |image12| image:: /_static/class1/image14.png
   :width: 2.37298in
   :height: 1.21504in
.. |image13| image:: /_static/class1/image15.png
   :width: 3.47292in
   :height: 2.42550in
.. |image14| image:: /_static/class1/image16.png
   :width: 1.06121in
   :height: 0.31212in
.. |image15| image:: /_static/class1/image17.png
   :width: 4.69514in
   :height: 1.19421in
.. |image16| image:: /_static/class1/image18.png
   :width: 1.18125in
   :height: 1.57974in
.. |image17| image:: /_static/class1/image19.png
   :width: 4.35910in
   :height: 2.22003in
.. |image18| image:: /_static/class1/image20.png
   :width: 2.29660in
   :height: 2.00804in
.. |image19| image:: /_static/class1/image21.png
   :width: 2.36054in
   :height: 0.43742in
.. |image20| image:: /_static/class1/image22.png
   :width: 4.07437in
   :height: 2.40647in
.. |image21| image:: /_static/class1/image23.png
   :width: 3.24122in
   :height: 2.22299in
.. |image22| image:: /_static/class1/image24.png
   :width: 4.94540in
   :height: 3.12273in
.. |image23| image:: /_static/class1/image25.png
   :width: 4.97622in
   :height: 1.20859in
.. |image24| image:: /_static/class1/image26.png
   :width: 0.55309in
   :height: 0.18609in
.. |image25| image:: /_static/class1/image27.png
   :width: 3.97715in
   :height: 3.30198in
.. |image26| image:: /_static/class1/image28.png
   :width: 3.62317in
   :height: 2.38923in
