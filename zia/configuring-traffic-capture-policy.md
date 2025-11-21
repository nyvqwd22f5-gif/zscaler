# Configuring the Traffic Capture Policy
Source: https://help.zscaler.com/zia/configuring-traffic-capture-policy
PDF: https://help.zscaler.com/pdf/com/en/1532182.pdf

You can add rules to the Traffic Capture policy to capture matching traffic and forward it for storage. To learn more, see [About Traffic Capture Policy](/zia/about-traffic-capture-policy).
Policy Execution
There is a series of logical operators between the criteria in Traffic Capture policy rules. The criteria on each tab have their own set of logical operators.
The tabs trigger based on the following relationships:
- **Who, Where, & When**: [(Users `OR` Groups `OR` Departments) `AND` (Locations `OR` Location Groups) `AND` Time `AND` (Devices `OR` Device Groups)]
- **Services**: (Network Service Groups `OR` Network Services)
- **Applications**: [(Network Application Groups `OR` Network Applications) `AND` (Application Service Groups)]
- **Source IP**: (Source IPv4 Groups `OR` Source IPv6 Groups `OR` IP Addresses `OR` Countries)
- **Destination IP**: (Destination IPv4 Groups `OR` Destination IPv6 Groups `OR` IP Address or FQDN `OR` Countries)
In addition to the logical operators between criteria, the relationship between tabs is `AND`.
- [See an example of how the Traffic Capture policy triggers.](#pol-ex)
Prerequisites
Traffic Capture must be enabled on the Traffic Capture Settings page in the Administration section (Administration > Traffic Capture). You must also connect an Amazon S3 storage bucket. Firewall must be enabled for any locations you want to configure Traffic Capture policy rules for. To learn more, see [Configuring Traffic Capture Settings](/zia/configuring-traffic-capture-settings).
When configuring your S3 bucket, Zscaler recommends using dual-stack storage endpoints for all cloud destinations. To learn more, refer to the [Amazon S3 documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html).
Before adding or modifying rules for the Traffic Capture policy, ensure that you have configured any resources that the policies reference. These resources include:
- Users, groups, departments, locations, and sublocations to which the Traffic Capture policy applies.
- Location Groups.
- Time Intervals.
- Network Applications. You can create network application groups as needed.
- Network Services. You can modify network services to edit services, add custom services, and create groups.
- Source and destination IP address groups.
- [IPv6 configuration.](/zia/understanding-ipv6-support)
Adding a Traffic Capture Rule
To configure a Traffic Capture policy rule:
- Go to **Policy** > **Traffic Capture**.
-
Click **Add Traffic Capture Rule**.
The **Add Traffic Capture Rule** window appears.
-
In the **Add Traffic Capture Rule** window, enter the rule attributes:
- **Rule Order**:** **The policy automatically assigns the **Rule Order** number. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value, but if you've enabled [Admin Rank](/zia/about-admin-rank), your assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Choose your admin rank. This option appears if you enable [Admin Ranking](/zia/about-admin-rank) on the [Advanced Settings](/zia/about-advanced-settings) page. Enter a value from 0 to 7 (0 is the highest rank). Your assigned [admin rank](/zia/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule's admin rank determines the value you can select in the rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: The policy automatically creates a rule name, which you can change. The maximum length is 63 characters.
- **Rule Status**:** **By default, the status is **Enabled**. An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order. The service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/zia/about-rule-labels).
[See image.](#img1)
-
On the **Who, Where, & When** tab:
-
**Users**, **Groups**, **Departments**, and **Locations**: Select any to which this rule applies. You can search for items or click the **Add **icon to add an item. By default, these fields are set to **Any**. If you do not select specific values for a field, it remains set to **Any**, and the field criteria are ignored during policy evaluation.
If you've enabled the policy for unauthenticated users under[ Advanced Settings](/zia/about-advanced-settings), and want to apply this rule to unauthenticated traffic, you can do so by making selections accordingly in the **Users **and **Departments **fields. To learn more, see [Configuring Policies for Unauthenticated Traffic](/zia/configuring-policies-for-unauthenticated-traffic).
If you want to apply this rule only to remote users' traffic, select **Road Warrior** from the **Locations** field. Rules configured for locations other than Road Warrior also apply to remote user traffic from those locations.
- **Location Groups**: Select the [location groups](/zia/about-location-groups) to which the rule applies. By default, this field is set to **Any**. If you do not select specific location groups, the field remains set to **Any**, and the criterion is ignored during policy evaluation. You can select up to 32 location groups. You can also search for specific location groups to select them.
- **Time**: Select the [time interval](/zia/defining-time-intervals) during which the rule applies. Select **Always** to apply this rule to all time intervals, or select up to two time intervals. You can search for a time interval or click the **Add** icon to add a new time interval.
- **Devices**: Select the [devices](/zia/about-devices) for which you want to apply the rule. Selecting no value ignores the criterion in the policy evaluation.
-
**Device Groups**: Select the [device group](/zia/about-device-groups) for which you want to apply the rule. For [Zscaler Client Connector](/zscaler-client-connector/what-is-zscaler-client-connector) traffic, select the appropriate group based on the device platform. Select **Cloud Browser Isolation** or **No Client Connector** to apply the rule to [Isolation](/isolation/what-is-isolation) traffic or to traffic that is not tunneled through Zscaler Client Connector, respectively. Selecting no value ignores the criterion in the policy evaluation.
The **Cloud Browser Isolation** group is available only if Isolation is enabled for your organization.
[See image.](#img2)
-
On the **Services **tab:
- **Network Service Groups:** Select the predefined or custom [network service groups](/zia/adding-network-service-groups) to which the rule applies.
- **Network Services: **Select the [network services](/zia/about-network-services) to which the rule applies. By default, this field is set to **Any**. If you do not select specific network services, the field remains set to **Any**, and the criterion is ignored during policy evaluation.
[See image.](#img3)
-
On the **Applications** tab:
- **Network Application Groups: **Select the [application groups](/zia/adding-network-application-groups) that you want to apply the rule to. The service provides predefined applications that you can group, but not modify.
- **Network Applications: **Select the [applications](/zia/about-network-applications) that you want to apply the rule to. By default, this field is set to **Any**. If you do not select specific applications, the field remains set to **Any**, and the criterion is ignored during policy evaluation. The service provides predefined applications, which you can group, but not modify.
- **Application Service Groups**: Select the [application service groups](/zia/about-application-service-groups) that you want to apply the rule to. The service provides predefined application services that you can group, but not modify.
[See image.](#Applications)
-
On the **Source IP** tab:
- **Source IPv4 Groups**: Select the [source IPv4 groups](/zia/about-source-ip-groups) that you want to apply the rule to. Click the **Add **icon to add a new source IPv4 group.
-
**Source IPv6 Groups**: To apply the rule to source IPv6 addresses, select the **All IPv6** group, which is the predefined source IPv6 group for all IPv6 addresses.
Custom source IPv6 groups are currently not supported. To learn more, see [About Source IP Groups](/zia/about-source-ip-groups).
-
**IP Addresses**: Enter addresses (IPv4 only) in any of the following formats:
- An individual address, such as `192.0.2.1`.
- A subnet, such as `192.0.2.0/24`.
- An address range, such as `192.0.2.1 - 192.0.2.5`.
Specifying individual, subnet, or range of IPv6 addresses is currently not supported.
For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
-
**Countries**: To apply the rule to traffic from specific countries, select the traffic's source country. The traffic's country of origin is determined using the geolocation of the client's IP address. When configuring this criterion, you can either use the **Include** option to match the rule on the specified countries or use the **Exclude** option to match the rule on all countries except those that are selected.
When using the **Include** option, you can select specific countries or leave the field set to the default value, **Any**, which causes the criterion to be ignored during policy evaluation. However, selecting countries is mandatory when using the **Exclude** option.
[See image.](#img4)
-
On the **Destination IP** tab:
- **Destination IPv4 Groups**:** **Select the [destination IPv4 groups](/zia/about-destination-ip-groups) that you want to apply the rule to. Click the **Add **icon to add a new destination IPv4 group.
-
**Destination IPv6 Groups**: To apply the rule to destination IPv6 addresses, select the **All IPv6** Group, which is the default destination IPv6 group for all IPv6 addresses.
Custom destination IPv6 groups are currently not supported. To learn more, see [About Destination IP Groups](/zia/about-destination-ip-groups).
-
**IP Address or Wildcard FQDN**: Enter addresses (IPv4 only) in any of the following formats:
- An individual address, such as `192.0.2.1`.
- A subnet, such as `192.0.2.0/24`.
- An address range, such as `192.0.2.1 - 192.0.2.5`.
Specifying individual, subnet, or range of IPv6 addresses is currently not supported.
You can also add FQDNs for applications with multiple or frequently changing IPv4 addresses. Wildcard FQDNs are also supported with an asterisk (*) as the wildcard character. For guidelines to configure wildcard FQDNs, see [Configuring Destination IP Groups](/zia/configuring-destination-ip-groups). When the [rule is activated](/zia/saving-and-activating-changes-admin-portal), FQDNs are resolved to their corresponding IP addresses and stored by the Zscaler service. To obtain the IP address of a domain, DNS queries are made until no new IP addresses are returned in two consecutive DNS responses. The resolved IP addresses are then stored for a period of twice the Time to Live (TTL) value in the DNS record.
As both FQDN and IP address values are available for a destination, this criterion applies to the web as well as non-web traffic examined by the Zscaler service. The Zscaler service employs an IP address match when evaluating non-web traffic using this criterion, whereas the web traffic evaluation relies on an FQDN match against the hostname in the HTTP/FTP header or Server Name Indication (SNI) for HTTPS.
To evaluate wildcard FQDNs against non-web traffic, Zscaler requires the IP address to which the FQDN resolves. Hence, for non-web traffic, the Zscaler service should be aware of the preceding DNS request/response. To ensure this, forward *all* of your DNS traffic to the Zscaler service if you intend to configure wildcard FQDNs in policies. Additionally, ZIA with DNS Control is required. This functionality is included in Advanced Firewall and DNS Control and [ZIA editions](https://www.zscaler.com/pricing-and-plans). To learn how DNS resolution is handled by the Zscaler service, see [Handling DNS Resolution for Various Traffic Forwarding Methods](/zia/handling-dns-resolution-various-traffic-forwarding-methods).
Wildcard FQDN match against web traffic (HTTP and TLS/SNI) can function without meeting these conditions.
To add multiple entries, press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Countries**: Select the countries to apply the rule to the outgoing traffic that matches the specified countries. The country where the destination server is placed is determined using the geolocation of the server's IP address. By default, this field is set to **Any**. If you do not select specific countries, the field remains set to **Any**, and the criterion is ignored during policy evaluation.
[See image.](#img5)
-
Choose the Network Traffic **Action** that the Zscaler service takes when packets match the rule.
- **Capture**: Enable to capture traffic that matches the rule. If this setting is not enabled, the policy skips** **the traffic designated by the rule.
- **Sampling**: Select the percentage of connections sampled for capturing each time the rule is triggered.
- **Storage Limit**: Select the maximum amount of traffic to capture per connection.
[See image.](#action)
- **Description: **(Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change.](/zia/saving-and-activating-changes-admin-portal)
[]To see the impact of the logical relationship between criteria, consider a rule with an **Action** of **Capture** and the following criteria:
- **Who, Where, & When**
- Users = User 1
- Groups = Any
- Departments = Sales
- Locations = San Jose
- Location Groups = Any
- Time = Always
- Device = Left blank
- Device Groups = Left blank
- **Services**
- Network Service Groups = None
- Network Services = Any
- **Applications**
- Network Applications = None
- Network Application Groups = None
- Application Service Groups = None
- **Source IP**
- Source IPv4 Groups = Office IPs
- Source IPv6 Groups = Left blank
- IP Addresses = Left blank
- Countries = Include United States
- **Destination IP**
- Destination IPv4 Groups = None
- Destination IPv6 Groups = Left blank
- IP Address or Wildcard FQDN = 192.0.2.1 - 192.0.2.5
- Countries = Any
Then, consider the following scenario:
- The user is User 1, and they are from the Engineering department and in the San Jose location. Since there is an `OR` relationship between Users, Groups, and Departments, the **Who, Where, & When** tab triggers even though User 1 is from the Engineering department, not Sales. The rule bypasses the fields that are set to **Any**,** **when any one of the fields has set criteria among the `OR` fields within an `AND` bracket.
- Since all Network Services and Network Applications are included in this rule, the **Services & Applications** tab triggers.
- User 1's traffic originates in the United States, but the source IP address is not part of the Office IPs Source IPv4 Group. However, the **Source IP** tab triggers because of the `OR` relationship between these criteria.
- The URL that User 1 attempts to visit belongs to Forbidden Websites, but the IP address of the URL does not fall within the specified range. Because of the `OR` relationship, the **Destination IP** tab triggers.
The rule triggers for all the values in the fields if you set **Any** for all the fields that have an `OR` relation together within an `AND` bracket.
Since all the tabs trigger, the policy rule triggers and the traffic is captured.
However, if the location of the user changed from San Jose to San Francisco, the **Who, Where, & When** tab would not trigger, which would cause the whole rule not to trigger.
[]![The Add Traffic Capture Rule page with the fields Rule Order, Admin Rank, Rule Name, Rule Status, and Rule Label](/downloads/zia/policies/traffic-capture/configuring-traffic-capture-policy/ZIA-add-capture-rule-policy-info.png)
[]![Who, Where, & When Tab for adding a Traffic Capture rule](/downloads/zia/policies/traffic-capture/configuring-traffic-capture-policy/ZIA-traffic-capture-policy-who-where-and-when.png)
[]![The Services page with the fields Network Service Groups and Network Services.](/downloads/zia/policies/traffic-capture/configuring-traffic-capture-policy/ZIA-traffic-capture-policy-services.png)
[]![The Source IP criteria in Traffic Capture rule](/downloads/zia/policies/traffic-capture/configuring-traffic-capture-policy/ZIA-traffic-capture-policy-source-ip-criteria.png)
[]![The destination IP criteria in Traffic Capture rule](/downloads/zia/policies/traffic-capture/configuring-traffic-capture-policy/ZIA-traffic-capture-policy-destination-ip-criteria.png)
[]![The Applications page with the fields Network Applications, Network Application Groups, Application Services, and Application Service Groups.](/downloads/zia/policies/traffic-capture/configuring-traffic-capture-policy/ZIA-traffic-capture-policy-applications.png)
[]![The Action section for the Traffic Capture policy rule](/downloads/zia/policies/traffic-capture/configuring-traffic-capture-policy/ZIA-traffic-capture-policy-action-section.png)