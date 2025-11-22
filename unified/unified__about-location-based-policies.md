# About Location-Based Policies
Source: https://help.zscaler.com/unified/about-location-based-policies
PDF: https://help.zscaler.com/pdf/com/en/1533786.pdf

Location-based policies are rulesets that steer traffic and apply endpoint firewall rules based on a user’s network type (e.g, On-Trusted or Off-Trusted). These rulesets can include inbound and outbound endpoint firewall rules, DNS domain inclusions and exclusions, and bypasses for applications and IP addresses. Rulesets can include traffic steering only, endpoint firewall rules only, or a combination of both. You can add a ruleset for each network type and assign the rulesets to app profiles.
This feature is available only for Zscaler Client Connector version 4.8 and later for Windows. Contact Zscaler Support to enable this feature.
Location-based policies provide the following benefits and enable you to do the following:
- Create policies using a framework with support for reusable objects and bulk changes.
- Bypass or tunnel traffic for destination IP addresses and subnets, traffic from predefined and custom IP-based applications, and DNS queries by domain.
- Bypass all traffic from specific processes.
- Enforce endpoint firewall rules for inbound and outbound traffic, including 5-tuples, applications, and default rules.
- Enforce inbound rules for Private Applications client-to-client traffic.
- Save time by removing the need to configure default outbound Allow All rules in your host firewall settings.
About the Location-Based Policies Page
On the Location-Based Policies page (Infrastructure > Connectors > Client > Location-Based Policies), you can do the following:
- [Add a ruleset](/unified/adding-ruleset).
- [Add a traffic steering IP list](/unified/adding-traffic-steering-ip-list).
- [Add a domain list](/unified/adding-domain-list).
- [Add an application for a ruleset](/unified/adding-application-ruleset).
- [Add a firewall IP list](/unified/adding-firewall-ip-list).
- View a list of all rulesets configured for your organization. For each ruleset, you can see the following details:
- **Ruleset Name**: The name of the ruleset.
- **Last Edited Time**: The date and time when the ruleset was last edited.
- Perform an exact match search of rulesets that include:
- **Policy Rulesets**: The name of the ruleset.
- **Traffic Steering IP List**: A list from the [Traffic Steering IP Lists](/unified/adding-traffic-steering-ip-list) tab.
- **Domain List**: A list from the [Domain Lists](/unified/adding-domain-list) tab.
- **Application List**: An application from the [Applications](/unified/adding-application-ruleset) tab.
- **Firewall IP List**: A list from the [Firewall IP Lists](/unified/adding-firewall-ip-list) tab.
- **Process-Based Application Bypass**: A [process-based application](/unified/adding-process-based-applications-bypass-traffic) from Application Bypass.
- **Predefined IP-Based Application Bypass**: A Zscaler predefined IP-based application.
- **Custom IP-Based Application Bypass**: A [custom IP-based application](/unified/adding-ip-based-applications-bypass-traffic) from Application Bypass.
- Search for a ruleset.
- Modify the table and its columns.
- Copy a ruleset.
- Edit a ruleset.
- Delete a ruleset.
![Location-Based Policies page](/downloads/zscaler-client-connector/forwarding-traffic-management/about-location-based-policies/zclient-connector-location-based-policies.png)