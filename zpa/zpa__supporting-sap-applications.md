# Supporting SAP Applications
Source: https://help.zscaler.com/zpa/supporting-sap-applications
PDF: https://help.zscaler.com/pdf/com/en/1484371.pdf

To control access to SAP applications, create application segments and configure DNS search domains.
It's possible to create an application segment with a wildcard and a wide port range to allow broad access to SAP apps. However, it is more secure to create application segments for individual apps.
SAP Login Information
SAP is a collection of applications and databases. When using the SAP client, the connection is made to an SAP message server that returns a list of applications to connect to. After the user selects the application, the SAP client attempts to connect to the hostname or IP address on a specified port.
The SAP messages during the login process provide important context when configuring the ZPA service for use with SAP applications. In the following image, a packet capture was performed during login. This was done using Wireshark with the SAP Dissection plugin. [See image.](#pcap)
[]![Screenshot of a Wireshark packet capture during SAP login](/downloads/zscaler-tech-pubs-style-guide/draft-articles/supporting-sap-applications-0/zpa-sap-pcap-obsc.png)
For each application, the client receives the following information:
- **Client Name**: This is the application name that is displayed in the SAP UI.
- **Host**: This is the hostname of the application.
- **Service**: This is the database or service name in SAP.
- **Message Types**: Details about the record being sent.
- **Host Address v6**: The IPv6 IP address of the service.
- **Host Address v4**: The IPv4 IP address of the service.
- **Service Number**: The TCP Port to connect to.
- **Status**: This is either **Active** or **Disabled**.
In Packet 60 you can see the DNS query response for the initial connection resolving to `10.10.10.XXX` for the SAP message server. The client connects to the SAP message server on TCP 3610 in packet 61 and gets the service list back in packet 69. This is displayed in the bottom pane. The client selects `example0123_A01_01` as their application. This is listed in the bottom pane as `Host: example0123 with Service Number: 3216`. This action results in a connection in packet 74. In this example, there isn't a DNS lookup. This means either it was cached on the client, or (because of the lack of a DNS search suffix) it wasn't resolvable so the client connected to the IP address.
Best Practices
Zscaler recommends the following best practices:
- Create a single application segment for all SAP applications. This will allow the ZPA service to load balance user requests for these applications. However, if segmentation is required, then create multiple application segments for the SAP applications.
- Create application segments for SAP applications using FQDNs. If the SAP client is unsuccessful in resolving the host's FQDN, it will attempt to connect to the IP address. While the service supports IP addresses, it is more secure for zero-trust models to connect with FQDNs.
- If the SAP hostname is not an FQDN, a DNS search domain is required. If the client has no search suffix, it cannot complete the FQDN to connect to SAP. The client will fall back to the IP address provided by the SAP message server, which might not be desirable or routable over the ZPA service.
- Use the Wireshark trace, or SAP configurations, to identify the IP addresses of all SAP servers, and create an application segment which includes only these IP addresses and the appropriate TCP ports. Do not advertise the entire subnet range (e.g., 192.168.1.0/24).
- If there is an access control list (ACL) configured in the SAP message server or application server, add the App Connector IP addresses to it. Since the ZPA service performs a source NAT for the client, all traffic is seen from the IP address of the App Connector. For the [App Connector group](/zpa/about-connector-groups) associated with the application segments, ZPA will load balance user requests across App Connectors in this App Connector group. Because of this, it's recommended that the IP addresses for all the App Connectors in the App Connector group be added to the ACL.
Configuring SAP
Supporting SAP applications in ZPA requires you to configure application segments and DNS search domains.
Step 1: Add an Application Segment
To configure an application segment for SAP applications:
- Go to **Resource Management** > **Application Management** > **Application Segments **> **Defined Application Segments**.
- Click **Add Application Segment**.
The **Add Application Segment** window appears.
- In the **Add Application** window, under **1. Define Applications**:
- For **Applications**:
- Enter a fully qualified domain name (FQDN) that corresponds to the SAP applications. In the example from the packet capture, you would add example0123.company.com.
While it's possible to enter an IP address, Zscaler recommends you use FQDNs wherever possible as it's more secure. If the client has no search suffix, it cannot complete the FQDN to connect to SAP. The client will fall back to the IP address provided by the SAP Message Server.
- For **Zscaler Client Connector Access**:
- **TCP Port Ranges**: Enter the TCP port to connect to. In the example from the packet capture, you would add 3216, as it's the port for the example0123 application.
To learn more about SAP ports, see the [SAP Help Portal](https://help.sap.com/viewer/ports).
- Complete the configuration for the new application as detailed in [Configuring Application Segments](/zpa/configuring-application-segments).
Step 2: Add a DNS Search Domain
For SAP, you can configure DNS Search Domains for FQDNs within the ZPA Admin Portal. This allows the SAP client to append the search suffix and build the FQDN. However, you can also configure SAP to provide an FQDN instead of a short name. Doing this removes the need to configure a DNS Search Domain. To learn more, see this [SAP Note](http://sapsecurity-basis.blogspot.com/2014/04/sap-note-434918-configuration-for-fully.html) and [Adding DNS Search Domains](/zpa/about-applications/dnsDomains).