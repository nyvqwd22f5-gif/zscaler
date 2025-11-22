# About Network Service Groups for Cloud & Branch Connector
Source: https://help.zscaler.com/unified/about-network-service-groups-cloud-branch-connector
PDF: https://help.zscaler.com/pdf/com/en/1516536.pdf

You can group predefined and custom network services for use in policies.
Network services configured in Zscaler are identified at the first packet, leading to immediate policy action. In contrast, multiple packets are typically required by deep packet inspection to identify network applications before a policy action can take place. Therefore, Zscaler recommends that you rank firewall filtering rules for network service groups higher than rules for network applications to prevent packets from being allowed unnecessarily from traffic that would otherwise be blocked by rules using first-packet identification.
Network applications are available in security policies only. Cloud & Branch Connector forwarding policies are not supported.
Network Service Groups provide the following benefits and enable you to:
- Group multiple network services into a group to use in a single policy.
- Add, remove, or update network services and leverage a single policy for the entire group.
About the Network Service Group Page
On the Network Service Groups page (**Policies **>** Access Control** > **Firewall** > **Network Services** > **Service Groups**), you can do the following:
- [Add a network service group](/unified/configuring-network-service-groups-0).
- View a list of all network service groups. For each group, you can view:
- **Name**: The name of the network service group.
- **Description**: The description of the group, if available.
- **Services**: The network services included in the group.
- Edit a network service group.
- View a network service group.
- Modify the table and its columns.
- Search for a network service group.
- Go to the [Network Services](/unified/about-network-services-0) page.
![Network Service Group page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/firewall-filtering/about-network-service-groups/About%20Network%20Service%20Groups.jpg)