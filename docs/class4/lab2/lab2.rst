Exercise 2 - Exporting NGINX Plus spans and metrics using Open Telemetry 
============================================================================

With our application now functioning correctly and delivering trace data to Jaeger, we'll now expand our observability to include our front-end load balancer, (NGINX Plus).  

Configure NGINX tracing
-----------------------

The lab environment includes an NGINX Plus instance that has been configured to publish and provide load balancing to our previously deployed application, (thelabApp).  The application can be reached at *http://10.1.10.4*.  

NGINX uses a configuration file (nginx.conf) to define its behavior, including server blocks, reverse proxy settings, load balancing, security rules, logging, and performance optimizations.  During this exercise, you will modify the *nginx.conf* file to enable the sending of trace information, (*spans*) to Jaeger. 

From the VS Code UI use the navigation pane on the left and open the NGINX Plus configuration file, (*nginx.conf*).  Familiarize yourself with the configuration file contents, (see below).  

.. image:: ../images/Picture39.png
   :alt: Image 39

Several lines related to OTel integration have been "remmed out".  Let's review the lines and remove the leading '#' to enable to line item.

- Line 2 - The [NGINX Open Telemetry module](https://docs.nginx.com/nginx/admin-guide/dynamic-modules/opentelemetry/) has been installed on the lab NGINX instance.  The module provides OTel distributed tracing support and must also be loaded via the NGINX configuration.  Remove the leading '#' to enable loading of the module.

   ![Image](../images/Picture40.png)
   .. image:: ../images/Picture40.png
   :alt: Image 40

- Line 10 - The '*otel_service_name*' directive sets the trace stream's service name.  All spans generated will be categorized and grouped under this service name, (see below). Remove the leading '#' to set the service name.

    ![Image](../images/Picture41.png)

- Lines 11 thru 13 - The '*otel_exporter*' directive block is used to specify the address of the destination service. For this lab, we have specified the locally hosted Jaeger endpoint. Remove the leading '#' to set the export destination.

   ![Image](../images/Picture42.png)
- Line 22 - The '*otel_trace*' directive flag determines whether tracing is enabled. Remove the leading '#' to enable tracing.  

   ![Image](../images/Picture43.png)

- Line 25 - The '*otel_span_name*' directive sets the event span name. Remove the leading '#' to set the span name.
- Line 26 - In additionn to the default attributes provided, the '*otel_span_attr*' directive can be used to assign custom attributes, (key/value). Remove the leading '#' to create a custom span attribute. 
- Line 27 - The '*otel_trace_context*' directive determines how the trace context relates to other traces. Remove the leading '#' to set trace context.

   ![Image](../images/Picture44.png)

With the above noted file lines updated, save the file and use the following command to verify and reload the NGINX configuration:

```sudo nginx -t && sudo nginx -s reload```

Verify NGINX tracing
^^^^^^^^^^^^^^^^^^^^^

Once you have reloaded NGINX, refresh the application (http://10.1.10.4) a few times then return to the Jaeger UI, refresh the page.  From the Jaeger UI select the '*NGINX*' service and search for the latest traces by selecting *'**Find Traces**'*, (see below).

![Image](../images/Picture45.png)

Review the various spans paying special attention to the NGINX span '*LB Frontend call*' tags.  In addition to the default tags provided, you should be able to find the custom span attribute configured via the NGINX configuration file, (see below).

![Image](../images/Picture46.png)

Configure NGINX metrics
-----------------------

The OpenTelemetry Collector service provides a vendor-agnostic proxy to receive, process and export observability data.  The collector supports open-source observability data formats (e.g. Jaeger, Prometheus, Fluent Bit, etc.) sending to one or more open-source or commercial back-ends.

The OTel collector is managed via a user-readable YAML configuration file.  At a minimum, the configuration must include the following three sections:
- **Receivers** - section with information related to how the collector will receive observability data, (i.e. protocols, endpoint addresses, ports) 

- **Processors** - section with configuration information related to data manipulation and insertion.  In this section, one can add/delete/modify data streams using filters.

- **Exporters** - section including information related push or pull based backends/destinations

From the VS Code UI use the navigation pane on the left and open the OTel collector gateway configuration file, (*collector-gateway.yml*).  

The collector provides an integration with NGINX to ingest metrics.  The Collector fetches status metrics from the configured path in the NGINX receiver, (see below). From there the metrics are processed and exported to the specified exporter.  Familiarize yourself with the configuration file contents.  

Specific to this exercise, the collector configuration file, (*example below*)  has been configured to:
 - Pull telemetry from a published NGINX status page
 - Process records using the standard batch processor
 - Export metrics to a Prometheus backend

![Image](../images/Picture18.png)

Before you can pull metrics from NGINX, you must first expose the NGINX status page via the NGINX configuration file.  From the VS Code UI use the navigation pane on the left and open the NGINX Plus configuration file, (*nginx.conf*).

To expose the NGINX status page, navigate down to an remove the leading '*#*' from lines 35 - 37, (see below).

![Image](../images/Picture47.png)

With the above noted file lines updated, save the file and use the following command to verify and reload the NGINX configuration:

```sudo nginx -t && sudo nginx -s reload```

NGINX Metrics
^^^^^^^^^^^^^

Once you have reloaded NGINX, refresh the application (http://10.1.10.4) a few times to generate new traffic.  The NGINX OTel receiver is configured to pull metrics from the NGINX status page every 5 seconds.  Once pulled by th OTel collector, the metrics are processed and delivered to Prometheus for visualization.

If not currently opened, open Google Chrome from the desktop and select the Prometheus tab.  If the tab is no longer visible, the Prometheus UI is located at http://10.1.20.4:9090.

![Image](../images/Picture24.png)

To perform a quick test on the system, select the *Graph* tab and enter '**f5_nginx_requests_total**' in the search bar; click on 'Execute'.  

The system will query metrics for the NGINX requests total metric and return a relevant time chart, (*see below*).

![Image](../images/Picture48.png)

You can now use the metrics explorer to view the available NGINX metrics (*see below*).

![Image](../images/Picture49.png)

This concludes Exercise 2.

---

**Go to [Exercise 3 - Exporting BIG-IP metrics using the OTel consumer](../lab3/lab3.md)**

**Go to [Overview](../overview.md)**