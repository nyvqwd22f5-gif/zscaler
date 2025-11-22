# Configuring the Firewall Filtering Policy
Source: https://help.zscaler.com/zia/configuring-firewall-filtering-policy
PDF: https://help.zscaler.com/pdf/com/en/1399876.pdf

[Watch a video about Firewall Control, including how to configure the Firewall Filtering policy](https://fast.wistia.net/embed/iframe/aauzes6y9s)
You can add rules to the Firewall Filtering policy to allow or block specific types of traffic from your network to the internet. You can capture and store traffic blocked through this policy as PCAP files. To learn more, see [About Traffic Capture Settings](/zia/about-traffic-capture). The Firewall Filtering policy has a default rule, which blocks all traffic from your network to the internet. To learn more, see [Editing the Default Firewall Filtering Rule](/zia/modifying-default-firewall-filtering-rule). Apart from the Default Firewall Filtering Rule, Zscaler provides a few predefined firewall filtering rules. To learn more, see About [Predefined Firewall Filtering Rules](/zia/about-predefined-firewall-filtering-rules).
After adding rules to the Firewall Filtering policy, you might also need to do the following before [enabling firewall](/zia/enabling-firewall-locations) for your locations:
- Modify rules for the [NAT Control policy](/zia/about-nat-control) and [DNS Control policy](/zia/about-dns-control).
- Configure [custom ports](/zia/configuring-custom-ports).
Policy Execution
There is a series of logical operators between the criteria in Firewall Filtering policy rules. The criteria on each tab have their own set of logical operators.
The tabs trigger based on the following relationships:
- **Who, Where, & When**: [Users (`OR`) Groups (`OR`) Departments] (`AND`) [Locations (`OR`) Location Groups] (`AND`) Time (`AND`) [Devices (`OR`) Device Groups] (`AND`) Device Trust Level.
- **Services**: Network Service Groups (`OR`) Network Services.
- **Applications**: [Network Application Groups (`OR`) Network Applications (`OR`) Application Service Groups] (`AND`) ZPA Application Segment.
- **Source IP**: Source IPv4 Groups (`OR`) IP Addresses (`OR`) Countries.
- **Destination IP**: Destination Groups (`OR`) IP Address/FQDN (`OR`) Countries (`OR`) URL Categories.
In addition to the logical operators between criteria, the relationship between tabs is `AND`.
- [See an example of how Firewall Filtering policy triggers](#pol-ex)
Prerequisites
Before adding or modifying rules for the Firewall Filtering policy, ensure that you have configured any resources that the policies reference. These resources include:
- Users, groups, departments, locations, and sublocations to which the Firewall Filtering policy applies.
- Location Groups.
- Time Intervals.
- Workload Groups.
- Network Applications. You can create network application groups as needed.
- Network Services. You can modify network services to edit services, add custom services, and create groups.
- Source and destination IP address groups.
- [IPv6 configuration.](/zia/understanding-ipv6-support)
Adding a Firewall Filtering Rule
To configure a Firewall Filtering policy rule:
- Go to **Policy** > **Firewall Control** > **Firewall Filtering Policy**.
-
Click **Add Firewall Filtering Rule**.
The **Add Firewall Filtering Rule** window appears.
-
In the **Add Firewall Filtering Rule** window, enter the rule attributes:
- **Rule Order**:** **The firewall automatically assigns the **Rule Order** number. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value, but if you've enabled [Admin Rank](/zia/about-admin-rank), your assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Choose your admin rank. This option appears if you enable [Admin Ranking](/zia/about-admin-rank) on the [Advanced Settings](/zia/about-advanced-settings) page. Enter a value from 0 to 7 (0 is the highest rank). Your assigned [admin rank](/zia/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule's admin rank determines the value you can select in the rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: The firewall automatically creates a rule name, which you can change. The maximum length is 63 characters.
- **Rule Status**:** **By default, the status is **Enabled**. An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the Rule Order. The service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/zia/about-rule-labels).
[See image.](#img1)
-
On the **Who, Where, & When** tab:
-
Select the **Users**, **Groups**, **Departments**, and **Locations** to which this rule applies. You can search for items or click the **Add **icon to add an item. Select **Any** to apply the rules to all users, groups, departments, and locations or select up to 32 users, groups, departments, and locations. If you do not select specific values for a field, it remains set to **Any**, and the field criteria are ignored during policy evaluation.
If you've enabled the policy for unauthenticated users under[ Advanced Settings](/zia/about-advanced-settings), and want to apply this rule to unauthenticated traffic, you can do so by making selections accordingly in the **Users **and **Departments **fields. To learn more, see [Configuring Policies for Unauthenticated Traffic](/zia/configuring-policies-for-unauthenticated-traffic).
Contact Zscaler Support to increase the limit of **Users**, **Groups**, **Departments**, or **Locations**.
If you want to apply this rule only to remote users' traffic, select **Road Warrior** from the Locations field. Rules configured for locations other than Road Warrior also apply to remote user traffic from those locations.
The rules configured for Road Warrior location apply to Zscaler Tunnel (Z-Tunnel) 1.0 and PAC only when the **Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors** option is enabled in [Advanced Settings](/zia/about-advanced-settings#firewall-remote-users).
- **Location Groups**: Select the [location groups](/zia/about-location-groups) to which the rule applies. By default, this field is set to **Any**. If you do not select specific location groups, the field remains set to **Any**, and the criterion is ignored during policy evaluation. You can select up to 32 location groups. You can also search for specific location groups to select them.
- **Time**: Select the [time interval](/zia/defining-time-intervals) during which the rule applies. Select **Always** to apply this rule to all time intervals, or select up to two time intervals. You can search for a time interval or click the **Add** icon to add a new time interval.
- **Devices**: Select the [devices](/zia/about-devices) for which you want to apply the rule. Selecting no value ignores the criterion in the policy evaluation.
-
**Device Groups**: Select the [device group](/zia/about-device-groups) for which you want to apply the rule. For Zscaler Client Connector traffic, select the appropriate group based on the device platform. Select **Cloud Browser Isolation** or **No Client Connector** to apply the rule to Isolation traffic or to traffic that is not tunneled through Zscaler Client Connector, respectively. Selecting no value ignores the criterion in the policy evaluation.
The **Cloud Browser Isolation** group is available only if Isolation is enabled for your organization.
- []
**Device Trust Level**: Select the device trust level values (**High Trust**, **Medium Trust**, **Low Trust**, or **Unknown**) to which the rule applies. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic. Selecting no value ignores the criterion in the policy evaluation.
The trust levels assigned to the devices are based on your [posture configurations](/client-connector/adding-zia-posture-profiles) in the Zscaler Client Connector Portal.
- **Workload Groups**: Select up to 8 [workload groups](/zia/about-workload-groups) for which you want to apply the rule. You can also search for a workload group. Selecting **None** ignores this criterion during policy evaluation.
[See image.](#img2)
-
On the **Services **tab:
- **Network Service Groups:** Select the predefined or custom [network service groups](/zia/configuring-network-service-groups) to which the rule applies.
- **Network Services: **Select the [network services](/zia/about-network-services) to which the rule applies. By default, this field is set to **Any**. If you do not select specific network services, the field remains set to **Any**, and the criterion is ignored during policy evaluation. The Zscaler Firewall has 50 predefined services, and you can configure up to 832 additional custom services.
In standard mode, RTSP applications use RTP and RTCP. This means that if RTSP applications are allowed, then RTP and RTCP connections (which are dynamically created by RTSP) are automatically allowed too. This happens even if there is a Firewall rule to block RTP and RTCP Network Applications. This does not happen if the RTSP application is in interleaved mode.
[See image.](#img3)
-
On the **Applications** tab:
- **Network Application Groups: **Select the [application groups](/zia/adding-network-application-groups) that you want to control with this rule. The service provides predefined applications that you can group, but not modify.
-
**Network Applications: **Select the [applications](/zia/about-network-applications) that you want to control with this rule. By default, this field is set to **Any**. If you do not select specific applications, the field remains set to **Any**, and the criterion is ignored during policy evaluation. The service provides predefined applications, which you can group, but not modify.
Network services and application services configured in Zscaler are identified in the first packet, leading to immediate policy action. In contrast, multiple packets are typically required by deep packet inspection to identify network applications before a policy action can take place. Therefore, Zscaler recommends that you rank firewall filtering rules for network applications lower than rules for network services or application services to prevent packets from being allowed unnecessarily from traffic that would otherwise be blocked by rules using first-packet identification. To learn more, see [About Network Applications](/zia/about-network-applications).
- **Application Service Groups**: Select the [application service groups](/zia/about-application-service-groups) that you want to control with this rule. The service provides predefined application services that you can group, but not modify.
-
**ZPA Application Segment:** Select **Any** to apply the rule to all [Zscaler Private Access (ZPA) application segments](/zpa/configuring-application-segments), or select up to 255 ZPA application segments. You can also search for ZPA application segments. The list displays only those ZPA application segments that have the [Source IP Anchor](/zia/understanding-source-ip-anchoring) option enabled.
If you select the** Inspect App Segments** option from the list, then the configured rule applies to all the ZPA application segments paired to your ZIA tenant. This option is only available if the **SIPA App Segments** subscription is enabled for your organization.
[See image.](#zpa-application-segment-image)
[See image.](#Applications)
-
On the **Source IP** tab:
- **Source IPv4 Groups**: Select the [source IPv4 groups](/zia/about-source-ip-groups) that you want to control with this rule. Click the **Add **icon to add a new source IPv4 group.
-
**Source IPv6 Groups**: To control source IPv6 addresses with this rule, select the **All IPv6** group, which is the predefined source IPv6 group for all IPv6 addresses.
Custom source IPv6 groups are currently not supported. To learn more, see [About Source IP Groups](/zia/about-source-ip-groups).
-
**IP Addresses**: Enter addresses (IPv4 only) in any of the following formats:
- An individual address, such as 192.0.2.1.
- A subnet, such as 192.0.2.0/24.
- An address range, such as 192.0.2.1 - 192.0.2.5.
Specifying individual, subnet, or range of IPv6 addresses is currently not supported.
For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
-
**Countries**: To apply the rule to traffic from specific countries, select the traffic's source country. The traffic's country of origin is determined using the geolocation of the client's IP address. When configuring this criterion, you can either use the **Include** option to match the rule on the specified countries or use the **Exclude** option to match the rule on all countries except those that are selected.
When using the **Include** option, you can select specific countries or leave the field set to the default value, **Any**, which causes the criterion to be ignored during policy evaluation. However, selecting countries is mandatory when using the **Exclude** option.
[See image.](#img4)
-
On the **Destination IP** tab:
- **Destination IPv4 Groups**:** **Select the [destination IPv4 groups](/zia/about-destination-ip-groups) that you want to control with this rule. Click the **Add **icon to add a new destination IPv4 group.
-
**Destination IPv6 Groups**: To control destination IPv6 addresses with this rule, select the **All IPv6** Group, which is the default destination IPv6 group for all IPv6 addresses.
Custom destination IPv6 groups are currently not supported. To learn more, see [About Destination IP Groups](/zia/about-destination-ip-groups).
-
**IP Address or Wildcard FQDN**: Enter addresses (IPv4 only) in any of the following formats:
- An individual address, such as 192.0.2.1.
- A subnet, such as 192.0.2.0/24.
- An address range, such as 192.0.2.1 - 192.0.2.5.
Specifying individual, subnet, or range of IPv6 addresses is currently not supported.
You can also add FQDNs for applications with multiple or frequently changing IPv4 addresses. Wildcard FQDNs are also supported with an asterisk (*) as the wildcard character. For guidelines to configure wildcard FQDNs, see [Configuring Destination IP Groups](/zia/configuring-destination-ip-groups). When the [rule is activated](/zia/saving-and-activating-changes-admin-portal), FQDNs are resolved to their corresponding IP addresses and stored by the Zscaler service. To obtain the IP address of a domain, DNS queries are made until no new IP addresses are returned in two consecutive DNS responses. The resolved IP address(es) is then stored for a period of twice the Time to Live (TTL) value in the DNS record.
As both FQDN and IP address values are available for a destination, this criterion applies to the web as well as non-web traffic examined by the Zscaler service. The Zscaler service employs an IP address match when evaluating non-web traffic using this criterion, whereas the web traffic evaluation relies on an FQDN match against the hostname in the HTTP/FTP header or Server Name Indication (SNI) for HTTPS.
To evaluate wildcard FQDNs against non-web traffic, Zscaler requires the IP address to which the FQDN resolves. Hence, for non-web traffic, the Zscaler service should be aware of the preceding DNS request/response. To ensure this, forward *all* of your DNS traffic to the Zscaler service if you intend to configure wildcard FQDNs in policies. Additionally, a subscription or Zscaler Internet Access (ZIA) edition with DNS Control is required. This functionality is included in Advanced Firewall and DNS Control and [ZIA editions](https://www.zscaler.com/pricing-and-plans). To learn how DNS resolution is handled by the Zscaler service, see [Handling DNS Resolution for Various Traffic Forwarding Methods](/zia/handling-dns-resolution-various-traffic-forwarding-methods).
Wildcard FQDN match against web traffic (HTTP and TLS/SNI) can function without meeting these conditions.
To add multiple entries, press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
If a rule blocks traffic solely based on the destination, removing destination IP addresses or FQDNs from the rule should be done cautiously as that might result in the rule blocking all traffic without requiring any criteria match.
- **Countries**: Select the countries to apply the rule to the outgoing traffic that matches the specified countries. The country where the destination server is placed is determined using the geolocation of the server's IP address. By default, this field is set to **Any**. If you do not select specific countries, the field remains set to **Any**, and the criterion is ignored during policy evaluation.
-
**URL Categories**: Select the URL categories for which you want to control traffic. By default, this field is set to **Any**. If you do not select specific URL categories, the field remains set to **Any**, and the criterion is ignored during policy evaluation.
You can also select [custom TLD categories](/zia/about-tld-categories) from this field.
You can identify destinations based on the custom URL category of the domain. You can also use a custom URL category based on a specific database address (FQDN) or a wildcard FQDN which allows destinations to be placed on the allowlist or denylist as desired. To learn more, see [About URL Categories](/zia/about-url-categories).
Zscaler Firewall examines only the host portion of a URL (i.e., domain and subdomain) and ignores the URL path. For example, if a rule is configured to block traffic directed to www.subdomain.example.com/subdirectory/path.html via a URL category, all traffic bound to www.subdomain.example.com is blocked.
Unlike the FQDNs specified directly in a rule via the **IP Address or Wildcard FQDN** field, FQDNs specified through a URL category are *not* pre-resolved to an IP address and stored by the Zscaler service. This restricts the URL category’s application to only web traffic, where an FQDN match against the hostname in the HTTP/FTP header or SNI for HTTPS triggers the rule. However, you can add IP addresses to URL categories in order to use this criterion for non-web traffic.
[See image.](#img5)
-
Choose the Network Traffic **Action** that the Zscaler service takes when packets match the rule.
- **Allow**: Allow the packets to pass through the firewall.
-
**Block/Drop**: Silently block packets that match the rule.
When the Block/Drop action is configured to block IP addresses, it might still result in sending packets to the destination server based on web sessions if the traffic is HTTPS and an end user notification (EUN) is served via web security policies. These packets are sent to obtain the server’s signed certificate (i.e., beaconing), which is a legitimate and necessary part of the EUN workflow.
- **Block/ICMP**: Drop all packets that match the rule and send the client an ICMP error message of Type 3 (Destination Unreachable) and Code 13 (Communication Administratively Prohibited).
- **Block/Reset**: For TCP traffic, the Zscaler service drops all packets that match the rule and sends the client a TCP reset. (A TCP packet with the *reset* (RST) flag is set to 1 in the TCPheader, indicating that the TCP connection must be instantly stopped.) For non-TCP traffic, the action is the same as Block/Drop.
If Traffic Capture is enabled, the **Capture** option appears when **Block** is selected. Captured traffic is stored in PCAP files for later analysis. To enable Traffic Capture for this policy, see [Configuring Traffic Capture Settings](/zia/configuring-traffic-capture).
-
Choose the **Logging** option:
- **Aggregate**: The service groups together individual sessions based on user, rule, network service, network application and records them periodically. Log aggregation happens approximately every 15 minutes.
-
**Full**: The service logs all sessions of the rule individually, except HTTP(S).
In Standard Firewall, full logging is supported only for Block rules. Full logging for all other rules requires Full Logging or Advanced Firewall.
[See image.](#img6)
-
Under **Notification**:
End user notification (EUN) is supported only with Block actions and requires Advanced Firewall. The EUN is supported on Windows devices running Zscaler Client Connector version 4.8 or later over Z-Tunnel 2.0. To learn more, see [Configuring EUNs for Firewall Filtering](/zia/configuring-euns-firewall-filtering).
- **Client Connector EUN**: Enable this option to display a notification to end users through Zscaler Client Connector when they access traffic blocked by this rule.
- **Notification Message**: This option appears if the end user notification (EUN) is enabled, and allows you to select the notification message. You can select from default and custom notification messages to display for users.
[See image.](#enable-zscaler-client-connector-eun)
- (Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change.](/zia/saving-and-activating-changes-admin-portal)
[]To see the impact of the logical relationship between criteria, consider a rule with an **Action** of **Block/Drop** and the following criteria:
- **Who, Where, & When**
- Users = User 1
- Groups = Any
- Departments = Sales
- Locations = San Jose
- Location Groups = Any
- Time = Always
- Device = Left blank
- Device Groups = Left blank
- Device Trust Level = Left blank
- Workload Groups = Left blank
- **Services & Applications**
- Network Service Groups = None
- Network Services = Any
- Application Service Groups = None
- **Source IP**
- Source IPv4 Groups = Office IPs
- Source IPv6 Groups = Left blank
- IP Addresses = Left blank
- Countries = Include Unites States
- **Destination IP**
- Destination IPv4 Groups = None
- Destination IPv6 Groups = Left blank
- IP Address or Wildcard FQDN = 192.0.2.1 - 192.0.2.5
- Countries = Any
- Categories = Forbidden Websites (a custom category)
Then, consider the following scenario:
- The user is User 1, and they are from the Engineering department and in the San Jose location. Since there is an `OR` relationship between Users, Groups, and Departments, the **Who, Where, & When** tab triggers even though User 1 is from the Engineering department, not Sales. The rule bypasses the fields that are set to **Any**,** **when any one of the fields has set criteria among the `OR` fields within an `AND` bracket.
- Since all Network Services and Network Applications are included in this rule, the **Services & Applications** tab triggers.
- User 1's traffic originates in the United States, but the source IP address is not part of the Office IPs Source IPv4 Group. However, the **Source IP** tab triggers because of the `OR` relationship between these criteria.
- The URL that User 1 attempts to visit belongs to Forbidden Websites, but the IP address of the URL does not fall within the specified range. Because of the `OR` relationship, the **Destination IP** tab triggers.
The rule triggers for all the values in the fields if you set **Any** for all the fields that have an `OR` relation together within an `AND` bracket.
Since all the tabs trigger, the policy rule triggers and the user is blocked from the transaction.
However, if the location of the user changed from San Jose to San Francisco, the **Who, Where, & When** tab would not trigger, which would cause the whole rule not to trigger.
[]![The Add Firewall Filtering Rule page with the fields Rule Order, Admin Rank, Rule Name, Rule Status, and Rule Label](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/configuring-firewall-filtering-policy/firewall-filtering-rule-fields.png)
[]![Who, where, and when criteria for firewall filtering rules](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/configuring-firewall-filtering-policy/who-where-when-criteria-firewall-filtering.png)
[]![The Services page with the fields Network Service Groups and Network Services.](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-control/configuring-firewall-filtering-policy/add-FW-filtering-rule_criteria_services.png)
[]![The Source IP criteria in firewall filtering rule](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/configuring-firewall-filtering-policy/firewall-filtering-source-ip-tab.png)
[]![The destination IP criteria in firewall filtering rule](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-control/configuring-firewall-filtering-policy/firewall-filtering-destination-ip.png)
[]![Firewall filtering rule actions](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/configuring-firewall-filtering-policy/firewall-filtering-actions-logging.png)
[]![The Applications page with the fields Network Applications, Network Application Groups, Application Services, and Application Service Groups.](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/configuring-firewall-filtering-policy/firewall-filtering-rule-applications-tab.png)
![The Inspect App Segments option for the ZPA Application Segment field](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/configuring-firewall-filtering-policy/zia-configuring-firewall-control-zpa-app-segments-inspect-app-segments-option.png)
[]
[]![Enable Zscaler Client Connector EUN and select a notification message](/downloads/zia/policies/firewall/firewall-control/firewall-filtering/configuring-firewall-filtering-policy/firewall-rule-zscaler-client-connector-eun.png)