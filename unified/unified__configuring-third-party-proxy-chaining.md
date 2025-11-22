# Configuring Third-Party Proxy Chaining
Source: https://help.zscaler.com/unified/configuring-third-party-proxy-chaining
PDF: https://help.zscaler.com/pdf/com/en/1497731.pdf

The Third-Party Proxy Chaining feature allows Zscaler to forward certain outbound traffic to a specific third-party proxy service. To learn more, see [Understanding Third-Party Proxy Chaining](/unified/understanding-third-party-proxy-chaining).
To configure the third-party proxy chaining feature:
- [Step 1: Configure Proxies for the Third-Party Proxy Service](/unified/configuring-third-party-proxies)
- [Step 2: Create a Gateway for the Proxies Configured](/unified/configuring-gateways-proxies)
- [Step 3: Configure the Forwarding Policies for Third-Party Proxy Chaining Using the Gateways Created](#forwarding-policy)
[]You can use forwarding policies to configure appropriate rules for traffic that needs to be forwarded to a third-party proxy service of your choice.
To configure a forwarding rule for third-party proxy chaining:
- Go to **Infrastructure** > **Internet & SaaS** > **Network Policies** > **Forwarding Control Policy**.
- Click **Add Forwarding Rule**. The** Add Forwarding Rule** window appears.
- Under the **Forwarding Rule** section, configure the following rule attributes:
- **Rule Order**: Enter the order of the rule. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the Rule Order reflects this rule's place in the order. You can change the value based on your requirements. However, if you've enabled Admin Rank, your assigned admin rank determines the Rule Order values you can select.
- **Admin Rank:** Enter a value from 0-7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule's Admin Rank determines the value you can select in Rule Order, so that a rule with a higher Admin Rank always precedes a rule with a lower Admin Rank.
- **Rule Name**: Enter a user-friendly name for the rule. The Forwarding Control automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**: Enable this option to enforce the rule actively. Disabling this option does not actively enforce the rule and the service skips it and moves to the next rule. However, the rule does not lose its place in the Rule Order.
- **Rule Label**: Select a rule label to associate with the rule. To learn more, see [About Rule Label](/unified/about-rule-labels).
-
**Forwarding Method**: Select the forwarding method to be used for this rule. Choose **Proxy Chaining** to forward the traffic to a third-party proxy service.
If you select **Direct**, Zscaler forwards the traffic directly to the destination server using the Zscaler service IP address.
- Under the following tabs, configure the appropriate rule attributes:
- [General](#general-third-party-proxy-chaining)
- [Services](#services-third-party-proxy-chaining)
- [Applications](#applications-third-party-proxy-chaining)
- [Source](#source-third-party-proxy-chaining)
- [Destination](#destination-third-party-proxy-chaining)
- From the **Forward to Proxy Gateway** drop-down menu, choose the appropriate proxy gateway. To configure a proxy gateway, see [Configuring Gateways for Proxies](/unified/configuring-gateways-proxies).
- (Optional) Enter a description for the rule in the **Description** field.
- Click **Save** and activate the change.
-
[]**Location/SubLocation**: Select **Any** to apply the rule to all locations, or select up to 8 locations. You can also search for a location or click the **Add** icon to add a new location. To apply this rule to unauthenticated traffic, the rule must apply to all locations.
- If you want to use the IP address mentioned in the XFF header, use this option instead of the **Source IPs Groups** option under the **Source** criteria because the sublocation is used to detect the source IPs based on the XFF Header.
- If you want to apply this rule only to remote users’ traffic, select **Road Warrior** from the Locations field. Rules configured for locations other than **Road Warrior** also apply to remote user traffic from those locations.
The rules configured for Road Warrior location apply to Z-Tunnel 1.0 and PAC only when the **Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors** option is enabled in [Advanced Settings](/unified/configuring-advanced-settings#firewall-remote-users).
- **Location Group**: Select **Any** to apply the rule to all location groups, or select up to 32 location groups.
- **Users**: Select **Any** to apply the rule to all users, select **General Users** to apply the rule to all authenticated users, or select **Special Users** to apply the rule to all unauthenticated users policy. You can also manually select up to 4 general and/or special users. You can search for users or click the **Add** icon to add a new user.
- **Groups**: Select **Any** to apply the rule to all groups, or select up to 8 groups. You can search for groups or click the **Add** icon to add a new group.
- **Departments**: Select **Any** to apply the rule to all departments, or select any number of departments. If you've enabled the unauthenticated users policy, you can select **Special Departments** to apply this rule to all unauthenticated transactions. You can search for departments or click the **Add** icon to add a new department.
- []**Network Service**: Select **Any** to apply the rule to all network services or select specific network services. The Zscaler Firewall has predefined services and you can configure up to 832 additional custom services.
- **Network Service Group**: Select any number of predefined or custom **network service groups** to which the rule applies.
- []**Application Service Groups**: Select any number of application service groups to which the rule applies.
- []**Source IPv4 Groups**: Select the [source IPv4 groups](/unified/about-source-ip-groups) that you want to control with this rule. You can also add a new Source IPv4 Group by clicking the **Add **icon.
-
**Source IPv6 Groups**: To control source IPv6 addresses with this rule, select the **All IPv6** group, which is the default source IPv6 group for all IPv6 addresses.
Custom source IPv6 groups are not currently supported. To learn more, see [About Source IP Groups](/unified/about-source-ip-groups).
-
**IP Addresses**: Enter the source IP address (IPv4 only) in any of the following formats:
- An individual address, such as 192.0.2.1
- A subnet, such as 192.0.2.0/24
- An address range, such as 192.0.2.1 - 192.0.2.5
Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
-
[]**URL Category**: To identify destinations based on the URL category of the domain, select any number of categories.
You can also select [custom TLD categories](/unified/about-tld-categories) from this field.
-
**Destination IP Address / Wildcard FQDN**: Enter IP addresses (IPv4 only) or fully qualified domain names (FQDNs), if the domain has multiple destination IP addresses or if its IP addresses may change. You can also enter wildcard FQDNs using an asterisk (*) as the wildcard character. For guidelines to configure wildcard FQDNs, see [Configuring Destination IP Groups](/unified/configuring-destination-ip-groups). For IP addresses, you can enter individual IP addresses (IPv4 only), subnets, or address ranges. You can specify IP addresses in any of the following formats:
- An individual address, such as 192.0.2.1
- A subnet, such as 192.0.2.0/24
- An address range, such as 192.0.2.1 - 192.0.2.5
If you are adding multiple items, hit ****Enter**** after each entry.
- Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
- Forwarding rules based on Wildcard FQDNs require DNS requests from clients to be forwarded to the Zscaler service to evaluate criteria match. To learn how DNS resolution is handled by the Zscaler service, see [Handling DNS Resolution for Various Traffic Forwarding Methods](/unified/handling-dns-resolution-various-traffic-forwarding-methods).
- **Destination IPv4 Groups**: Select the [destination IPv4 groups](/unified/configuring-destination-ip-groups) that you want to control with this rule. You can also add a new Destination IPv4 Group by clicking the **Add **icon.
-
**Destination IPv6 Groups**: To control destination IPv6 addresses with this rule, select the **All IPv6** Group, which is the default destination IPv6 group for all IPv6 addresses.
Custom destination IPv6 groups are not currently supported. To learn more, see [About Destination IP Groups](/unified/about-destination-ip-groups).
- **Destination Country**: To identify destinations based on the location of a server, select Any to apply the rule to all countries or select the countries to which you want to control traffic.