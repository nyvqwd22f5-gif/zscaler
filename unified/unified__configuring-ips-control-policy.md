# Configuring IPS Control Policy
Source: https://help.zscaler.com/unified/configuring-ips-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1494306.pdf

Zscaler's Intrusion Prevention System (IPS) uses signature-based detection to monitor and protect your network traffic from malicious activities. With IPS Control, you can configure rules that are matched against your traffic to enforce condition-based actions to allow or block the traffic in real time. You can capture and store traffic allowed or blocked by this policy as PCAP files. To learn more, see [About Traffic Capture](/unified/about-traffic-capture).
The Zscaler service provides a default rule that blocks all traffic and logs sessions using aggregate logging. You need to modify this rule or create a higher-order rule to allow traffic through the Zscaler service. The default rule always maintains the lowest precedence, and it cannot be deleted.
After configuring the IPS rules, you need to enable IPS Control for location traffic and remote user traffic. To learn more, see [About IPS Control](/unified/about-ips-control).
The default IPS rule can be modified only with the super admin role.
Policy Execution
There is a series of logical operators between the criteria in DNS Control policy rules. The criteria on each tab have their own set of logical operators.
The tabs trigger based on the following relationships:
- **Who, Where, & When**: [Users (`OR`) Groups OR Departments] (`AND`) [Locations (`OR`) Location Groups] (`AND`) Time.
- **Services & Threat Categories**: [Network Service Groups (`OR`) Network Services] (`AND`) Advanced Threat Category.
- **Source IP**: Source IP Groups (`OR`) IP Addresses.
- **Destination IP**: Destination Groups (`OR`) IP Address/FQDN (`OR`) Countries (`OR`) URL Categories.
In addition to the logical operators between criteria, the relationship between tabs is (`AND`).
Prerequisites
Before adding or modifying rules for IPS Control policy, ensure that you have configured any resources that the policies reference:
- Users, groups, departments, locations, and sublocations to which the IPS Control policy rules apply.
- Location Groups.
- Time Intervals.
- Network Services. You can modify network services to edit services, add custom services, and create groups.
- Source and destination IP address groups.
- [IPv6 configuration.](/unified/understanding-ipv6-support)
Adding an IPS Control Rule
To configure an IPS Control policy rule:
- Go to **Policies **> **Cybersecurity **> **Inline Security **> **IPS Control**.
-
Click **Add IPS Control Rule**.
The **Add IPS Control Rule** window appears.
- In the **Add IPS Control Rule** window, enter the **IPS Control Rule** attributes:
- **Rule Order**:** **The firewall automatically assigns the rule order number. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value, but if you've enabled [Admin Rank](/unified/about-admin-rank) , your assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Choose your admin rank. This option appears if you enable [Admin Ranking](/unified/about-admin-rank) on the [Advanced Settings](/unified/configuring-advanced-settings) page. Enter a value from 0 to 7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule's admin rank determines the value you can select in the rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: The firewall automatically creates a rule name, which you can change. The maximum length is 63 characters.
- **Rule Status**:** **By default, the status is **Enabled**. An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order. The service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/unified/about-rule-labels).
- On the **Who, Where, & When** tab:
-
Select the **Users**, **Groups**, **Departments**, and **Locations** to which this rule applies. You can select **Any** to select all items or select up to 32 users, groups, departments, and locations. You can search for items or click the **Add **icon to add an item.
If you've enabled the policy for unauthenticated users under[ Advanced Settings](/unified/configuring-advanced-settings), and want to apply this rule to unauthenticated traffic, you can do so by making selections accordingly in the **Users **and **Departments **fields. To learn more, see [Configuring Policies for Unauthenticated Traffic](/unified/configuring-policies-unauthenticated-traffic).
Contact Zscaler Support to increase the limit of **Users**, **Groups**, **Departments**, or **Locations**.
If you want to apply this rule only to remote users’ traffic, select **Road Warrior** from the Locations field. Rules configured for locations other than Road Warrior also apply to remote user traffic from those locations.
The rules configured for Road Warrior location apply to Zscaler Tunnel (Z-Tunnel) 1.0 and PAC only when the **Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors** option is enabled in [Advanced Settings](/unified/configuring-advanced-settings#firewall-remote-users).
- **Location Groups**: Select the [location groups](/unified/about-location-groups) to which this rule applies. You can select **Any** to select all location groups, or select up to 32 location groups. You can search for location groups.
- **Time**: Select the [time interval](/unified/defining-time-intervals) during which the rule applies. Select **Always** to apply this rule to all time intervals, or select up to two time intervals. You can search for a time interval or click the **Add** icon to add a new time interval.
- On the **Services & Threat Categories** tab:
- **Network Service Groups:** Select the predefined or custom [network service groups](/unified/configuring-network-service-groups) to which the rule applies.
- **Network Services: **Select **Any** to apply the rule to all [network services](/unified/about-network-services) or select specific network services. The Zscaler Firewall has 50 predefined services, and you can configure up to 832 additional custom services.
- **Advanced Threat Categories**: Select **Any** to apply the rule to all threat categories, or select specific threat categories. Advanced Threat Categories group together common threats to your organization allowing you to block threats such as viruses or botnets. [See the list of predefined advanced threat categories and their descriptions](/unified/about-threat-categories#threat-category-list).
-
On the **Applications** tab:
**ZPA Application Segment:** Select **Any** to apply the rule to all [application segments of Private Applications](/unified/configuring-defined-application-segments), or select up to 255 application segments of Private Applications. You can also search for application segments of Private Applications. The list displays only those application segments of Private Applications that have the [Source IP Anchor](/unified/understanding-source-ip-anchoring) option enabled.
If you select the** Inspect App Segments** option from the list, then the configured rule applies to all the application segments of Private Applications paired to your Internet & SaaS tenant. This option is only available if the **SIPA App Segments** subscription is enabled for your organization.
[See image.](#zpa-application-segment-image)
- On the **Source IP** tab:
- **Source IPv4 Groups**: Select the [source IPv4 groups](/unified/about-source-ip-groups) that you want to control with this rule. You can also add a new Source IPv4 Group by clicking the **Add **icon.
-
**Source IPv6 Groups**: To control source IPv6 addresses with this rule, select the **All IPv6** group, which is the default source IPv6 group for all IPv6 addresses.
Custom source IPv6 groups are currently not supported. To learn more, see [About Source IP Groups](/unified/about-source-ip-groups).
-
**IP Address**: Enter IP addresses (IPv4 only) in any of the following formats:
- An individual IP address, such as 192.0.2.1.
- A subnet, such as 192.0.2.0/24.
- An IP address range, such as 192.0.2.1 - 192.0.2.5.
Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- On the **Destination IP** tab:
- **Destination IPv4 Groups**:** **Select the [destination IPv4 groups](/unified/configuring-destination-ip-groups) that you want to control with this rule. You can also add a new Destination IPv4 Group by clicking the **Add **icon.
-
**Destination IPv6 Groups**: To control destination IPv6 addresses with this rule, select the **All IPv6** Group, which is the default destination IPv6 group for all IPv6 addresses.
Custom destination IPv6 groups are not currently supported. To learn more, see [About Destination IP Groups](/unified/about-destination-ip-groups).
-
**IP Address or Wildcard FQDN** (FQDN is available with Advanced Firewall): Enter IP addresses (IPv4 only) in any of the following formats:
- An IP address range, such as 192.0.2.1 - 192.0.2.5.
- A subnet, such as 192.0.2.0/24.
- An individual IP address, such as 192.0.2.1.
If you have Advanced Firewall, you can also add FQDNs for applications with multiple IP addresses or with IP addresses that frequently change. Wildcard FQDNs are also supported with an asterisk (*) as the wildcard character. For guidelines to configure wildcard FQDNs, see [Configuring Destination IP Groups](/unified/configuring-destination-ip-groups).
- Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
- IPS control rules based on Wildcard FQDNs require DNS requests from clients to be forwarded to the Zscaler service to evaluate criteria match. To learn how DNS resolution is handled by the Zscaler service, see [Handling DNS Resolution for Various Traffic Forwarding Methods](/unified/handling-dns-resolution-various-traffic-forwarding-methods).
- **Countries**: Select the countries you want to control with this rule. You can identify destinations based on the location of a server. Select **Any** to apply the rule to all countries or select the countries for which you want to control traffic.
-
**Categories**: Select the [custom URL categories](/unified/configuring-custom-url-categories) that you want to control with this rule. You can also use a custom URL category based on a specific database address (FQDN) which allows destinations to be placed on the allowlist or denylist as desired. Select **Any** to apply the rule to all categories or select the specific categories for which you want to control traffic.
You can also select [custom TLD categories](/unified/about-tld-categories) from this field.
- Choose the **Action** that the Zscaler service takes when packets match the rule.
- **Allow**: Allow the packets to pass through the IPS.
- **Block/Drop**: Silently block packets that match the rule.
- **Block/Reset**: For TCP traffic, the Zscaler service drops all packets that match the rule and sends the client a TCP reset. (A TCP packet with the "reset" (RST) flag is set to 1 in the TCP header, indicating that the TCP connection must be instantly stopped.) For non-TCP traffic, same as** Block/Drop**.
-
**Bypass IPS**: Allow the packets without scanning. If you select this option, you cannot select any **Advanced Threat Category** for the rule.
If Traffic Capture is enabled, the **Capture** option appears when **Allow** or **Block** are selected. Captured traffic is stored in PCAP files for later analysis. To enable Traffic Capture for this policy, see [Configuring Traffic Capture](/unified/configuring-traffic-capture).
- Choose the **Logging** option:
- **Aggregate**: The service groups together individual sessions based on user, rule, and network service and records them periodically. Log aggregation happens approximately every 15 minutes.
-
**Full**: The service logs all sessions of the rule individually, except HTTP(S).
In Standard Firewall, full logging is supported only for Block rules. Full logging for all other rules requires Full Logging or Advanced Firewall.
-
Under **Notification**:
End user notification (EUN) is supported only for **Allow** and **Block** actions and is not supported for **Bypass/IPS**. The EUN is supported on Windows devices running Zscaler Client Connector version 4.8 or later over Z-Tunnel 2.0. To learn more, see [Configuring EUNs for IPS Control](/unified/configuring-euns-ips-control).
- **Client Connector EUN**: Enable this option to display a notification to end users through Zscaler Client Connector when users access traffic that is allowed or blocked by this rule.
- **Notification Message**: This option appears if the end user notification (EUN) is enabled, and allows you to select the notification message. You can select from default and custom notification messages to display for users.
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change.](/unified/saving-and-activating-changes-admin-portal)
![The Inspect App Segments option for the ZPA Application Segment field ](/downloads/zia/policies/firewall/ips-control/configuring-ips-control-policy/zia-configuring-ips-control-zpa-app-segments-inspect-app-segments-option.png)
[]