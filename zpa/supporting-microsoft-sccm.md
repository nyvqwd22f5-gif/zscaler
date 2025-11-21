# Supporting Microsoft SCCM
Source: https://help.zscaler.com/zpa/supporting-microsoft-sccm
PDF: https://help.zscaler.com/pdf/com/en/1484396.pdf

Organizations use Microsoft System Center Configuration Manager (SCCM) to install updates to devices. SCCM is a client-to-server application that works on a user’s local area network (LAN) or wide area network (WAN) by gathering system configuration and update details from the SCCM server. If there is an update, the SCCM server will direct the client to a distribution point to gather the update information and install the update. To learn more, see the [Microsoft SCCM documentation](https://www.microsoft.com/en-us/cloud-platform/system-center-configuration-manager).
Clients use boundary groups to identify the assigned distribution point where the client can install software. A boundary group is a group of network locations on the intranet. When a client needs to download software based on the boundary group, it contacts a server configured as a distribution point.
Distribution points deliver content to the clients and are used to reduce the WAN traffic, similarly to a content delivery network (CDN). For example, in a location with 100 devices, rather than pulling updates across the WAN, the devices have a distribution point where they receive their updates.
When users are remote, the distribution server is identified as the closest to the point where the client's traffic enters the network. With a traditional VPN, the distribution point is selected based on the client IP address assigned by the VPN gateway. For ZPA, the client is never placed on the network, which means the client never gets an IP address for the data center network. However, it is possible to support SCCM deployments over ZPA.
Use one of the following methods for configuring SCCM boundaries:
- [Boundaries based on Active Directory site names](#activedirectory)
- [Boundaries based on IP subnets and IP ranges](#ips)
The following server-to-client and peer-to-peer Configuration Manager clients and site systems are not supported:
- Configuration Manager console to Client (Remote Assistance - Remote Desktop Protocol)
- Site server to Client (Wake On LAN)
- Client to Client (Wake On LAN)
[]Zscaler recommends using Active Directory sites name for boundaries.
Active Directory sites are detected by a domain-joined device by using DNS SRV record requests. Once the device receives the domain controller IP address, it sends a Lightweight Directory Access Protocol (LDAP) ping to make sure that the domain controller belongs to the same Active Directory site as the device. The LDAP ping does not send the IP address in its header. Hence, the domain controller relies on the source IP address of the packet. For ZPA, the IP address seen by the domain controller is the App Connector's source IP address, which needs to be added to the Active Directory site. To learn more, see [Microsoft LDAP Ping documentation](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-adts/895a7744-aff3-4f64-bcfa-f8c05915d2e9).
Configuring SCCM for Active Directory Site Names
To configure Microsoft SCCM in ZPA:
- Create an [application segment](/zpa/configuring-application-segments)  that contains a wildcard to enable the SRV resolution in ZPA.
- Add the App Connector’s interface IP address to the correct Active Directory site.
Complete this for all App Connectors that require SCCM updates.
- Confirm that the SCCM boundary has the type set to **Active Directory site**.
[]In order for ZPA to function correctly with SCCM, you must configure the IP addresses that users will realistically come from when ZPA is enabled. The user’s device will have a private IP address based on RFC1918 address space since ZPA does not assign an IP address to the client. The SCCM client will report this private IP address as part of the communication to discover the closest distribution point. This means you must create boundaries that cover all RFC1918 addresses (e.g., 192.168.0.0/16, 172.16.0.0/12, 10.0.0.0/8).
If it is not possible to add the RFC1918 address space as a SCCM boundary, another option is to configure [Zscaler Client Connector (Z App)](/z-app/configuring-forwarding-profiles-zscaler-app) with the Tunnel Driver Type as Route Based ([See image](#routebased_img)). If Zscaler Client Connector is configured this way, it will install a virtual network adapter with an IP address in the CGNAT address space. This means adding a SCCM boundary group for RFC6598 100.64.0.0/24.
Configuring SCCM for IP Subnets and IP Ranges
To configure Microsoft SCCM in ZPA:
- Create boundaries for RFC1918 ranges and RFC6598.
- Add the boundaries to a boundary group.
- Assign the boundary group to a distribution point close to your App Connectors.
- Create an [application segment](/zpa/configuring-application-segments) that includes the FQDNs of all the SCCM distribution points.
- Assign the application segment to a server group configured for [Dynamic Server Discovery](/zpa/about-application/onboard#createservergroup).
Ensure that the assigned server groups are only associated with App Connector groups close to the SCCM distribution points.
To learn more about the ports that are used by Configuration Manager clients and site systems for communication, see the [Microsoft SCCM documentation](https://docs.microsoft.com/en-us/sccm/core/plan-design/hierarchy/ports).
[ ] ![Example of Tunnel Driver Set to Route Based](/downloads/zpa/supporting-microsoft-sccm/routebased.png)