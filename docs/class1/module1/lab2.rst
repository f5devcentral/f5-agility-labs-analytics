Lab 2: Understanding the setup
------------------------------

While you wait for the traffic to be generated and sent to the BIG-IPs,
and for AVR to gather and analyze the data, let us use this time to
explore the setup we have.

JMeter – Generating the user traffic
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Apache JMeter is a traffic generator that we are using in this lab in
order to simulate user traffic, since we do not have any actual traffic
hitting our applications or BIG-IPs. In your own environment, you
probably would not need to use JMeter, since you presumably have actual
users accessing your applications through your BIG-IP devices.

AVR Module – Analyzing the user data. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Application Visibility and Reporting (AVR) module is a built-in
module that is available on all BIG-IP platforms starting software
version 11.x onwards. This is a special module that does not need a
separate license (it is included by default). However, it does need to
be provisioned as a module on your BIG-IP in order to use it. You can
verify that we have the module provisioned on our BIG-IPs by going to
the BIG-IP GUI (in the Chrome browser), and going to **System > Resource
Provisioning**, and verifying that AVR is provisioned (check marked
under the **Provisioning** column). In your own environment, you will
need to provision the AVR module on your BIG-IPs before you can use it.
Note that provisioning (or de-provisioning) any module will re-start
some services on the BIG-IP, which could disrupt some traffic, hence you
may want to only do so during a maintenance window.

BIG-IP Virtual Servers – randomizing the client source IPs and User Agents
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Since we do not have actual user traffic in the lab environment, we have
setup the lab to simulate traffic originating from several different
client source IP addresses and HTTP User Agent strings. This allows us
to get some more interesting reports for Analytics. The way this is
accomplished is by using "proxy" Virtual Servers
(``Src_IP_Randomizer_HTTP`` / ``Src_IP_Randomizer_HTTPS``) which
intercept the incoming traffic from the Win7\_Client, change the source
IP to a randomly chosen IP address, and then forward the request to the
actual application Virtual Server that will process the traffic. The
application Virtual Servers (``F5_Demo_HTTP_VS`` /
``F5_Demo_HTTPS_VS``) then further change the HTTP ``User-Agent`` header to
a randomly chosen value before forwarding the request to the pool member
(application web server). All of this is accomplished via iRules
attached to these Virtual Servers. We encourage you to take a look at
how the whole setup works by going to **Local Traffic > Network Map.**
Look at the configuration for the virtual servers named
``Src_IP_Randomizer_HTTP/HTTPS``. There is just a simple iRule
(``Src_IP_Randomizer_/HTTP / _HTTPS``) attached to these. Click on the
iRule name to view its details. Similarly, view the
``Src_UA_Randomizer`` iRule attached the application Virtual Servers.
Ask the instructor if you would like help understanding how these iRules
work.

In order to see all this in action, open a new tab in the Chrome browser
window, and click on either the **Demo1** (HTTP) or **Demo2** (HTTPS)
bookmarks in the browser bookmark bar. When the page loads, scroll down
to the **HTTP Request and Response Information** section and click the
link for **Request and Response Headers**. Now refresh this page several
times (``Ctrl-Shift-R``), and observe the ``Client IP address/port``
field and the ``User-Agent`` field displayed on the page, and notice how
they change every time you refresh the page.

.. NOTE:: In your own environment, you will not need to use these tricks
   to change the client Source IPs and User Agent strings, since you would
   presumably have traffic from actual users originating from different IP
   addresses and using different HTTP User-Agent strings.
