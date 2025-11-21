# About Network Applications
Source: https://help.zscaler.com/zia/about-network-applications
PDF: https://help.zscaler.com/pdf/com/en/1399936.pdf

[Watch a video about Network Applications](https://fast.wistia.net/embed/iframe/uog2xsgkhz)
Network applications are predefined applications maintained by Zscaler based on information in Layer 7 of the OSI model. The Zscaler service can identify network applications dynamically using Deep Packet Inspection (DPI) and control the network application traffic using firewall filtering rules. You can [group network applications](/zia/adding-network-application-groups) but cannot edit or delete them.
Network applications provide the following benefits and allow you to:
- Identify and control predefined network applications using Deep Packet Inspection (DPI).
- Define security policies based on network applications and enforce condition-based allow or block action on your network traffic.
- Group network applications to control them together using the same policies.
You can define firewall filtering rules using network application criteria to identify network applications, and allow or block the traffic. Unlike the evaluation of [network service](/zia/about-network-services) or [application service](/zia/about-application-service-groups) rule conditions that match on the first packet, the DPI used for identifying network applications often requires more than one packet of traffic directed to the destination to be allowed and assessed before it can determine the type of traffic or network application.
If the DPI cannot determine the network application after examining sufficient data, the firewall module matches the assessed packets to a policy action. The policy action is based on the firewall rule evaluation at the base protocol (TCP or UDP), encryption (SSL/TLS) protocol, or high-level protocol (HTTP or HTTPS). If the DPI session terminates unexpectedly (e.g., non-gracefully without a FIN or RST) before it could determine the application by examining sufficient data, then the transactions for the allowed packets are logged with the *Allow due to insufficient app data* action. This also assumes that a higher-ranked firewall rule did not block the base protocol, encryption protocol, or high-level protocol used by the application before the session terminated. However, if the DPI session terminates due to a web policy (e.g., URL Filtering policy or Cloud App Control policy) blocking the traffic, then the transaction is logged using an implicit rule, Blocked by Web Proxy Policy, by the firewall module. Sessions are logged individually using Full Logging with the Block/Drop action and can be viewed in [Firewall Insights Logs](/zia/firewall-insights-logs-columns). The full details of these sessions are available in [Web Insights Logs](/zia/web-insights-logs-filters).
Zscaler recommends the following best practices when configuring firewall filtering rules with network applications criteria:
- If you configure a rule with network applications as the only condition, place the rule in a lower order than rules where a first packet match is possible (i.e., rules based on network services, application services, destination IP addresses, users, etc.). This way of ordering is crucial when you have block rules that support a first packet match. These rules must be of a higher order than the network application-based rules to prevent packets from being allowed unnecessarily from traffic that would have been otherwise blocked. Additionally, it ensures that only a subset of all traffic flows is examined for network application identification.
- If network applications are part of a higher-order rule, ensure that network applications are combined with other conditions (e.g., users, network services, and destination IP addresses) to make the rule qualify for a limited number of traffic flows or sessions. E.g., combining the destination IP address with network applications criteria so the DPI is used to identify only network applications destined for that IP address.
- Advanced Firewall is required to identify and control network application traffic using DPI.
- Zscaler provides a predefined Office 365 application group to facilitate rule creation for Microsoft Office 365 apps. To view or edit the applications in the group, see [About Network Application Groups.](/zia/about-network-application-groups)
About the Network Applications Page
On the Network Applications page (Administration > Network Applications), you can do the following:
- View a list of all network applications. For each application, you can view and sort:
- **Name**: The name of the network application.
- **Category**: The category to which the network application belongs.
- **Description**: A brief description of the application.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- Search for a network application.
- Go to the [Network Application Groups page](/zia/about-network-application-groups).
- Go to the [DNS Application Groups page](/zia/about-dns-application-groups).
![Network Applications page](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policy-resources/about-network-applications/network-application.png)