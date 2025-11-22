# About DNS Gateways
Source: https://help.zscaler.com/cloud-branch-connector/about-dns-gateways
PDF: https://help.zscaler.us/pdf/com/en/1471251.pdf

DNS gateways provide the ability to redirect the DNS request received by the Cloud or Branch Connector to specific DNS servers.
DNS Gateways provide the following benefits and enable you to:
- Ensure the high availability of the DNS service used by your organization by configuring primary and secondary DNS services.
- Ensure compliance with regulatory and contractual requirements like employing Protective DNS service.
To use DNS gateway and policy functionalities, design your network where workloads, servers, and endpoints are deployed to route DNS queries through the Cloud or Branch Connector.
About the DNS Gateway Page
On the DNS Gateway page (Administration > Gateways), you can do the following:
- [Add a DNS gateway](/cloud-branch-connector/configuring-dns-gateway).
- View a list of all gateways. For each gateway, you can view:
- **Gateway Name**: The name of the gateway. You can sort this column.
- **Primary Proxy**: The primary proxy for the gateway.
- **Secondary Proxy**: The secondary proxy for the gateway.
- **Failure Behavior**: The failure behavior for the gateway (i.e., **Return error response** or **Forward to Original DNS Server**).
-
View a list of predefined gateways created by Zscaler. They are disabled by default, but you can enable them:
- **LAN CTR**: The LAN Customer Trusted Resolver (CTR) has DNS servers configured in the LAN section of the [branch configuration template](/cloud-branch-connector/configuring-branch-configuration-template).
- **WAN CTR**: The WAN CTR has DNS servers, which are either manually configured or received by DHCP protocol, configured in the WAN section of the [branch configuration template](/cloud-branch-connector/configuring-branch-configuration-template).
Predefined gateways are only applicable to hardware devices deployed in gateway mode.
- [Edit](/cloud-branch-connector/editing-deleting-or-duplicating-items) a DNS gateway. You cannot edit predefined DNS gateways.
-
[Delete](/cloud-branch-connector/editing-deleting-or-duplicating-items) a DNS gateway.
You cannot delete the default DNS gateway.
- View a DNS gateway and its details.
- Modify the table and its columns.
- Search for a gateway.
- Go to the [ZIA Gateway](/cloud-branch-connector/about-zia-gateways) page.
- Go to the [Log and Control Gateway](/cloud-branch-connector/about-log-and-control-gateways) page.
![The DNS Gateway page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/forwarding-methods/about-dns-gateways/AboutDNSGateways.png)