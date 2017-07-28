Lab 3: Viewing the Analytics data
---------------------------------

Task 1: Generate detailed charts and reports to visualize the analytics data
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once we have had some traffic received by the application Virtual
Servers and processed by the Analytics profile, we can now go in and
view and analyze this data.

#. In the BIG-IP GUI, go to **Statistics > Analytics > HTTP > Overview**

   |image6|

#. In the **Override time range to** pull-down menu at the top, change
   the value to **Last Hour**

   |image7|

#. This page now shows you details about the traffic received by all the
   Virtual Servers that had the HTTP Analytics profile attached.

#. You can change the settings of any of the charts/graphs/tables by
   clicking on the **Settings** button on the corresponding widget. You
   can also change the chart type and the time range for any chart by
   clicking the **Chart Type** or **Time Range** menus at the top of any
   widget. You can click on any portion of a chart to view more details
   of the object you clicked on. You can also click the **View Details**
   link in any chart to get a detailed chart.

   |image8|

#. You can move the widgets around and re-arrange the page by simply
   dragging-and-dropping the widgets from the top-left corner of each
   widget. add more widgets on the page by clicking the **Add Widget**
   button at the bottom of the page.

#. Similarly, you can modify the tables on the right side of the page,
   and add another table by clicking the **Add Widget** button below the
   last table on the right.

   |image9|

#. Once you have updated the page to show you the data you want, you can
   create a report by clicking the **Export** button at the top-right of
   the page.

   |image10|

#. We encourage you to explore the different tabs (**Overview,
   Transactions, Latency, Throughput,** etc.) on the page, and change
   the settings on each page to view and analyze the data by various
   metrics.

.. |image6| image:: /_static/class1/image8.png
   :width: 3.93125in
   :height: 1.96563in
.. |image7| image:: /_static/class1/image9.png
   :width: 4.23681in
   :height: 1.42908in
.. |image8| image:: /_static/class1/image10.png
   :width: 4.84792in
   :height: 4.50426in
.. |image9| image:: /_static/class1/image11.png
   :width: 1.18125in
   :height: 0.34107in
.. |image10| image:: /_static/class1/image12.png
   :width: 2.65347in
   :height: 2.34130in
