# Maintenance Support for Virtual Service Edge
Source: https://help.zscaler.com/zia/maintenance-support-virtual-service-edge
PDF: https://help.zscaler.com/pdf/com/en/1417031.pdf

ZIA Virtual Service Edges are installed in an organization’s data center and are dedicated to the organization’s traffic, but they are managed and maintained by Zscaler Cloud Operations. Zscaler maintains the Virtual Service Edges with a near zero touch needed from your organization.
The Zscaler Operations team performs the following tasks on an organization's Virtual Service Edges:
- Updates the Service Edges to maintain the operational standards of Zscaler. It is the organization's responsibility to install and run the virtual machine (VM).
- Alerts organizations when Zscaler requires their assistance, such as when the Service Edge VM needs to be rebooted.
- Maintains the technical refresh status of the Service Edge.
- Provides periodic remote management of the Service Edge, including remote updates of software and security feed updates on a schedule in conformance with the standard release and maintenance practices of Zscaler.
Organization's Responsibilities
For Zscaler Operations to service, manage, and maintain the Service Edges and ensure their smooth operation, Zscaler requires that the organization:
- Provide network access to Zscaler.
- Monitor the Virtual Service Edge using supported [SNMP MIBs](/zia/about-the-zscaler-snmp-mibs) to determine the health of the device in the organization’s environment.
- Provide a continuous, uninterrupted, and suitable power supply to the host that is running the VM.
- Ensure that each Service Edge has internet connectivity.
- Notify Zscaler of any maintenance or scheduled periods that could impact the ability of Zscaler to establish connectivity to the Service Edge.
- Ensure that Virtual Service Edge has sufficient compute and memory resources allocated to it, as notified by Zscaler.
- Ensure that only Zscaler staff access or service the Virtual Service Edge. The organization or any third party should refrain from making any repair attempts or other changes to the Virtual Service Edge unless they have explicit approval from Zscaler.
- Ensure that someone can respond 24/7 to requests from Zscaler, in case there is an issue with your organization's data center.
- Manage all network-related issues.
- Ensure that the Service Edges are installed and operated in accordance with the specifications and recommendations provided by Zscaler.
- Comply with the [firewall configuration requirements](/zia/firewall-configuration-requirements-for-private-service-edge-deployments), if you use a firewall to control access to the products on the Service Edges.
- Connect the Service Edges to the appropriate network resources recommended by Zscaler and provide them with the necessary IP addresses to run the service.
- Periodically make and store, in a safe place, archival copies of valuable data residing on or affected by the operation or malfunction of the Service Edge.
In the event of software failure, your organization can contact Zscaler Support. Zscaler works with your organization to validate and troubleshoot the software failure.