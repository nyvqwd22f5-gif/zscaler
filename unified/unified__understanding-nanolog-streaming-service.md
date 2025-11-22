# Understanding Nanolog Streaming Service (NSS)
Source: https://help.zscaler.com/unified/understanding-nanolog-streaming-service
PDF: https://help.zscaler.com/pdf/com/en/1496616.pdf

Zscaler's Nanolog Streaming Service (NSS) is a family of products that enable Zscaler cloud communication with third-party security solution devices for exchanging event logs.
Log Streaming
This provision allows streaming of all logs from the Zscaler Nanolog to your security information and event management (SIEM) system with the following offerings:
- **Virtual machine (VM)-based NSS**: Uses a VM set within your network to stream logs to your SIEM over a raw TCP connection.
- **Cloud NSS**: Uses an HTTPS API feed to push logs to an HTTPS API-based log collector on your SIEM.
Through SIEM integration, you can leverage VM-based NSS or Cloud NSS to enable real-time alerting on security events of your choice, correlate Zscaler's logs with the logs from your other devices, and locally set up long-term log archival.
To learn more, see:
- [About VM-based NSS](#vm-based-nss-deployment)
- [About Cloud NSS](#cloud-nss)
- [Comparison between VM-based NSS and Cloud NSS](#comparison-table)
Log Collection
This provision allows for near real-time log collection from third-party vendors' firewall and web proxy devices inside your network perimeter and streaming of the logs to the Zscaler cloud by using the [NSS Collector](/unified/about-nss-collector-servers). The log data collected from third-party security solutions is integrated with Zscaler’s unified console to provide a comprehensive [Shadow IT Report](/unified/about-shadow-it-report) for a broad range of cloud application discovery and analysis.
The NSS Collector functionality and the data collected using this functionality are exclusive to Shadow IT Report. To enable this feature for your organization, contact Zscaler Support.
To learn more, see:
- [About NSS Collector](#nss-collector)
[]The NSS uses a virtual machine (VM) to stream logs to your SIEM. You can [deploy the NSS](/unified/deploying-nss-virtual-appliances) VM via vSphere, Amazon Web Services, or Microsoft Azure. Zscaler offers the following NSS subscriptions:
- **NSS for Web**: Streams web and mobile traffic logs.
- **NSS for Firewall**: Streams logs from the Zscaler Firewall.
As shown in the following diagram, the web and Firewall logs are stored in the Nanolog in the Zscaler cloud. When you deploy one NSS for web and another for Firewall logs, each NSS opens a secure tunnel to the Nanolog in the Zscaler cloud. The Nanolog then streams copies of the logs to each NSS in a highly compressed format to reduce bandwidth footprint. The original logs are retained in the Nanolog.
When an NSS receives the logs from the Nanolog, it decompresses and detokenizes them, applies the configured filters to exclude unwanted logs, converts the filtered logs to the configured output format so that they can be consumed and parsed by your SIEM, and then streams the logs to your SIEM over a raw TCP connection.
![Diagram of the VM-based Nanolog Streaming Service, which streams web and Firewall logs from the Zscaler Nanolog to your SIEM system](/downloads/zia/nanolog-streaming-service/understanding-nanolog-streaming-service/zia_nss_vm_diagram.png)
As part of VM-based deployment, you add NSS servers and configure NSS feeds in the Admin Portal to specify the data that the NSS sends to your SIEM. To learn more, see [About NSS Servers](/unified/about-nss-servers) and [About NSS Feeds](/unified/about-nss-feeds).
After deployment, the NSS requires minimal administration and automatically polls the Zscaler service for updates and installs them. For monitoring purposes, you can [configure a separate feed for NSS alerts](/unified/adding-nss-feeds-alerts). The service sends the alerts in an [RFC-compliant Syslog format](/unified/syslog-overview) to the specified IP address and port.
The NSS has the following reliability mechanisms:
- **NSS to SIEM**: The NSS buffers the logs in the VM memory to increase its resiliency to transient network issues between the SIEM and the NSS. If the connection drops, the NSS replays logs from the buffer, according to the Duplicate Logs setting.
- **Nanolog to SIEM**: If the connectivity between the Zscaler cloud and NSS is interrupted, the NSS misses logs that arrived at the Nanolog cluster during the interruption, and they are not delivered to the SIEM. When the connection is restored, the NSS one-hour recovery allows the Nanolog to replay logs up to one hour back.
Additionally, if you have [Advanced Sandbox](/unified/about-sandbox), you can open a [Sandbox Detail Report](/unified/viewing-sandbox-reports-and-data) based on the MD5 parameter that you retrieve from your logs in the SIEM.
[]About NSS Deployment Guides
The following guides detail the requirements and steps to deploy NSS via the appropriate platform:
- [NSS Deployment Guide for Amazon Web Services](/unified/nss-deployment-guide-amazon-web-services)
- [NSS Deployment Guide for Google Cloud Platform](/unified/nss-deployment-guide-google-cloud-platform)
- [NSS Deployment Guide for Microsoft Azure](/unified/nss-deployment-guide-microsoft-azure)
- [NSS Deployment Guide for VMware vSphere](/unified/nss-deployment-guide-vmware-vsphere)
[]You can optionally subscribe to Cloud NSS, enabling direct cloud-to-cloud log streaming for all [log types](/unified/adding-cloud-nss-feeds) into a compatible cloud-based SIEM without any on-premises connectors. Zscaler offers Cloud NSS for Web and Cloud NSS for Firewall subscriptions.
Instead of deploying, managing, and monitoring NSS VMs, you can configure an HTTPS API feed to push logs from the Zscaler cloud into an HTTPS API-based log collector on your SIEM. As a result, you can focus on meaningful log analysis activities (e.g., detection, hunting, investigation, alerting), rather than the administration of logging infrastructure.
![Diagram of Cloud NSS, which enables direct cloud-to-cloud log streaming without any on-premises connectors](/downloads/zia/nanolog-streaming-service/understanding-nanolog-streaming-service/zia_cloud_nss_diagram.png)
Cloud NSS supports a customizable HTTPS outbound connector, allowing interoperability with most private and public cloud-based SIEMs that support a stateless log ingestion API. Zscaler can `POST` batches of logs if the SIEM exposes a publicly routable HTTPS log collection API (e.g., Splunk HTTP Event Collector). HTTPS is the more reliable and preferred approach for log delivery over the internet.
If the connection between the Nanolog cluster and the SIEM is interrupted, logs are not delivered to the SIEM. When the connection is restored, the Cloud NSS one-hour recovery, provided by a separate Zscaler capability, allows the Nanolog to replay logs up to one hour back.
You can create one Cloud NSS feed per log type per Cloud NSS instance. When configuring a Cloud NSS feed, you can customize the feed format; Zscaler recommends using JSON. To learn more, see [About Cloud NSS Feeds](/unified/about-cloud-nss-feeds).
After deployment, you have access to continuous monitoring and alerting with Zscaler CloudOps.
To learn more about the geo-availability and qualifications for Cloud NSS, contact Zscaler Support.
[]The following table summarizes the benefits, limitations, and requirements of the offerings:
-
-
-
-
-
[](/unified/adding-nss-feeds)[](/unified/adding-nss-feeds-web-logs)[](/unified/adding-nss-feeds-firewall-logs)[](/unified/deploying-nss-virtual-appliances)
-
-
-
-
[](/unified/adding-cloud-nss-feeds)
|  | **Benefits** | **Limitations** | **Requirements** |
| --- | ------------ | --------------- | ---------------- |
| VM-based NSS | Operates with minimal administration after deployment.Automatically polls the Zscaler service for updates and installs them.Supports a customizable feed format.Supports a separate alerts feed for monitoring purposes.Buffers logs in the VM memory for increased resiliency. | Supports up to 16 NSS feeds per NSS server. (Web and Firewall logs are each limited to 8 feeds per server to ensure optimal performance.) | Requires a virtual appliance for deployment. To learn more, see Deploying NSS Virtual Appliances. |
| Cloud NSS | Operates without an additional VM within your network.Supports a customizable HTTPS outbound connector, allowing interoperability with most SIEMs.Supports a customizable feed format (JSON recommended).Includes CloudOps 24/7 monitoring and alerting. | Supports one Cloud NSS feed per log type per Cloud NSS instance. | Requires a separate concurrent subscription. To learn more, contact Zscaler Support. |
[]The NSS Collector collects traffic logs from third-party syslog feeds, processes the log data, and securely pushes the logs to the Zscaler cloud over HTTPS. The NSS Collector requires a subscription to the NSS VM or Cloud NSS. The NSS Collector must be deployed on VMware within your organization’s network perimeter. The deployment involves installing the NSS Collector server using the [packaged software](/unified/adding-nss-collector-servers) (VM image) obtained from the Admin Portal and configuring the client certificate issued by Zscaler for the NSS Collector server.
The following illustration shows the NSS Collector’s deployment and workflow used in the third-party log integration with Zscaler:
![A diagram of log collection from third-party security devices using NSS Collector](/downloads/zia/nanolog-streaming-service/understanding-nanolog-streaming-service/zia_nss_collector_diagram.png)
When the NSS Collector service is started, it listens on a fixed port configured on your firewall to forward the logs. The firewall must also be configured to use a syslog feed format for forwarding logs to the NSS Collector’s IP address and predesignated port. The NSS Collector can collect the syslog feeds from one or many firewall devices in the CEF format over a TCP connection. Upon receiving the logs, the NSS Collector performs the following actions to process the log data:
- Resolves user information based on integration with IdP. Unmanaged Zscaler users are categorized as Unidentified Users.
- Resolves the URL information to facilitate cloud application discovery and analysis by Zscaler.
- Securely transmits processed log data to the Zscaler cloud over HTTPS.
The third-party device logs are processed by Zscaler and retained for 6 months. This data is integrated with Zscaler and is made available for cloud application discovery and analytics through the Shadow IT Report.
The NSS Collector maintains a one-hour buffer to ensure no data loss due to communication issues with the Zscaler cloud or during maintenance procedures. If the connection between the NSS Collector and the Zscaler cloud is disrupted, the NSS Collector buffers the third-party firewall or web proxy logs and sends them when the connection is re-established. To learn about the amount of memory required to buffer the logs, see the [prerequisites in NSS Collector Deployment Guide for VMware vSphere](/unified/nss-collector-deployment-guide-vmware-vsphere#step1-prerequisites). The buffer size increases proportionally to the amount of RAM allocated to the NSS Collector.
- An organization can have up to 4 NSS Collector servers.
- The NSS Collector does not support historical load from the source. Records older than one hour are dropped from the stream.
The NSS Collector restricts the log events streaming to the Zscaler cloud to 10K events per second. Events that exceed the rate limit are dropped.
About NSS Collector Deployment Guides
To learn more about the requirements and steps to deploy the NSS Collector via the VMware vSphere platform, see [NSS Collector Deployment Guide for VMware vSphere](/unified/nss-collector-deployment-guide-vmware-vsphere).