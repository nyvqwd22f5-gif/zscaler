# Adding a Ruleset
Source: https://help.zscaler.com/zscaler-client-connector/adding-ruleset
PDF: https://help.zscaler.com/pdf/com/en/1532876.pdf

You can add a ruleset that steers traffic and applies endpoint firewall rules based on a user’s network type (e.g, On-Trusted or Off-Trusted). You can add up to 300 rulesets. For each ruleset, you can enter one or both of the following:
- Traffic steering rules, including DNS domain inclusions and exclusions, IP address inclusions and exclusions, and application bypasses
- Inbound and outbound endpoint firewall rules, including default rules
To learn more, see [About Location-Based Policies](/zscaler-client-connector/about-location-based-policies).
This feature is available only for Zscaler Client Connector version 4.8 and later for Windows. Contact Zscaler Support to enable this feature.
Prerequisites
Before you add a ruleset, make sure that you have added any of the following items you want to use in the ruleset:
- If you want to include traffic steering in the ruleset:
- [Lists of IP addresses to bypass or tunnel traffic](/zscaler-client-connector/adding-traffic-steering-ip-list) to the Zscaler Internet Access (ZIA) service.
- [Lists of domains](/zscaler-client-connector/adding-domain-list) for which to bypass or tunnel DNS queries to the ZIA service.
- If you want to include endpoint firewall rules in the ruleset:
- [Applications](/zscaler-client-connector/adding-application-ruleset) to include in inbound or outbound endpoint firewall rules.
- [Lists of IP addresses](/zscaler-client-connector/adding-firewall-ip-list) to include in inbound or outbound endpoint firewall rules.
You must select a ruleset for the On-Trusted network type and a ruleset for the Off-Trusted network type. So, if you want a different ruleset for each network type, make sure to add items as necessary.
Adding a Ruleset
To add a ruleset:
- Go to **Administration** > **Location-Based Policies**.
-
On the **Policy Rulesets** tab, click **Add Ruleset**.
The **Add Ruleset** window appears.
- In the **Add Ruleset** window, you can configure the following settings:
- [General](#general)
- [DNS](#DNS)
- [Global Bypasses & IP Inclusions/Exclusions](#bypasses)
- [Inbound Firewall Rules](#inbound-rule)
- [Default Inbound Firewall Rule](#default-inbound)
- [Outbound Firewall Rules](#outbound-rule)
- [Default Outbound Firewall Rule](#default-outbound)
- Click **Save**.
After you add a ruleset, you can add it to an app profile on the [Location Policies](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#location-policies) tab and apply it to one or more network types.
- []**Name**: Enter a unique alphanumeric name for your ruleset.
![General section on Add Ruleset window](/downloads/zscaler-client-connector/location-based-policies/about-location-based-policies/zclient-connector-add-ruleset-general.png)
[]Enter the domain inclusions and exclusions that apply to the ruleset for traffic steering:
- **Domain Inclusion**: Select a domain list from the [Domain Lists](/zscaler-client-connector/adding-domain-list) tab for which Zscaler Client Connector should send DNS requests to the ZIA Public Service Edge.
- **Domain Exclusion**: Select a domain list from the [Domain Lists](/zscaler-client-connector/adding-domain-list) tab for which Zscaler Client Connector should send DNS requests to the DNS server defined on the device (and not to the ZIA Public Service Edge).
- **Prioritize DNS Exclusions over Z-Tunnel 2.0**: When enabled, Zscaler Client Connector prioritizes DNS domains in Domain Exclusions over Domain Inclusions. To learn more, see the [How Zscaler Client Connector processes the domain inclusions and exclusions](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#DNS_IP_in_Inclusion) section.
![DNS section on Add Ruleset window](/downloads/zscaler-client-connector/location-based-policies/about-location-based-policies/zclient-connector-add-ruleset-dns.png)
[]Enter the bypasses and IP inclusions and exclusions that apply to the ruleset for traffic steering:
- **Process-Based Application Bypass**: Allows bypassing of [process-based applications](/zscaler-client-connector/adding-process-based-applications-bypass-traffic) that you can use for both Zscaler Tunnel (Z-Tunnel) 1.0 and Z-Tunnel 2.0. Click **Select All** or select applications from the drop-down menu.
- **Predefined IP-Based Application Bypass**: Allows bypassing of [predefined IP-based applications](/zscaler-client-connector/about-application-bypass-info). Click **Select All** or select applications from the drop-down menu.
- **Custom IP-Based Application Bypass**: Allows bypassing of [custom IP-based applications](/zscaler-client-connector/adding-ip-based-applications-bypass-traffic) that you can use for Z-Tunnel 2.0. Click **Select All** or select applications from the drop-down menu.
- **IP Exclusion List**: Select a list of IP addresses from the [Traffic Steering IP Lists](/zscaler-client-connector/adding-traffic-steering-ip-list) tab to exclude, or keep the default value of `Default IP Exclusion List` to use the default exclusion list on the tab.
- **IP Inclusion List**: Select a list of IP addresses from the [Traffic Steering IP Lists](/zscaler-client-connector/adding-traffic-steering-ip-list) tab to include, or keep the default value of `Default IP Inclusion List` to use the default inclusion list on the tab.
-
**Source Port-Based Bypass**: Enter the source port and protocol from which Zscaler Client Connector bypasses existing inbound traffic. The port value can range from `1` to `65535`. The protocol value is `TCP`, `UDP`, or `*`.
Zscaler recommends you use endpoint firewall rules instead of a source port-based bypass because rules are stateful.
![Global Bypasses and IP Inclusions/Exclusions section on Add Ruleset window](/downloads/zscaler-client-connector/location-based-policies/about-location-based-policies/zclient-connector-add-ruleset-bypasses.png)
[]Configure the endpoint firewall rule for inbound traffic:
- **Rule Order**: Select the appropriate rule order value from the drop-down menu. The rule order determines the processing order within the ruleset. Precedence is based on ascending numerical order.
- **Firewall IP List**: Select the criteria to apply the inbound firewall rule to:
- **Any**: Apply to any IP address, port, and protocol.
- **Local subnet**: Apply to the subnet range into which the device falls. The local subnet is auto-detected and Zscaler Client Connector creates both IPv4 (multicast address) and IPv6 (link-local IP and multicast address) filters based on the subnet.
- **<IP List name>**: Apply to the selected Firewall IP list from the [Firewall IP Lists](/zscaler-client-connector/adding-firewall-ip-list) tab.
- **Application**: Select the application from the [Applications](/zscaler-client-connector/adding-application-ruleset) tab that the inbound firewall rule applies to, or select **Any **to apply it to all applications.
- **Action**: Select the action for the rule:
- **Firewall Allow**: Allow inbound traffic that matches the rule.
- **Firewall Block**: Block inbound traffic that matches the rule.
You must select at least one Firewall IP List or Application. To reset to the default configuration, click **Restore Default**. You can click **Add Rule** to enter up to a maximum of 10 rules. Each new rule displays under the previously added one.
![Inbound Firewall Rules section on Add Ruleset window](/downloads/zscaler-client-connector/location-based-policies/about-location-based-policies/zclient-connector-add-ruleset-inbound.png)
- []**Action**: Select the action that the filter applies to inbound traffic that doesn’t match any inbound firewall rules in the ruleset:
- **None**: Use the existing firewall policy (e.g., Windows Defender). This is the default value.
- **Firewall Allow**: Allow inbound traffic that doesn’t match the inbound firewall rules in the ruleset.
-
**Firewall Block**: Block inbound traffic that doesn’t match the inbound firewall rules in the ruleset.
This action does not apply to loopback traffic as loopback traffic is always allowed.
- **Allow ZPA Client to Client Traffic**: Select this option to allow inbound access for Zscaler Private Access (ZPA) client-to-client traffic (e.g., client-based remote assistance) even if all other inbound traffic is blocked. To learn more, see [Understanding Client-to-Client Connectivity](/zpa/understanding-client-client-connectivity).
![Default Inbound Firewall Rule section on Add Ruleset window](/downloads/zscaler-client-connector/location-based-policies/about-location-based-policies/zclient-connector-add-ruleset-default-inbound.png)
[]Configure the endpoint firewall rule for outbound traffic:
- **Rule Order**: Select the appropriate rule order value from the drop-down menu. The rule order determines the processing order within the ruleset. Precedence is based on ascending numerical order.
- **Firewall IP List**: Select the criteria to apply the outbound firewall rule to:
- **Any**: Apply to any IP address, port, and protocol.
- **Local subnet**: Apply to the subnet range into which the device falls. The local subnet is auto-detected and Zscaler Client Connector creates both IPv4 (multicast address) and IPv6 (link-local IP and multicast address) filters based on the subnet.
- **<IP List name>**: Apply to the selected Firewall IP list from the [Firewall IP Lists](/zscaler-client-connector/adding-firewall-ip-list) tab.
- **Application**: Select the application from the [Applications](/zscaler-client-connector/adding-application-ruleset) tab that the outbound firewall rule applies to or select **Any **to apply it to all applications.
- **Action**: Select the action for the rule:
- **Firewall Allow**: Allow outbound traffic that matches the rule.
-
**Firewall Block**: Block outbound traffic that matches the rule.
This action does not apply to loopback traffic as loopback traffic is always allowed.
You must select at least one Firewall IP List or Application. To reset to the default configuration, click **Restore Default**. You can click **Add Rule** to enter up to a maximum of 10 rules. Each new rule displays under the previously added one.
![Outbound Firewall Rules section on Add Ruleset window](/downloads/zscaler-client-connector/location-based-policies/about-location-based-policies/zclient-connector-add-ruleset-outbound.png)
- []**Action**: Select the action that the filter applies to inbound traffic that doesn’t match any of the outbound firewall rules:
-
**None**: Use the existing firewall policy (e.g., Windows Defender). This is the default value.
If your host default outbound firewall rule is set to deny, you must ensure that the host firewall allows outbound traffic to your IdP.
- **Firewall Allow**: Allow outbound traffic that doesn’t match the outbound firewall rules in the ruleset. You must select this option if a ruleset includes any outbound firewall rules.
![Default Outbound Firewall Rule section on Add Ruleset window](/downloads/zscaler-client-connector/location-based-policies/about-location-based-policies/zclient-connector-add-ruleset-default-outbound.png)