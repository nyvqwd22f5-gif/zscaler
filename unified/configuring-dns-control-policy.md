# Configuring the DNS Control Policy
Source: https://help.zscaler.com/zia/configuring-dns-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1399991.pdf

[Watch a video about Configuring DNS Control Policy.](https://fast.wistia.net/embed/iframe/9hj1kgu3pc)
Configuring a DNS Control rule provides you with greater control over your DNS traffic. You can capture and store traffic blocked through this policy as PCAP files. To learn more, see [About Traffic Capture Settings](/zia/about-traffic-capture).
To learn about the recommended configurations for the DNS Control policy, see [Best Practices for DNS Control Rules](/zia/best-practices-dns-control-rules).
Policy Execution
There is a series of logical operators between the criteria in DNS Control policy rules. The criteria on each tab have their own set of logical operators.
The tabs trigger based on the following relationships:
- **Who, Where, & When**: [Users (`OR`) Groups (`OR`) Departments] (`AND`) [Locations (`OR`) Location Groups] (`AND`) Time.
- **Source IP**: Source Groups (`OR`) IP Addresses.
- **Destination/Resolved IPs**: Destination IPv4 Groups (`OR`) DNS Server IP Addresses.
- **DNS Application**: [DNS Tunnels & Network Apps (`OR`) DNS Application Group] (`AND`) [Resolved IP-Based Countries (`OR`) Requested Categories/Response Categories] (`AND`) DNS Request Types (`AND`) Protocol.
In addition to the logical operators between criteria, the relationship between tabs is (`AND`).
[See an example of how the DNS Control policy triggers.](#example-dns-rule)
Prerequisites
Make sure the following prerequisites are met:
- Ensure that you have configured, as necessary, the resources that the policies reference:
- [Users](/zia/about-users), [groups](/zia/about-groups), [departments](/zia/about-departments), and [locations](/zia/about-locations) to which the DNS Control policy applies
- [Location groups](/zia/about-location-groups)
- [Time intervals](/zia/how-do-i-define-time-intervals)
- Optionally, [source](/zia/configuring-source-ip-groups) and [destination IPv4](/zia/how-do-i-configure-destination-ip-groups) address groups
- Optionally, [IPv6 configuration](/zia/understanding-ipv6-support)
-
Ensure that you set up the following DNS configurations per your requirements:
- [Recursive DNS Requests](#recursive-dns-requests)
- [Iterative DNS Requests](#iterative-dns-requests)
To learn more, see [About DNS Control](/zia/about-dns-control#dns-traffic-control-methods).
Non-English characters are not supported in DNS Control rules, with the exception of those from the ISO/IEC 8859-1 character set.
Adding a DNS Control Rule
To configure a DNS Control policy filtering rule:
- Go to **Policy **>** DNS Control**.
- Click **Add DNS Filtering Rule**.
- Enter the rule attributes:
- **Rule Order**:** **The firewall automatically assigns the rule order number. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value, but if you've enabled [Admin Rank](/zia/what-admin-rank), your assigned admin rank determines the rule order values you can select.
- **Admin Rank**:** **Choose your admin rank. This option appears if you've enabled [Admin Ranking](/zia/about-admin-rank) on the [Advanced Settings](/zia/about-advanced-settings) page.
- **Rule Name**: The firewall automatically creates a rule name, which you can change. The maximum length is 63 characters. Avoid using the names of rules that were previously deleted. If you do, the service displays the logs for the deleted rule and the new rule when you view the logs.
- **Rule Status**:** **By default, rule status shows that the rule is enabled. An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order. The service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/zia/about-rule-labels).
-
On the **Who, Where, & When** tab, you can choose the **Users**, **Groups**, **Departments**, and **Locations** to which this rule applies. You can select **Any** to select all items, or select up to 32 users, groups, departments, and locations. You can search for items or click the **Add** icon to add an item.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, **Departments**, or **Locations**.
- From the **Time** menu, choose the [time interval](/zia/how-do-i-define-time-intervals) during which the rule applies. Select **Always** to apply this rule to all time intervals, or select up to two time intervals. You can search for a time interval or click the **Add** icon to add a new time interval.
- From the **Location Groups **menu, choose the [location groups](/zia/about-location-groups) to which this rule applies. You can select **Any** to select all location groups, or select up to 32 location groups. You can search for location groups.
If you've enabled the policy for unauthenticated users under [Advanced Settings](/zia/configuring-advanced-settings), and want to apply this rule to any unauthenticated traffic, see [Configuring Policies for Unauthenticated Traffic](/zia/configuring-policies-for-unauthenticated-traffic). If you want to apply this rule only to remote users' traffic, select **Road Warrior** from the **Locations** field. Rules configured for locations other than Road Warrior also apply to remote user traffic from those locations.
-
On the **Source IPs** tab:
-
Select the [source IPv4 groups](/zia/about-source-ip-groups) that you want to control with this rule. You can also add a new Source IPv4 Group by clicking the **Add **icon. To control source IPv6 addresses with this rule, select the **All IPv6** group, which is the default source IPv6 group for all IPv6 addresses.
Custom source IPv6 groups are not currently supported. To learn more, see [About Source IP Groups](/zia/about-source-ip-groups).
-
Enter addresses (IPv4 only) in any of the following formats:
- An individual address (e.g., 192.0.2.1)
- A subnet (e.g., 192.0.2.0/24)
- An address range (e.g., 192.0.2.1 - 192.0.2.5)
Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
-
On the **Destination/Resolved IPs** tab:
-
Select the [destination IPv4 groups](/zia/about-destination-groups) that you want to control with this rule. You can also add a new Destination IPv4 Group by clicking the **Add **icon. To control destination IPv6 addresses with this rule, select the **All IPv6** group, which is the default destination IPv6 group for all IPv6 addresses.
- During policy evaluation, IP address-based destination groups in the rule criteria are ignored if an SNI value is present in HTTPS requests.
- Custom destination IPv6 groups are not currently supported. To learn more, see [About Destination IP Groups](/zia/about-destination-ip-groups).
-
Enter addresses (IPv4 only) in any of the following formats:
- An individual address (e.g., 192.0.2.1)
- A subnet (e.g., 192.0.2.0/24)
- An address range (e.g., 192.0.2.1 - 192.0.2.5)
Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
-
On the **DNS Application **tab:
- **DNS Tunnels & Network Apps**: Select any tunnels** **that you wish to control. Tunnels are categorized as **Commonly Allowed DNS Tunnels**, **Commonly Blocked DNS Tunnels**, or **Unknown DNS Tunnels**. To learn more, see [Detecting and Controlling DNS Tunnels](/zia/detecting-and-controlling-dns-tunnels). In addition to controlling tunneling traffic, you can also include specific **Web** pages, **Social Networking** sites, **Search Engines**, or **Network Services** that you wish to control at the DNS level.
- **DNS Application Groups**: Select any DNS Application Groups that you want to control. To learn more, see [About DNS Application Groups](/zia/about-dns-application-groups) and [Adding DNS Application Groups](/zia/adding-dns-application-groups).
- **Resolved IP-Based Countries**: Select the countries you want to control. Their destination is identified based on the server location.
- **Requested Categories**: Select the request categories that you want to control. Select **Any **to ignore the field for matching the rule. Click the **Sync** icon if you want the **Resolved Categories** field value to be the same as **Requested Categories**. You can also [create custom categories](/zia/adding-custom-url-categories) to control the DNS request.
-
**Resolved Categories: **Select the response categories that you want to control. Select **Any **to ignore the field for matching the rule. Click the **Sync** icon if you want the **Requested Categories** field value to be the same as **Resolved Categories**. You can also [create custom categories](/zia/adding-custom-url-categories) to control the DNS response.
You can also select [custom TLD categories](/zia/about-tld-categories) from the **Requested Categories** and **Resolved Categories** fields.
-
**DNS Request Type**: Select the DNS request types you want to control.
[See information on DNS request types and descriptions.](#seetable)
-
**Protocol**: Select the protocols you want to control listed as follows. You can select any number of protocols:
- **DNS Over HTTPS**
- **TCP**
- **UDP**
The protocols displayed might vary with the **Action** selected for the rule. For example, only **DNS Over HTTPS **and **TCP** are shown for the **Redirect Request Using TCP** action, whereas **DNS Over HTTPS** and **UDP** are shown for the **Redirect Request Using UDP** action.
You can select **Any** to select all items in a category or select specific items by clicking the checkbox. You can also search for items. For **DNS Tunnels & Network Apps **and **Requested Domain/Resolved IP Categories**, selecting a parent category includes all of its members. For example, if you select **Commonly Allowed DNS Tunnels** as part of your rule, then all tunnels listed as commonly allowed are included. By default, **Any** is selected for all categories on this tab.
-
In the **Action** section, for the **Network Traffic** field, choose the action that the Zscaler service takes when a session matches the criteria:
- **Allow**: Allows the DNS requests and responses.
-
**Block**: Silently block all DNS requests and responses.
When you select this action while Traffic Capture is enabled, an additional **Capture** field appears. Enable this option to capture and store traffic in PCAP files. To learn more, see [Configuring Traffic Capture Settings](/zia/configuring-traffic-capture).
-
**Block with Response Code**: Blocks DNS requests and responses and sends the specified response code to the client.
When this action is selected, an additional **Response Code** field appears where you can specify the response code that needs to be returned.
[List of Supported Response Codes](#block-response-code)
-
**Redirect Request Using DoH:** Redirect DNS requests using DNS over HTTPS (DoH) to the DNS service configured in the specified DNS Gateway. If the incoming DNS request uses protocols other than DoH (i.e., UDP or TCP), the Zscaler service translates the protocol to DoH and sends the DNS request to the external DNS service.
In the **DNS Gateway** field, select the DNS Gateway that must be used to redirect the DNS request. Only Gateways configured with DoH support are listed.
-
**Redirect Request Using TCP**: Redirect DNS requests using TCP to the DNS service configured in the specified DNS Gateway. The Zscaler service establishes a TCP connection to the DNS service if the incoming request uses TCP or DoH (after protocol translation). However, UDP-to-TCP translation is not supported.
When you select this action, any values configured in the **Protocol** condition are adjusted to show only supported options, namely DoH and TCP.
In the **DNS Gateway** field, select the DNS Gateway that must be used to redirect the DNS request. Only Gateways configured with TCP support are listed.
-
**Redirect Request Using UDP**: Redirect DNS requests using UDP to the DNS service configured in the specified DNS Gateway. The Zscaler service sends the request to the DNS service over UDP if the incoming request uses UDP or DoH (after protocol translation). However, TCP-to-UDP translation is not supported.
When you select this action, any values configured in the **Protocol** condition are adjusted to show only supported options, namely DoH and UDP.
In the **DNS Gateway** field, select the DNS Gateway that must be used to redirect the DNS request. Only Gateways configured with UDP support are listed.
-
**Redirect Request & Keep Sender Protocol**: Redirect DNS requests using the original user protocol (DoH, UDP, or TCP) to the DNS service configured in the specified DNS Gateway.
In the **DNS Gateway** field, select the DNS Gateway that must be used to redirect the DNS request. The DNS Gateway must be configured to support protocols used in incoming requests to redirect the DNS requests successfully. To learn more, see [About DNS Gateways](/zia/about-dns-gateways).
-
**Redirect Response**: Replace the IP address of the resolved hostname in the DNS response with a preferred IP address before sending the response to the client. This action happens on the response side but can match the request or response side condition.
In the **IP Address **field, enter the IP address that must replace the domain-resolved IP address in the DNS response to the client.
[Redirecting Users to EUN Page](#redirect-to-EUN-page)
-
**Resolve by ZPA**: Resolve domain names of Zscaler Private Access (ZPA) applications to an ephemeral IP address from a preconfigured IP pool. This action is used for redirecting traffic to ZPA and is applicable only to ZPA application segments that have Source IP Anchoring enabled.
In the **IP Pool** field, select an IP pool preconfigured for location traffic or remote user traffic, depending on the origin of traffic being forwarded.
**Logging** is set to **Full** by default and cannot be changed. With **Full** DNS logging, DNS transactions are logged individually with complete details.
-
Under **Notification**, you can enable either of the following end user notification (EUN) when specific rule actions are selected. The EUN options appear depending on the actions selected.
- **Web EUN** is supported with the **Block** action, whereas the **Client Connector EUN** is supported with **Block**, **Block with Response Code**, and **Redirect Response** actions.
- Both **Web EUN** and **Client Connector EUN** cannot function simultaneously. When both options are enabled, the **Web EUN** takes precedence and only this notification is displayed to users.
-
**Web EUN**: Enable to show a web notification to end users when they access domains that are blocked by this rule. This EUN is a standard web EUN page that Zscaler provides with support for customization to inform users of the reason for restricting access to specific domains per your organization's security policy.
[See image.](#web-eun-block-action)
-
**Client Connector EUN**: Enabling this option shows pop-up notifications to users via Zscaler Client Connector for DNS transactions that match the configured policy action. This EUN is supported with Block, Block with Response Code, and Redirect Response.
When this option is enabled, an additional **Notification Message** drop-down menu appears. You can select from default and [custom notification messages](/zia/configuring-euns-dns-control) to display for users.
This feature configuration requires Advanced DNS which is provided by the Advanced Firewall. The EUN is supported on Windows devices running Zscaler Client Connector version 4.8 or later over Z-Tunnel 2.0. To learn more, see [Configuring EUNs for DNS Control](/zia/configuring-euns-dns-control).
[See image.](#zscaler-client-connector-eun)
To learn more, see [DNS End User Notifications.](/zia/dns-end-user-notifications#advanced-eun)
- Optionally, enter additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
After adding rules to the DNS Control Policy, you might also need to do the following before [enabling the firewall](/zia/enabling-firewall-locations) for your locations.
- Modify rules for the [NAT Control Policy](/zia/about-nat-control) and [Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy) as applicable.
- Configure [custom ports](/zia/configuring-custom-ports) as applicable.
[]To see the impact of the logical relationship between criteria, consider a rule with an **Action** of **Block** and the following criteria:
- **Who, Where, & When**
- Users = User 1
- Groups = Any
- Departments = Sales
- Locations = San Jose
- Location Groups = Any
- Time = Always
- **Source IP**
- Source IPv4 Groups = Office IPs (a custom category)
- Source IPv6 Groups = Left blank
- IP Addresses = Left blank
- **Destination/Resolved IPs**
- Destination IPv4 Groups = Zscaler Resolver IP (a custom category)
- Destination IPv6 Groups = Left blank
- DNS Server IP Addresses = Any
- **DNS Application**
- DNS Tunnels & Network Apps = Agora
- DNS Application Group = Any
- Resolved IP-Based Countries = Any
- Requested Categories = Any
- Resolved Categories = Any
- DNS Request Type = Any
- Protocol = Any
Then consider the following scenario:
- The user is User 1 and they are from the Engineering department and in the San Jose location. Since there is an `OR` relationship between Users, Groups, and Departments, the **Who, Where, & When** tab triggers even though User 1 is from the Engineering department, not Sales. The rule bypasses the fields that are set to **Any **when any one of the fields has set criteria among the `OR` fields within an `AND` bracket.
- The source IP for User 1 is part of the Office IPs Source IPv4 Group. The **Source IP** tab triggers.
- The destination IP is part of the Zscaler Resolver IP group; hence, the **Destination/Resolved IPs** tab triggers.
- The User 1 request is forwarded from Agora. The Resolved IP-Based Countries and Requested Domain/Resolved IP Categories are set to **Any**, and this selection is made between two values that have an `OR` relation together within an `AND` bracket, hence the **DNS Application** tab triggers for all the Resolved IP-Based Countries and Requested Domain/Resolved IP Categories.
Since all the tabs trigger, the policy rule triggers and the user's DNS request is blocked.
However, if the location of the user changed from San Jose to San Francisco, the **Who, Where, & When** tab would not trigger which would cause the whole rule not to trigger.
[]
| DNS Request Type | Description |
| ---------------- | ----------- |
| A | IPv4 address record |
| A6 | IPv6 address record |
| AAAA | IPv6 address record |
| AFSDB | AFS database record |
| APL | Address Prefix List |
| ATMA | Asynchronous Transfer Mode address |
| CDNSKEY | Child DNSKEY |
| CDS | Child DS |
| CERT | Certificate record |
| CNAME | Canonical name record |
| CSYNC | Child-to-Parent Synchronization |
| DHCID | DHCP identifier |
| DNAME | Non-Terminal DNS Name Redirection |
| DNSKEY | DNS Key record |
| DS | Delegation signer |
| EID | DNS Endpoint Identifier resource records |
| GPOS | Group Policy Objects |
| HINFO | Host Information Record |
| HIP | Host Identity Protocol |
| HTTPS | Service binding for HTTPS including Encrypted Client Hello (ECH)You need to block the HTTPS DNS resource record type to stop ECH and prevent unmanaged encrypted traffic flows happening through the secure web gateway. |
| IPSECKEY | IPSec Key |
| ISDN | ISDN address record |
| KEY | Key record |
| KX | Key Exchanger record |
| LOC | Location record |
| MB | Mailbox record |
| MD | Mail destination record |
| MF | Mail forwarding record |
| MG | Mail group member record |
| MINFO | Mailbox or mail list record |
| MR | Renamed mailbox record |
| MX | Mail Exchanger record |
| NAPTR | Naming Authority Pointer |
| NIMLOC | Nimrod Locator resource records |
| NINFO | DNS zone status |
| NS | Name server record |
| NSAP | NSAP address record |
| NSAP_PTR | A pointer to an NSAP address record |
| NSEC | Next Secure record |
| NSEC3 | Next Secure record version 3 |
| NSEC3PARAM | NSEC3 parameters |
| NULL | A null resource record |
| NXT | The next existing server in the zone |
| OPENPGPKEY | OpenPGP public key record |
| OPT | An optional code |
| PTR | Pointer record |
| PX | X.400 mail mapping information |
| RKEY | Record for storing keys which encrypt NAPTR records |
| RP | Responsible Person |
| RRSIG | DNSSEC signature |
| RT | Route through record |
| SIG | Signature |
| SINK | Record for the storage of miscellaneous structured information |
| SOA | Start of an authority record zone |
| SRV | Service locator |
| SSHFP | SSH Public Key Fingerprint |
| SVCB | General-purpose service binding |
| TALINK | Trust Anchor LINK |
| Text File | Text record |
| TLSA | TLSA certificate association |
| WKS | A well-known service description |
| X25 | X.25 PSDN address |
| ZONEMD | Message Digest Over Zone Data |
[][](https://datatracker.ietf.org/doc/html/rfc6895)
| DNS Response Code | Description | Name per RFC 6895 |
| ----------------- | ----------- | ----------------- |
| 1 | Format Error | FormErr |
| 2 | Server Failure | ServFail |
| 3 | Non-Existent Domain | NXDomain |
| 4 | Not Implemented | NotImp |
| 5 | Query Refused | Refused |
Exercise caution when blocking with response codes, especially with "3 - Non-Existent Domain" (i.e., NXDomain), and adhere to the following recommendations:
- NXDomain should only be used exclusively with rule criteria such as Request Categories and Response Categories. These categories can include specific URL categories (both predefined and custom) and top-level domain (TLD) categories. However, categories such as Miscellaneous that are not mapped to specific target domains should be avoided in the criteria. Alternatively, consider using less definitive and less globally cacheable response codes such as "5 - Query Refused" (i.e., Refused) and "2 - Server Failure" (i.e., ServFail).
- Defining a response code for an entire type of DNS request should be strictly avoided. For example, defining a rule to block all DNS requests of A or AAAA record types (i.e., using DNS Request Type criteria) with NXDomain would likely result in an unintended DNS outage.
[]When users access specific sites that are restricted by your organization's policy, you can redirect the users to an EUN web page. You can either host a custom EUN page at a dedicated IP address, or you can redirect users to the Zscaler-provided static EUN web page hosted at the following public IP address: `34.215.46.88`. You need to manually configure this IP address in the DNS Control rule.
The static EUN web page is not customizable and is provided by Zscaler on a best effort basis. Generally, organizations should not exceed one web request per second on a sustained basis and the EUN web page should support a temporary increase to around 10 requests per second.
Zscaler recommends using the **Web EUN** notification for the **Block** action to display an EUN web page for blocked domains, as described in the preceding section. The static DNS EUN web page, accessible at `34.215.46.88`, is intended for users whose HTTP web requests are sent directly to the internet (without passing through ZIA) from unknown locations, or when the client browser/device does not trust the Zscaler CA certificate or the organization's custom certificate and it is not desirable to display a TLS certificate warning to the end users. Also, the static DNS EUN web page (at `34.215.46.88`) comes with certain limitations.
To learn more, see [DNS Static Web End User Notification](/zia/dns-static-web-end-user-notification) and [DNS End User Notifications](/zia/dns-end-user-notifications).
[]Zscaler can resolve recursive DNS queries sent directly by users or sent via a DNS server or forwarder. However, it is recommended to send recursive DNS requests from users directly (using Zscaler Client Connector with Z-Tunnel 2.0) instead of sending them via a DNS server or forwarder. Since these requests include user context, ZIA can enforce policies based on users, groups, and departments. For recursive DNS traffic that comes from a DNS server, ZIA sees only the source and not the user context.
Direct the recursive DNS requests sent to or through ZIA to the Zscaler Trusted Resolver using the predefined NAT rule, Zscaler Trusted DNS Resolver rule. The Zscaler Trusted DNS Resolver rule is enabled by default.
[]Iterative DNS requests from DNS servers should only transit ZIA (i.e., pass through ZIA and not be sent directly to it). Zscaler can secure iterative DNS traffic that transits ZIA, but enabling the Zscaler Trusted DNS Resolver rule disrupts this type of traffic.
[]![Enable web end user notification in DNS rule for Block action](/downloads/zia/policies/firewall/dns-control/configuring-dns-control-policy/dns-rule-block-action-web-eun.jpg)
[]![Enable Zscaler Client Connector end user notification in DNS rule ](/downloads/zia/policies/firewall/dns-control/configuring-dns-control-policy/dns-rule-zscaler-client-connector-eun.png)