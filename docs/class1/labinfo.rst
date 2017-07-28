Lab Environment Setup
---------------------

In the interest of time, the following components have been setup with
basic configurations for you:

-  Cloud-based lab environment complete with a Windows client, (2)
   BIG-IP Virtual Editions (VEs), and a Linux Web Server.

-  The Windows client is used as a jump host to access the BIG-IPs as
   well as the Linux server. It also has a traffic generator,
   pre-configured to generate a significant volume of traffic for the
   web applications.

-  The BIG-IP Virtual Editions are running BIG-IP version 12.1.2 (HF2)
   and have been pre-licensed and provisioned for Local Traffic Manager
   (LTM), as well as Analytics Visibility and Reporting (AVR). The
   BIG-IPs have also been paired together in an Active/Standby HA device
   cluster.

-  The Linux server serves up a web application on multiple IP addresses
   (used as pool members on the BIG-IPs). The server is also running an
   instance of Splunk Enterprise version 6.3.9, which is used in the
   latter part of the lab for gathering and visualizing Analytics data
   in Splunk.

Accessing the Lab Environment
-----------------------------

To access the lab environment, you will require a web browser and Remote
Desktop Protocol (RDP) client software. The web browser will be used to
access the Lab Training Portal to retrieve the IP address for your
Windows jump host that you will RDP into to access the entire lab
environment.

#. Connect to the Training Portal (details provided by lab instructor)

#. Retrieve Windows jump box (Win7 Client) IP Address

#. Establish an RDP connection to your jump box with the IP address
   retrieved from Step 2 and login with the following credentials:

   -  User: ``external_user``

   -  Password: ``password``

#. Launch Chrome from the desktop shortcut.

#. Click the bookmark (in the bookmark bar) for BIGIP\_A

#. Login into BIG-IP Configuration Utility with the following
       credentials:

   -  User: ``admin``

   -  Password: ``AgilityLab17``
