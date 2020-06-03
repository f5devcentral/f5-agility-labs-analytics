Task 1: Install the F5 Splunk app in Splunk
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. In the Chrome browser on your Windows jump box, click the bookmark for **Splunk** 
   to launch the Splunk web UI

#. On the Splunk Enterprise splash page, if you are prompted for an update, click 
   **Skip update**

#. In the Splunk Web GUI, click on the settings button next to **Apps** (on the left) 
   to **Manage Apps**

   |image14|

#. Click **Install app from file**

   |image15|

#. Click **Choose File**

#. In the file browser window, navigate to **Desktop > Analytics Lab Files,** and 
   choose the **f5-networks-analytics-new\_100.tgz file** and click **Open**

   |image16|

#. Click **Upload** 
   
   |image17|

#. Once the upload is complete, you should see the **F5 Networks** app listed in the 
   Apps table, with the Status set to **Enabled**

   |image18|

#. Click the **Splunk** logo in the top-left to go to the start page. You should now 
   see the **F5 Networks** app listed on the left

   |image19|

#. Now click the **Settings** menu in the top-right, and choose **Data inputs**

   |image20|

#. Click on **HTTP Event Collector**

   |image21|

#. Click on **Global Settings** in the top-right

   |image22|

#. In the Edit Global Settings window:

   - Click on **Enabled** for **All Tokens**

   - Ensure that **Enable SSL** is checked

   - Ensure that **HTTP Port Number** is set to **8088**

   - Click **Save**

   |image23|

   .. NOTE:: 
        Ensure that all of the above settings are exactly as shown, otherwise no data will show up in Splunk.

#. Click **New Token** in the top-right

#. For the Name, enter **F5-Analytics**, and then Click **Next >** at the top

#. On the **Input Settings** page, scroll down till you see **Default Index**, 
   and then click the **Create a new index** link

   |image24|

#. In the **New Index** window, enter **f5-default** for the **Index Name**, and click **Save**

   |image25|

#. In the **Select Allowed Indexes** table, click **f5-default** to move it to **Selected item(s)**

   |image26|

#. Click **Review** at the Top 
   
   |image27|

#. Ensure your settings match those shown in the screenshot below, then click **Submit**

   |image28|

#. Once your token has been created, highlight the **Token Value** for the newly created Token, 
   and copy it to your clipboard (**Ctrl-C** or **Right-click > Copy**). We will use this later.

   |image29|

   .. NOTE:: 
      Your token value will be different from the one shown above

#. Click on the **Splunk** logo in the top-left to go back to the Splunk start page.

.. |image14| image:: /_static/images/image14.png

.. |image15| image:: /_static/images/image15.png

.. |image16| image:: /_static/images/image16.png

.. |image17| image:: /_static/images/image17.png

.. |image18| image:: /_static/images/image18.png

.. |image19| image:: /_static/images/image19.png

.. |image20| image:: /_static/images/image20.png

.. |image21| image:: /_static/images/image21.png

.. |image22| image:: /_static/images/image22.png

.. |image23| image:: /_static/images/image23.png

.. |image24| image:: /_static/images/image24.png

.. |image25| image:: /_static/images/image25.png

.. |image26| image:: /_static/images/image26.png

.. |image27| image:: /_static/images/image27.png

.. |image28| image:: /_static/images/image28.png

.. |image29| image:: /_static/images/image29.png

