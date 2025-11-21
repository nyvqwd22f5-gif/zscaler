# About Probes
Source: https://help.zscaler.com/unified/about-probes
PDF: https://help.zscaler.com/pdf/com/en/1492836.pdf

Probes log data pertaining to certain aspects of applications in your organization. Predefined applications have preconfigured probes onboarded with them by default, while custom applications require probes to be manually created. At least one Web probe is required to enable most applications. However, only one Cloud Path probe is required for a Network application. To learn more, see [About Applications](/unified/about-applications-0) and [Monitoring Applications](/unified/monitoring-applications-overview).
If you click an application name, the Applications Dashboard is displayed. The tables and charts within the page are pre-filtered to include data and ZDX Scores specific to the probes associated with that application. To learn more, see [About the ZDX Score](/unified/about-zdx-score) and [Monitoring Applications](/unified/monitoring-applications-overview).
Supported Probe Types
The probe types Digital Experience Monitoring supports are Web probes and Cloud Path probes.
Web Probes
Web probes always pull objects from the server and do not do any local caching. They are used to collect the following metrics:
- Page Fetch Time: This metric collects the network fetch time of the web page from the URL-specified Web probe. It requests only the top-level page document and does not request all embedded links within the web page. This provides users with a metric similar to other developer tools.
- DNS Time: This metric represents the time it took to resolve the DNS name for the hostname specified in the Web probe URL.
- Server Response Time: Time to First Byte (TTFB).
- Availability (based on the HTTP Response code): If a success code is returned, the availability is either 1 or 0. If the probe times out, the availability defaults to 0.
The Secure Sockets Layer (SSL) policies configured for your organization do not apply to Digital Experience Monitoring synthetic Web probes, though all other policies applicable to regular traffic are applied. This exception is to enable the caching of responses, without which the destination servers would experience an excessive surge of probe requests that might consume their resources. To learn more about this feature, see [About SSL Inspection](/zia/about-ssl-inspection).
Cloud Path Probes
Cloud Path is used to provide a summarized path visualization between the hop points of traffic. It can provide visualization for the case of a direct traffic path, as in Zscaler Client Connector to egress to destination, as well as tunneling through an Internet & SaaS Public Service Edge (i.e., Zscaler Client Connector to egress to Internet & SaaS Public Service Edge to destination).
[See image.](#DirectPath)
If the hop is unreachable, it is considered unknown and shows in the path as a dotted arrow.
[See image.](#ZENPath)
Cloud Path probes are used to collect the following metrics:
- Hop Count: The number of hops between each hop point on the path.
- Packet Loss: The % of packet loss at each hop point on the path.
- Latency (Average, Minimum, Maximum, and Standard Deviation): The roundtrip path time measured in milliseconds.
About the Probes Page
On the Probes page, you can do the following:
-
[Add a new probe](/unified/configuring-probe). An application can have more than one probe, each with its own set of criteria.
A Web probe and Cloud Path probe are automatically enabled by default when you onboard a predefined application. The **Add New Probe** link is disabled if you've reached the maximum number of allowed applications or probes for your subscription level. To learn more about application and probe limits, see [Ranges & Limitations](/unified/ranges-limitations#digital-experience#applications-probes).
- [Edit](/unified/editing-probe) or copy a probe. You can delete a custom probe, but you cannot delete a probe associated with a predefined application. Cards for disabled probes are shown entirely in gray.
- Search for probes. To quickly locate a probe, you can filter the page by user groups, applications, probe statuses, location groups, departments, devices, users, and Zscaler locations. Filters applied on this page do not carry over to the User Overview dashboard, and vice versa.
- Go to the [Applications](/unified/about-applications-0) page to view and manage predefined and custom applications in your organization.
![Probes page](/downloads/zdx/configuration/probes/about-probes/zdx-probes-page-filters2.png)
[]![Traceroute Direct Path Visualization](/downloads/zdx/configuration/probes/about-probes/TR-path-direct-case.png)
[]![Traceroute ZEN Path Visualization](/downloads/zdx/configuration/probes/about-probes/TR-traffic-through-ZEN%2BUnknown-Hops.png)