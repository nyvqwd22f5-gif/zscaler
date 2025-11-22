# About Network Service Groups for Internet & SaaS
Source: https://help.zscaler.com/unified/about-network-service-groups-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1494141.pdf

You can group predefined and custom network services together for use in policies.
Network service groups provide the following benefits and enable you to:
- Group network services into a single entity to manage them collectively in security policies.
- Configure 5-tuple firewall rules, NAT rules, IPS Control policies, and forwarding rules based on network service groups and enforce condition-based actions to allow, block, or redirect your network traffic.
Network services configured in Zscaler are identified at the first packet, leading to immediate policy action. In contrast, multiple packets are typically required by deep packet inspection to identify network applications before a policy action can take place. Therefore, Zscaler recommends that you rank firewall filtering rules for network service groups higher than rules for network applications to prevent packets from being allowed unnecessarily from traffic that would otherwise be blocked by rules using first-packet identification. To learn more, see [About Network Applications](/unified/about-network-applications).
About the Network Service Group Page
On the Network Service Group page (Policies > Access Control > Firewall > Network Services > Service Groups), you can do the following:
- [Add a network service group](/unified/configuring-network-service-groups).
- View a list of all network service groups. For each group, you can view:
- **Name**: The name of the network service group. You can sort this column.
- **Services**: The network services included in the group.
- **Description**: The description of the group, if available. You can sort this column.
- Search for a network service group.
- [Modify the table and its columns](/unified/using-tables).
- Edit a network service group.
- Go to the [Network Services page](/unified/about-network-services).
![Network Service Groups page](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policy-resources/about-network-service-groups/network-service-groups_0.png)