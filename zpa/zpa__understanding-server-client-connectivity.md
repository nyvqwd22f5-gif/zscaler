# Understanding Server-to-Client Connectivity
Source: https://help.zscaler.com/zpa/understanding-server-client-connectivity
PDF: https://help.zscaler.com/pdf/com/en/1485581.pdf

This feature is in limited availability. To learn more, contact Zscaler Support.
In addition to connecting users to private applications, Zscaler Private Access (ZPA) also supports connecting users to other ZPA-enabled devices for remote assistance.
Enabling server-to-client connectivity allows applications on your internal servers to connect through Branch Connectors and Cloud Connectors to endpoints running Zscaler Client Connector. This supports use cases such as remote troubleshooting and software distribution. Server-to-client connectivity allows you to connect to an end user's machine using a Zscaler IP address or FQDN from servers that don't have Zscaler Client Connector installed. This differs from the [client-to-client](/zpa/about-client-based-remote-assistance) approach where the connectivity is between two endpoints running Zscaler Client Connector. A Zscaler IP, which is a virtual IP address maintained by Zscaler, makes any end user's machine reachable via the Cloud or Branch Connectors for server-to-client connectivity. To learn more, see [About Client Connector IP Assignment](/zpa/about-client-connector-ip-assignment).
The following diagram shows the network flow for server-to-client connectivity.
![​​​​Server-to-client connectivity flow chart diagram](/downloads/zpa/administration/peer-peer-connectivity/understanding-server-client-connectivity/zpa-server-to-client-diagram.png)
If you are leveraging virtual Zscaler IP-based connectivity:
- A client or endpoint enrolls in peer-to-peer connectivity when [validating a client hostname](/zpa/validating-client-hostname).
- Zscaler assigns a virtual Zscaler IP address from the configured IP range (e.g., 192.168.254.0/24). You can then download the IP assignment details as a CSV file. To learn more, see [About IP Bindings](/zpa/about-ip-bindings).
- The cloud applications or on-premises applications initiate connectivity to the client over the virtual Zscaler IP address (192.168.254.0/24) on a specific port (e.g., 445).
- Cloud or Branch Connector (as applicable and based on your policy criteria) intercepts these outgoing requests from the applications and forwards them to the Zscaler cloud for connectivity to the client or endpoint.
You can also achieve the virtual IP-based connectivity workflows using FQDN connectivity, depending on how your tools connect with the endpoints.
To successfully enable server-to-client connectivity, the end user must:
- Have [Zscaler Client Connector](/z-app/downloading-zscaler-app#zia-admin-portal) on their device with ZPA enabled.
- Deploy a Cloud or Branch Connector. To learn more, see [Zscaler Cloud and Branch Connector Help](/cloud-branch-connector/getting-started).
- If you are deploying Cloud or Branch Connector specifically for server-to-client connectivity through an FQDN, Zscaler recommends you configure conditional DNS forwarding so only the DNS requests from the applications requiring server-to-client connections are forwarded to the Cloud or Branch Connector.
- Update routing to ensure the Zscaler IP ranges traverse the Cloud or Branch Connector (e.g., 100.64.0.0/16 gateway = BranchConnectorGroup1).
- Define Zscaler virtual IP ranges or subnets along with the location attribute in ZPA that is assigned to Zscaler Client Connectors. The IP address or subnet is then assigned to Zscaler Client Connector from the defined IP ranges.
- Configure application segments and access policies in ZPA either with FQDNs of endpoints or virtual IP ranges or subnets that are assigned to Zscaler Client Connector.
The admin then uses their third-party tool (i.e., Microsoft Configuration Manager) to launch remote assistance to workstations by using the FQDNs or virtual Zscaler IP addresses. The Cloud or Branch Connector then forwards these requests to the ZPA cloud to begin connections with Zscaler Client Connector. Zscaler Client Connector then completes the connection and sends the request back to the server. To learn more, see [Configuring Server-To-Client Connectivity](/zpa/configuring-server-client-connectivity).
The following functions and features are not supported for server-to-client connectivity based on the virtual Zscaler IP:
- [Configuring a forwarding profile action for ZIA](/client-connector/configuring-forwarding-profiles-zscaler-client-connector#forwarding-profile-action-zia) using DTLA
- [Disaster Recovery](/zpa/understanding-disaster-recovery)
- [Machine Tunnels](/zpa/deploying-machine-tunnels-pre-windows-login)
- [Microtenants](/zpa/about-microtenants)
- [Zscaler Client Connector Support for Multiple Tenants](/zpa/about-client-connector-support-multiple-tenants). This limitation applies if those tenants correspond to partner tenants, or when a user is logged in to a partner tenant.