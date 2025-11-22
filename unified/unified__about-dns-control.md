# About DNS Control
Source: https://help.zscaler.com/unified/about-dns-control
PDF: https://help.zscaler.com/pdf/com/en/1494086.pdf

The Domain Name System (DNS) is a key part of the internet, offering the power of translating quickly between the human language of the URL and the computer language of the IP address. With DNS Control, you can define rules that control DNS requests and responses.
However, DNS traffic often goes unmonitored and does not go through traditional firewalls. Because of this, DNS traffic can be abused through techniques such as tunneling. DNS Control also allows you to detect and prevent DNS tunneling from occurring on your network. To learn more, see [Detecting and Controlling DNS Tunnels](/unified/detecting-and-controlling-dns-tunnels).
DNS Control provides the following benefits and enables you to:
- Monitor and apply policies to all DNS requests and responses, irrespective of the protocol and the encryption used. This includes UDP, TCP, and DNS over HTTPS (DoH).
- Define granular DNS filtering rules using a number of DNS conditions, such as users, groups, or departments, client locations, categorization of domains and IP addresses, DNS record types, the location of resolved IPs, etc.
- Enforce condition-based actions on DNS traffic, such as allowing or blocking traffic, redirecting requests to specific DNS servers, redirecting users by overwriting DNS responses, etc.
- Detect and prevent DNS-based attacks and data exfiltration through DNS tunnels.
- Enhance your security posture by using Zscaler Trusted DNS Resolver for domain resolution.
To enable DNS Control, you need to [configure the firewall for locations](/unified/configuring-locations). If your organization uses Zscaler Tunnel (Z-Tunnel) 1.0 or PAC files to route traffic, you need to enable the firewall for this type of traffic in the [Advanced Settings](/unified/configuring-advanced-settings). In addition, ensure that the DNS Services option is configured in the Advanced Settings.
Zscaler provides the following predefined DNS Rules:
- **UCaaS One Click Rule**: Allows traffic from the firewall when you enable any UCaaS application in the [Advanced Settings](/unified/configuring-advanced-settings).
- **ZPA Resolver for Locations**: Forwards location users’ source IP anchored traffic to Private Applications.
- **ZPA Resolver for the Road Warrior**: Forwards remote users’ source IP anchored traffic to Private Applications.
You can also disable or modify these predefined rules based on your needs. Zscaler also recommends maintaining these rules in higher rule order (i.e., Rule 1 and Rule 2).
The DNS control policy also has default rules that allow all DNS traffic. These rules always maintain the lowest precedence. You can modify their actions, but you cannot delete them. To learn more, see [Modifying the Default DNS Control Rule](/unified/modifying-predefined-dns-control-rules).
The Zscaler service categorizes domains that are newly registered within the last 30 days or observed for the first time as Newly Registered and Observed Domains (NROD) until a proper classification is available. As Zscaler updates the NROD database at periodic intervals, a latency of about 2 to 36 hours is expected for domains to be classified as NROD depending on whether the domain is newly registered, observed, or newly revived. Moreover, the URL classification may not be available for the first-ever DNS request for such domains due to propagation delays.
DNS Traffic Control Methods
You can apply the DNS Control policy to recursive and iterative DNS requests with appropriate policy configurations. Iterative DNS requests require additional policy configurations to transit the traffic through the Zscaler service. Depending on your DNS deployment method and configuration options, the Zscaler service can control your DNS traffic in the following ways.
- [Traffic from the Client IP Address](#client_traffic)
- [Traffic from the IP Address of the Internal DNS Server](#dns_server_traffic)
About the DNS Control Page
On the DNS Control page (Policies > Access Control > Firewall > DNS Control), you can do the following:
- [Configure a DNS Filtering policy rule](/unified/configuring-dns-control-policy).
- View a list of all configured DNS Filtering policy rules. Here you can see the following:
- **Rule Order**: The policy rule's order number. DNS Control policy rules are evaluated in ascending numerical order. You can sort this column.
- **Admin Rank**: The [admin rank](/unified/about-admin-rank) assigned for the rule. This is visible only if admin ranking is enabled in the [Advanced Settings](/unified/configuring-advanced-settings#admin-ranking). You can sort this column.
- **Rule Name**: The name of this rule. You can sort this column.
- **Criteria**: A description of the different criteria that have been added to this rule.
- **Action**: Whether the policy is set to Allow, Block, Redirect Request, or Redirect Response.
- **Label and Description**: The label and description of the policy rule, if available.
- Edit or duplicate a DNS Filtering policy rule.
- [Modify the table and its columns](/unified/using-tables).
- Select one of the following **View by** option to see the DNS Filtering rules accordingly:
-
**Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#rule-order-DNS-control)
-
**Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels. You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#rule-label-DNS-control)
- Search for a DNS Filtering policy rule.
![Screenshot of DNS Control page showing buttons and list used to manage Zscaler DNS Control policies.](/downloads/zia/policies/firewall/dns-control/ZIA-DNS-Control-Policy-Page.png)
[]The Zscaler service directs users’ DNS requests forwarded via GRE tunnels, IPSec tunnels, or Zscaler Client Connector (using Zscaler Tunnel (Z-Tunnel) 2.0) to a public DNS service (e.g., Google Public DNS 8.8.8.8) or a private service hosted publicly (e.g., AWS or Azure).
Alternatively, you can use the predefined NAT rule, Zscaler Trusted DNS Resolver, to redirect all your standard DNS traffic (dest:53) to the Zscaler Trusted DNS Resolver. To learn more about the predefined NAT rule, see [About NAT Control](/unified/about-nat-control). If Zscaler Trusted DNS Resolver fails to resolve DNS requests due to DNS cluster failure in Zscaler data centers, the DNS requests are forwarded to a public DNS service (e.g., Google Public DNS 8.8.8.8). DNS requests that time out or fail with the following response codes are redirected: `SERVFAIL` or `REFUSED`. The DNS requests are routed to an anycast DNS server that is geographically closest. In DNS Insights Logs, you can view the DNS server that was used to resolve the DNS requests. To learn more, see [DNS Insights Logs: Columns](/unified/dns-insights-logs-columns).
As the traffic originates from the client IP address, the Zscaler service can identify the user, group, and department the DNS request is coming from. This allows you to define and apply policies by user, group, department, location, and time.
[]The Zscaler service can control traffic from the internal DNS server that acts as a DNS forwarder or an iterative DNS resolver.
-
**Forwarded DNS Requests**: Zscaler's predefined NAT rule (Zscaler Trusted DNS Resolver) redirects all your standard DNS traffic (dest:53), including requests forwarded by the DNS server, to the Zscaler Trusted DNS Resolver. To learn more about the predefined NAT rule, see [About NAT Control](/unified/about-nat-control).
If Zscaler Trusted DNS Resolver fails to resolve DNS requests due to DNS cluster failure in Zscaler data centers, the DNS requests are forwarded to a public DNS service (e.g., Google Public DNS 8.8.8.8). DNS requests that time out or fail with the following response codes are redirected: `SERVFAIL` or `REFUSED`. The DNS requests are routed to an anycast DNS server that is geographically closest. In DNS Insights Logs, you can view the DNS server that was used to resolve the DNS requests. To learn more, see [DNS Insights Logs: Columns](/unified/dns-insights-logs-columns).
-
**Iterative DNS Requests**: DNS requests from an iterative DNS resolver must transit through the Zscaler service to an external DNS server that may support responses to the iterative DNS queries. Zscaler's predefined NAT rule (Zscaler Trusted DNS Resolver) redirects all your standard DNS traffic (dest:53) to the Zscaler Trusted DNS Resolver but drops the iterative DNS queries. So, if the predefined rule is enabled, you need to create a separate NAT rule with a higher rank to direct your iterative queries to an external DNS server. You can disable the predefined rule if your entire DNS traffic reaching the Internet & SaaS is only iterative or if you intend to direct all your standard DNS queries to an external DNS provider (e.g., 8.8.8.8).
Irrespective of whether the predefined NAT rule is enabled or disabled, the DNS over HTTPS (DoH) traffic (dest:443) will always transit to the external DNS provider specified. However, if you define a redirect rule in the DNS Control policy, the DoH traffic gets redirected and inspected by Internet & SaaS as standard DNS over UDP traffic (dest:53).
For DNS requests that come from the internal DNS server, you can only apply policies based on location and time.
[]![Screenshot of DNS Control page with Rule Order view selected.](/downloads/zia/policies/firewall/dns-control/ZIA-DNS-Control-Policy-Page-Viewby-Rule-Order.png)
[]![Screenshot of DNS Control page with Rule Label view selected.](/downloads/zia/policies/firewall/dns-control/ZIA-DNS-Control-Policy-Page-Viewby-Rule-Label.png)