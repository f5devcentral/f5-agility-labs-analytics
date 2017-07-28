Lab 1: Configuring AVR to generate on-box Analytics reports
-----------------------------------------------------------

In this lab, you will first configure an Analytics profile to attach to
your existing applications (Virtual Servers), and then generate some
traffic for these applications. You will then view the analytics graphs
and charts on the BIG-IP to gain more insight into the traffic patterns
for incoming traffic for your applications.

You will perform all configuration tasks from the Windows jump box

On the Windows Jump box, open the Chrome browser, and then use the
bookmark in the bookmark bar to access **BIGIP\_A**.

Login to the BIG-IP with these credentials:

Username: ``admin``

Password: ``AgilityLab17``

Task 1 – Create a new Analytics profile and attach it to your Virtual Servers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Go to **Local Traffic > Profiles > Analytics > HTTP Analytics**.

   |image0|

#. Click **Create**

#. Click the **Custom** checkbox in the top-right

#. Type in ``Custom_HTTP_Analytics`` for the **Profile Name**

   |image1|

#. Under the **Statistics Gathering Configuration,** checkmark the
   following options:

   - **Max TPS and Throughput**

   - **URLs**

   - **Countries**

   - **Client IP Addresses**

   - **User Agents**

#. Leave **Response Codes** and **Methods** check-marked

#. Click **Finished**

   |image2|

#. Go to **Local Traffic > Virtual Servers**

#. Click on **F5\_Demo\_HTTPS\_VS**

#. Use the pull-down menu to change the **Configuration** from **Basic**
   to **Advanced**

   |image3|

#. Scroll down and change the **HTTP Analytics Profile** from **None**
   to **Custom\_HTTP\_Analytics**

   |image4|

#. Click **Update** at the bottom to save the Virtual Server
   configuration

#. Repeat Steps 8 – 12 for the **F5\_Demo\_HTTP\_VS** as well.

Task 2 – Generate some traffic for your applications
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Minimize the Chrome browser window, and launch **JMeter** from the
   Desktop shortcut

#. Once the Apache JMeter window opens, go to **File > Open**, and open
   the **F5\_Analytics\_Demo.jmx** file

   |image5|

#. From the JMeter menu bar, click Run > Start

.. |image0| image:: /_static/class1/image2.png
   :width: 3.52847in
   :height: 3.68861in
.. |image1| image:: /_static/class1/image3.png
   :width: 4.69514in
   :height: 0.86460in
.. |image2| image:: /_static/class1/image4.png
   :width: 4.92431in
   :height: 1.64165in
.. |image3| image:: /_static/class1/image5.png
   :width: 4.23681in
   :height: 1.00351in
.. |image4| image:: /_static/class1/image6.png
   :width: 4.38958in
   :height: 1.20734in
.. |image5| image:: /_static/class1/image7.png
   :width: 2.93819in
   :height: 2.07318in
