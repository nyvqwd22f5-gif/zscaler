# Configuring the NAT Control Policy
Source: https://help.zscaler.com/zia/configuring-nat-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1399986.pdf

Configuring a NAT Control policy rule provides greater control over your NAT traffic.
The Zscaler service does not monitor the health or the availability status of an endpoint to which NAT rules forward traffic. This means that NAT rules forward traffic to the specified destination irrespective of whether the destination endpoint is reachable or not. So, ensure that the NAT destination endpoint is always available to prevent connection failures.
Policy Execution
There is a series of logical operators between the criteria in NAT Control policy rules. The criteria on each tab have their own set of logical operators.
The tabs trigger based on the following relationships:
- **Who, Where, & When**: [Users (`OR`) Groups (`OR`) Departments] (`AND`) [Locations (`OR`) Location Groups] (`AND`) Time.
- **Services**: Network Service Groups (`OR`) Network Services.
- **Source IP**: Source IP Groups (`OR`) IP Addresses.
- **Destination IP**: Destination Groups (`OR`) IP Address/Wildcard FQDN (`OR`) Countries (`OR`) Categories.
In addition to the logical operators between criteria, the relationship between tabs is `AND`.
- [See how an example NAT Control policy triggers](#exmaple-nat-config)
[]To see the impact of the logical relationship between criteria, consider a rule with an action to redirect the matching traffic to zstrustedresolver.zscaler.net and the following criteria:
- **Who, Where, & When**
- Users = User 1
- Groups = Any
- Departments = Sales
- Locations = San Jose
- Location Groups = Any
- Time = Always
- **Services & Applications**
- Network Service Groups = None
- Network Services = Any
- **Source IP**
- Source IP Groups = Office IPs (a custom category)
- Source IPv6 Groups = Left blank
- IP Addresses = Left blank
- **Destination IP**
- Destination IPv4 Groups = None
- Destination IPv6 Groups = Left blank
- Destination Groups = None
- IP Address or Wildcard FQDN = 192.0.2.1 - 192.0.2.5
- Countries = Any
- Categories = Forbidden Websites (a custom category)
Then consider the following scenario:
- The user is User 1 and they are from the Engineering department and in the San Jose location. Since there is an OR relationship between Users, Groups, and Departments, the **Who, Where, & When** tab triggers even though User 1 is from the Engineering department, not Sales. The rule bypasses the fields that are set to **Any **when any one of the fields has set criteria among the OR fields within an AND bracket.
- Since all network services are included in this rule, the **Services & Applications** tab triggers.
- The source IP for User 1 is part of the Office IPs Source IPv4 Group. The **Source IP** tab triggers.
- The URL, User 1 attempts to visit, belongs to Forbidden Websites but the IP address of the URL does not fall within the specified range. Because of the OR relationship, the **Destination IP** tab triggers.
The rule triggers for all the values in the fields if you set **Any** for all the fields that have an `OR` relationship together within an `AND` bracket.
Since all the tabs trigger, the policy rule triggers and the matching traffic is redirected to the destination specified in the DNAT IP Address or Wildcard FQDN field.
However, if the location of the user changed from San Jose to San Francisco, the **Who, Where, & When** tab would not trigger, which would cause the whole rule not to trigger.
Prerequisites
Before adding rules to the NAT Control policy, ensure that you have configured the resources that the policies reference:
- [Users](/zia/about-users), [groups](/zia/about-groups), [departments](/zia/about-departments), and [locations](/zia/about-locations) to which the firewall policies apply.
- [Location Groups](/zia/about-location-groups).
- [Time Intervals](/zia/how-do-i-define-time-intervals).
- The firewall provides predefined network services. You can modify [network services](/zia/about-network-services) to edit services, add custom services, and create groups.
- Optionally, [source](/zia/configuring-source-ip-groups) and [destination IP](/zia/how-do-i-configure-destination-ip-groups) address groups.
- Optionally, [IPv6 configuration](/zia/understanding-ipv6-support).
After adding rules to the NAT Control policy, you might also need to do the following before [enabling the firewall](/zia/how-do-i-enable-firewall-locations) for your locations:
- Add rules to the [Firewall Filtering policy](/zia/how-do-i-configure-firewall-filtering-policy) and [DNS Control policy](/zia/about-dns-control), if applicable.
- Configure [custom ports](/zia/how-do-i-configure-custom-ports), if applicable.
Adding a NAT Control Rule
To configure a NAT Control policy rule:
- Go to **Policy** > **Firewall Control** > **NAT Control Policy**.
-
Click **Add NAT Control Rule**.
The **Add NAT Control Rule** window appears.
- In the **Add NAT Control Rule** window, enter the **NAT Control Rule** attributes:
- **Rule Order**:** **The firewall automatically assigns the rule order number. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule’s place in the order. You can change the value, but if you’ve enabled [Admin Rank](/zia/what-admin-rank), your assigned admin rank determines the rule order values you can select.
- **Admin Rank**:** **Choose your admin rank. This option appears if you enabled [Admin Ranking](/zia/what-admin-rank) on the [Advanced Settings](/zia/about-advanced-settings) page. Enter a value from 0 to 7 (0 is the highest rank). Your assigned [admin rank](/zia/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule’s admin rank determines the value you can select in the rule order. A rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**:** **The firewall automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**:** **By default, rule status shows that the rule is enabled. An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order. The service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/zia/about-rule-labels).
- [See image.](#img1)
-
On the **Who, Where, & When** tab, you can configure the following options:
-
Select the **Users**, **Groups**, **Departments**, and **Locations** (requires Advanced Firewall) to which this rule applies. You can select **Any** to select all items or select up to 32 users, groups, departments, and locations. You can search for items or click the **Add **icon to add an item.
If you've enabled the policy for unauthenticated users under [Advanced Settings](/zia/about-advanced-settings), and want to apply this rule to unauthenticated traffic, you can do so by making selections accordingly in the **Users **and **Departments **fields. To learn more, see [Configuring Policies for Unauthenticated Traffic](/zia/how-do-i-configure-policy-unauthenticated-traffic).
Contact Zscaler Support to increase the limit of **Users**, **Groups**, **Departments**, or **Locations**.
If you want to apply this rule only to remote users’ traffic, select **Road Warrior** from the Locations field. Rules configured for locations other than Road Warrior also apply to remote user traffic from those locations.
The rules configured for Road Warrior location apply to Z-Tunnel 1.0 and PAC only when the **Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors** option is enabled in [Advanced Settings](/zia/about-advanced-settings#firewall-remote-users).
- **Location Groups**: Select the [location groups](/zia/about-location-groups) to which this rule applies. You can select **Any** to select all location groups, or select up to 32 location groups. You can search for location groups.
- **Time**: Select the [time interval](/zia/how-do-i-define-time-intervals) during which the rule applies. Select **Always** to apply this rule to all time intervals, or select up to two time intervals. You can search for a time interval or click the **Add** icon to add a new time interval.
[See image.](#img2)
-
On the **Services **tab, you can configure the following options:
- **Network Service Groups**:** **Select any number of predefined or custom [network service groups](/zia/about-network-service-groups) to which the rule applies.
- **Network Services**:** **Select **Always** to apply the rule to all [network services](/zia/about-network-services) or select specific network services. The Zscaler Firewall has 50 predefined services and you can configure up to 832 additional custom services.
If you configure these fields to exclusively match DNS network services defined in the [Advanced Settings](/zia/configuring-advanced-settings#dns), two additional actions, namely **Redirect Using DoH **and **Redirect DNS & Keep Sender Protocol**, are shown apart from the **DNAT IP Address or FQDN** action. These additional actions are available only when DNS is exclusively configured, without being combined with other network services.
If you select RTSP as a Network Service for your rule, the rule also applies to RTP and RTCP traffic since RTP and RTCP connections are dynamically created by RTSP.
[See image.](#img3)
-
On the **Source IP** tab, you can configure the following options:
- **Source IPv4 Groups**: Select the [source IPv4 groups](/zia/about-source-ip-groups) that you want to control with this rule. You can also add a new source IPv4 group by clicking the **Add **icon.
-
**Source IPv6 Groups**: To control source IPv6 addresses with this rule, select the **All IPv6** group, which is the default source IPv6 group for all IPv6 addresses.
Custom source IPv6 groups are currently not supported. To learn more, see [About Source IP Groups](/zia/about-source-ip-groups).
-
**IP Addresses**: Enter IP addresses (IPv4 only) in any of the following formats:
- An address range(e.g., 192.0.2.1 - 192.0.2.5)
- A subnet (e.g., 192.0.2.0/24)
- An individual IP address (e.g., 192.0.2.1)
Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
[See image.](#img4)
-
On the **Destination IP** tab, you can configure the following options:
- **Destination IPv4 Groups**:** **Select the [destination IPv4 groups](/zia/about-destination-ip-groups) that you want to control with this rule. You can also add a new Destination IPv4 Group by clicking the **Add **icon.
-
**Destination IPv6 Groups**: To control destination IPv6 addresses with the rule, select the **All IPv6** Group, which is the default destination IPv6 group for all IPv6 addresses.
Custom destination IPv6 groups are not currently supported. To learn more, see [About Destination IP Groups](/zia/about-destination-ip-groups).
-
**IP Address or Wildcard FQDN**: Enter IP addresses (IPv4 only) in any of the following formats:
- An IP address range (e.g., 192.0.2.1 - 192.0.2.5)
- A subnet (e.g., 192.0.2.0/24)
- An individual IP address (e.g., 192.0.2.1)
Specifying individual, subnet, or range of IPv6 addresses is currently not supported.
You can also add FQDNs for applications with multiple IP addresses or with IP addresses that frequently change. Wildcard FQDNs are also supported with an asterisk (*) as the wildcard character. For guidelines to configure wildcard FQDNs, see [Configuring Destination IP Groups](/zia/configuring-destination-ip-groups).
To evaluate wildcard FQDNs against non-web traffic, Zscaler requires the IP address to which the FQDN resolves. Hence, for non-web traffic, the Zscaler service should be aware of the preceding DNS request/response. To ensure this, forward *all* of your DNS traffic to the Zscaler service if you intend to configure wildcard FQDNs in policies. Additionally, a subscription or ZIA edition with DNS Control is required. This functionality is included in Advanced Firewall and DNS Control and [ZIA editions](https://www.zscaler.com/pricing-and-plans). To learn how DNS resolution is handled by the Zscaler service, see [Handling DNS Resolution for Various Traffic Forwarding Methods](/zia/handling-dns-resolution-various-traffic-forwarding-methods). Wildcard FQDN match against web traffic (HTTP and TLS/SNI) can function without meeting these conditions.
To add multiple entries, press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Countries**: You can identify destinations based on the location of a server. Select **Any** to apply the rule to all countries or select the countries for which you want to control traffic.
- **Categories**: You can identify destinations based on the [URL category](/zia/about-url-categories) of the domain. Select **Any** to apply the rule to all categories or select the specific categories for which you want to control traffic.
[See image.](#img5)
-
In the **Action** section, configure to redirect the traffic that matches the criteria to a specific destination. The actions displayed might vary with the policy criteria you have configured. The following action is supported for all criteria:
-
**DNAT IP Address or FQDN**: You can enter an IP address (IPv4 only) in one of the following formats and, optionally, specify a port number:
- An individual address (e.g., 192.0.2.1)
- A subnet (e.g., 192.0.2.0/24)
- An address range (e.g., 192.0.2.1 - 192.0.2.5)
You can specify wildcard FQDNs for domains with multiple IP addresses or with IP addresses that frequently change. You can enter FQDNs or wildcard FQDNs using an asterisk (*) as the wildcard character.
In addition to the **DNAT IP Address or FQDN** action, the following actions are shown if the **Network Services** and/or **Network Group Services** condition is configured to exclusively match DNS:
-
**Redirect Request Using DoH**: Redirect DNS requests using DoH to the external DNS service configured in the specified DNS Gateway. If the incoming DNS request uses protocols other than DoH (i.e., UDP or TCP), the Zscaler service translates the protocol to DoH and then redirects the request to the external DNS service.
In the **DNS Gateway** field, select the DNS Gateway that must be used to redirect the DNS request. Only DNS Gateways configured with DoH support are listed.
-
**Redirect DNS & Keep Sender Protocol**: Redirect DNS requests using the original user protocol to the external DNS service configured in the specified DNS Gateway.
In the **DNS Gateway** field, select the DNS Gateway that must be used to redirect the DNS request. The DNS Gateway must be configured to support protocols used by the incoming requests to redirect the DNS requests successfully. To learn more, see [About DNS Gateways](/zia/about-dns-gateways).
This action applies to DNS traffic sent over UDP or TCP.
[See image.](#img6)
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Add NAT Control Rule section with the fields Rule Order, Admin Rank, Rule Name, Rule Status, and Rule Label.](/downloads/zia/documentation-knowledgebase/policies/firewall/nat-control/configuring-nat-control-policy/ZIA-Add-NAT-Control-Rule-Screenshot.png)
[]![Who, Where, & When criteria in NAT rule](/downloads/zia/documentation-knowledgebase/policies/firewall/nat-control/configuring-nat-control-policy/nat-who-where-when.png)
[]![Services criteria in NAT rule](/downloads/zia/documentation-knowledgebase/policies/firewall/nat-control/configuring-nat-control-policy/nat-control-rule-services-tab.png)
[]![Source IP criteria in NAT rule](/downloads/zia/documentation-knowledgebase/policies/firewall/nat-control/configuring-nat-control-policy/nat-source-ip_0.png)
[]![The destination IP criteria in NAT rule](/downloads/zia/documentation-knowledgebase/policies/firewall/nat-control/configuring-nat-control-policy/nat-destination-ip_0.png)
[]![NAT rule actions](/downloads/zia/documentation-knowledgebase/policies/firewall/nat-control/configuring-nat-control-policy/nat-control-rule-action.png)