# Configuring Forwarding Policy
Source: https://help.zscaler.com/unified/configuring-forwarding-policy
PDF: https://help.zscaler.com/pdf/com/en/1497031.pdf

Zscaler uses forwarding control policies to forward selective Zscaler traffic to specific endpoints. You can configure your forwarding policy with appropriate rules to forward your web traffic to specific destinations directly, through a third-party proxy service, or through a Zscaler-assigned dedicated IP address or GeoIP address. You can also configure rules to forward application traffic to a Zscaler Private Applications App Connector.
You can configure forwarding rules for the following use cases:
- [Configuring Forwarding Rules for Proxy Chaining](#proxy-chaining)
- [Configuring Forwarding Rules for Private Applications](#source-ip-anchoring)
- [Configuring Forwarding Rules for Dedicated IP](#dedicated-Ip)
- [Configuring Forwarding Rules for GeoIP](#geo-ip)
- Any Forwarding Control policy (including Source IP Anchoring) based on user conditions such as users, groups, and departments requires a subscription to the Advanced Firewall.
- You can create up to 1,024 forwarding rules.
[]You can use forwarding policies to configure appropriate rules for traffic that needs to be forwarded to a third-party proxy service of your choice.
To configure a forwarding rule for third-party proxy chaining:
- Go to **Infrastructure** > **Internet & SaaS** > **Network Policies** > **Forwarding Control Policy**.
-
Click **Add Forwarding Rule**.
The** Add Forwarding Rule** window appears.
- Under the **Forwarding Rule** section, configure the following rule attributes:
- **Rule Order**: Enter the order of the rule. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value based on your requirements. However, if you've enabled Admin Rank, your assigned admin rank determines the rule order values you can select.
- **Rule Name**: Enter a user-friendly name for the rule. The Forwarding Control automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Admin Rank:** Enter a value from 0-7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule's Admin Rank determines the value you can select in Rule Order, so that a rule with a higher Admin Rank always precedes a rule with a lower Admin Rank.
- **Rule Status**: Enable this option to enforce the rule actively. Disabling this option does not actively enforce the rule and the service skips it and moves to the next rule. However, the rule does not lose its place in the rule order.
- **Rule Label**: Select a rule label to associate with the rule. To learn more, see [About Rule Labels](/unified/about-rule-labels).
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
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
-
[]**Location/Sublocation**: Select **Any** to apply the rule to all locations, or select up to 8 locations. You can also search for a location or click the **Add** icon to add a new location. To apply this rule to unauthenticated traffic, the rule must apply to all locations.
- If you want to use the IP address mentioned in the XFF header, use this option instead of the **Source IPs Groups** option under the **Source** criteria because the sublocation is used to detect the source IP addresses based on the XFF header.
- If you want to apply this rule only to remote users’ traffic, select **Road Warrior** from the Locations field. Rules configured for locations other than **Road Warrior** also apply to remote user traffic from those locations.
The rules configured for the Road Warrior location apply to Z-Tunnel 1.0 and PAC only when the **Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors** option is enabled in [Advanced Settings](/unified/configuring-advanced-settings#firewall-remote-users).
- **Location Groups**: Select **Any** to apply the rule to all location groups, or select up to 32 location groups.
- **Users**: Select **Any** to apply the rule to all users, select **General Users** to apply the rule to all authenticated users, or select **Special Users** to apply the rule to all unauthenticated user policies. You can also manually select up to 32 general or special users. You can search for users or click the **Add** icon to add a new user.
- **Groups**: Select **Any** to apply the rule to all groups, or select up to 32 groups. You can search for groups or click the **Add** icon to add a new group.
-
**Departments**: Select **Any** to apply the rule to all departments, or select up to 32 departments. If you've enabled the unauthenticated user policy, you can select **Special Departments** to apply this rule to all unauthenticated transactions. You can search for departments or click the **Add** icon to add a new department.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, or **Departments**.
-
**Device Groups**: Select the [device groups](/unified/about-device-groups-internet-saas) to which the rule applies. For Zscaler Client Connector traffic, select the appropriate group based on the device platform. Select **Cloud Browser Isolation**, **IoT**, or** No Client Connector** to apply the rule to Isolation traffic, IoT traffic, or traffic that is not tunneled through Zscaler Client Connector, respectively. You can also search for a device group. Selecting no value ignores this criterion in the policy evaluation.
The** Cloud Browser Isolation** and** IoT** groups are available only if Isolation and IoT discovery are enabled for your organization.
- []**Network Service**: Select **Any** to apply the rule to all network services or select specific network services. The Zscaler Firewall has predefined services, and you can configure up to 832 additional custom services.
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
[]**URL Category**: To identify destinations based on the domain's URL category, select any number of categories.
You can also select [custom TLD categories](/unified/about-tld-categories) from this field.
-
**Destination IP Address/Wildcard FQDN**: Enter IP addresses (IPv4 only) or fully qualified domain names (FQDNs), if the domain has multiple destination IP addresses or if its IP addresses might change. You can also enter wildcard FQDNs using an asterisk (*) as the wildcard character. For guidelines on configuring wildcard FQDNs, see [Configuring Destination IP Groups](/unified/configuring-destination-ip-groups). For IP addresses, you can enter individual IP addresses (IPv4 only), subnets, or address ranges. You can specify IP addresses in any of the following formats:
- An individual address, such as 192.0.2.1
- A subnet, such as 192.0.2.0/24
- An address range, such as 192.0.2.1 - 192.0.2.5
If you are adding multiple items, press ****Enter**** after each entry.
- Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
- Forwarding rules based on Wildcard FQDNs require DNS requests from clients to be forwarded to the Zscaler service to evaluate criteria match. To learn how DNS resolution is handled by the Zscaler service, see [Handling DNS Resolution for Various Traffic Forwarding Methods](/unified/handling-dns-resolution-various-traffic-forwarding-methods).
- **Destination IPv4 Groups**: Select the [destination IPv4 groups](/unified/configuring-destination-ip-groups) that you want to control with this rule. You can also add a new Destination IPv4 Group by clicking the **Add **icon.
-
**Destination IPv6 Groups**: To control destination IPv6 addresses with this rule, select the **All IPv6** Group, which is the default destination IPv6 group for all IPv6 addresses.
Custom destination IPv6 groups are not currently supported. To learn more, see [About Destination IP Groups](/unified/about-destination-ip-groups).
- **Destination Country**: To identify destinations based on the location of a server, select Any to apply the rule to all countries or select the countries to which you want to control traffic.
[]You can configure forwarding policies to forward Internet & SaaS traffic through Private Applications for scanning internal applications and source IP anchoring and for inspecting traffic of certain Private Applications application segments with Internet & SaaS. Zscaler provides a predefined forwarding rule, ZIA Inspected ZPA Apps, which is enabled by default. This rule forwards all Private Applications application segment traffic for Internet & SaaS inspection that has the **Inspect Traffic with ZIA** field enabled in the Admin Portal. You cannot edit this rule.
The predefined rule is available if you have ZPA App Inspection. For further assistance, contact Zscaler Support.
To configure a forwarding rule for Private Applications:
- Go to **Infrastructure** > **Internet & SaaS** > **Network Policies** > **Forwarding Control Policy**.
-
Click **Add Forwarding Rule**.
The** Add Forwarding Rule** window appears.
- Under the **Forwarding Rule** section, configure the following rule attributes:
- **Rule Order**: Enter the order of the rule. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value based on your requirements. However, if you've enabled Admin Rank, your assigned admin rank determines the rule order values you can select.
- **Rule Name**: Enter a user-friendly name for the rule. The Forwarding Control automatically creates a rule name, which you can change. The maximum length is 63 characters.
- **Admin Rank:** Enter a value from 0-7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule's Admin Rank determines the value you can select in Rule Order, so that a rule with a higher Admin Rank always precedes a rule with a lower Admin Rank.
- **Rule Status**: Enable this option to enforce the rule actively. Disabling this option does not actively enforce the rule and the service skips it and moves to the next rule. However, the rule does not lose its place in the rule order.
- **Rule Label**: Select a rule label to associate with the rule. To learn more, see [About Rule Labels](/unified/about-rule-labels).
-
**Forwarding Method**: Select the forwarding method to be used for this rule. Choose **ZPA** to forward the traffic to a Private Applications App Connector via the Private Applications cloud.
If you select **Direct**, Zscaler forwards the traffic directly to the destination server using the Zscaler service IP address.
- Under the following tabs, configure the appropriate rule attributes:
- [General](#general-source-IP-anchoring)
- [Source](#source-source-IP-anchoring)
- [Applications](#applications-source-IP-anchoring)
- [Destination](#destination-source-IP-anchoring)
-
From the **Forward to ZPA Gateway** drop-down menu, choose the appropriate Private Applications gateway. To configure a Private Applications gateway, see [Configuring ZPA Gateway](/unified/configuring-zpa-gateway).
This field is enabled only if you have selected application segments that require Source IP Anchoring in the Application Segment field, and those application segments are associated with a common Private Applications gateway. An empty list indicates that there is no common gateway configured for the selected application segments.
- (Optional) Enter a description of the rule in the **Description** field.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
-
[]**Location/Sublocation**: Select **Any** to apply the rule to all locations, or select up to 8 locations. You can also search for a location or click the **Add** icon to add a new location. To apply this rule to unauthenticated traffic, the rule must apply to all locations.
- If you want to use the IP address mentioned in the XFF header, use this option instead of the **Source IPs Groups** option under the **Source** criteria because the sublocation is used to detect the source IP addresses based on the XFF header.
- If you want to apply this rule only to remote users’ traffic, select **Road Warrior** from the Locations field. Rules configured for locations other than **Road Warrior** also apply to remote user traffic from those locations.
The rules configured for the Road Warrior location apply to Z-Tunnel 1.0 and PAC only when the **Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors** option is enabled in [Advanced Settings](/unified/configuring-advanced-settings#firewall-remote-users).
- **Location Groups**: Select **Any** to apply the rule to all location groups, or select up to 32 location groups.
- **Users**: Select **Any** to apply the rule to all users, select **General Users** to apply the rule to all authenticated users, or select **Special Users** to apply the rule to all unauthenticated user policies. You can also manually select up to 4 general or special users. You can search for users or click the **Add** icon to add a new user.
- **Groups**: Select **Any** to apply the rule to all groups, or select up to 8 groups. You can search for groups or click the **Add** icon to add a new group.
-
**Departments**: Select **Any** to apply the rule to all departments, or select any number of departments. If you've enabled the unauthenticated user policy, you can select **Special Departments** to apply this rule to all unauthenticated transactions. You can search for departments or click the **Add** icon to add a new department.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, or **Departments**.
-
**Device Groups**: Select the [device groups](/unified/about-device-groups-internet-saas) to which the rule applies. For Zscaler Client Connector traffic, select the appropriate group based on the device platform. Select **Cloud Browser Isolation**, **IoT**, or** No Client Connector** to apply the rule to Isolation traffic, IoT traffic, or traffic that is not tunneled through Zscaler Client Connector, respectively. You can also search for a device group. Selecting no value ignores this criterion in the policy evaluation.
The** Cloud Browser Isolation** and** IoT** groups are available only if Isolation and IoT discovery are enabled for your organization.
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
- []**Application Service Groups**: Select any number of application service groups to which the rule applies.
- []**Application Segment**: Select the appropriate application segments that require Source IP Anchoring.
[]You can use forwarding policies to configure appropriate rules to forward traffic through the dedicated IP gateways to the destinations of your choice. To learn more about dedicated IP, see [Understanding Zscaler-Managed Dedicated IP](/unified/understanding-zscaler-managed-dedicated-ip).
To configure a forwarding rule for dedicated IP:
- Go to **Infrastructure** > **Internet & SaaS** > **Network Policies** > **Forwarding Control Policy**.
-
Click **Add Forwarding Rule**.
The** Add Forwarding Rule** window appears.
- Under the **Forwarding Rule** section, configure the following rule attributes:
- **Rule Order**: Enter the order of the rule. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value based on your requirements. However, if you've enabled **Admin Rank**, your assigned admin rank determines the rule order values you can select.
- **Rule Name**: Enter a user-friendly name for the rule. The Forwarding Control automatically creates a rule name, which you can change. The maximum length is 63 characters.
- **Rule Status**: Enable this option to enforce the rule actively. Disabling this option does not actively enforce the rule and the service skips it and moves to the next rule. However, the rule does not lose its place in the rule order.
- **Rule Label**: Select a rule label to associate with the rule. To learn more, see [About Rule Labels](/unified/about-rule-labels).
-
**Forwarding Method**: Select the forwarding method to be used for this rule. Choose **Dedicated IP** to forward the traffic through a dedicated IP gateway.
If you select **Direct**, Zscaler forwards the traffic directly to the destination server using the Zscaler service IP address.
- Under the following tabs, configure the appropriate rule attributes:
- [General](#general-dedicated-ip)
- [Services](#services-dedicated-ip)
- [Applications](#applications-dedicated-ip)
- [Source](#source-dedicated-ip)
- [Destination](#destination-dedicated-ip)
- From the **Forward to Gateway** drop-down menu, choose the appropriate dedicated IP gateway. Select **Default** gateway to allow the Zscaler service to automatically choose the optimal data center based on your location. To configure a dedicated IP gateway, see [Configuring Dedicated IP Gateways](/unified/configuring-dedicated-ip-gateways).
- (Optional) In the **Description** field, enter a description of the rule.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
-
[]**Location/Sublocation**: Select **Any** to apply the rule to all locations, or select up to 8 locations. You can also search for a location or click the **Add** icon to add a new location. To apply this rule to unauthenticated traffic, the rule must apply to all locations.
- If you want to use the IP address mentioned in the XFF header, use this option instead of the **Source IPs Groups** option under the **Source** criteria because the sublocation is used to detect the source IP addresses based on the XFF header.
- If you want to apply this rule only to remote users’ traffic, select **Road Warrior** from the Locations field. Rules configured for locations other than **Road Warrior** also apply to remote user traffic from those locations.
The rules configured for the Road Warrior location apply to Z-Tunnel 1.0 and PAC only when the **Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors** option is enabled in [Advanced Settings](/unified/configuring-advanced-settings#firewall-remote-users).
- **Location Groups**: Select **Any** to apply the rule to all location groups, or select up to 32 location groups.
- **Users**: Select **Any** to apply the rule to all users, select **General Users** to apply the rule to all authenticated users, or select **Special Users** to apply the rule to all unauthenticated user policies. You can also manually select up to 4 general or special users. You can search for users or click the **Add** icon to add a new user.
- **Groups**: Select **Any** to apply the rule to all groups, or select up to 8 groups. You can search for groups or click the **Add** icon to add a new group.
-
**Departments**: Select **Any** to apply the rule to all departments, or select any number of departments. If you've enabled the unauthenticated user policy, you can select **Special Departments** to apply this rule to all unauthenticated transactions. You can search for departments or click the **Add** icon to add a new department.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, or **Departments**.
-
**Device Groups**: Select the [device groups](/unified/about-device-groups-internet-saas) to which the rule applies. For Zscaler Client Connector traffic, select the appropriate group based on the device platform. Select **Cloud Browser Isolation**, **IoT**, or** No Client Connector** to apply the rule to Isolation traffic, IoT traffic, or traffic that is not tunneled through Zscaler Client Connector, respectively. You can also search for a device group. Selecting no value ignores this criterion in the policy evaluation.
The** Cloud Browser Isolation** and** IoT** groups are available only if Isolation and IoT discovery are enabled for your organization.
- []**Network Service**: Select **Any** to apply the rule to all network services or select specific network services. The Zscaler Firewall has predefined services, and you can configure up to 832 additional custom services.
- **Network Service Group**: Select any number of predefined or custom network service groups to which the rule applies.
- []**Application Service Groups**: Select any number of application service groups to which the rule applies.
- []**Source IPv4 Groups**: Select the [source IPv4 groups](/unified/about-source-ip-groups-internet-saas) that you want to control with this rule. You can also add a new Source IPv4 Group by clicking the **Add **icon.
-
**Source IPv6 Groups**: To control source IPv6 addresses with this rule, select the **All IPv6** group, which is the default source IPv6 group for all IPv6 addresses.
Custom source IPv6 groups are not currently supported. To learn more, see [About Source IP Groups](/unified/about-source-ip-groups-internet-saas).
-
**IP Addresses**: Enter the source IP address (IPv4 only) in any of the following formats:
- An individual address, such as 192.0.2.1
- A subnet, such as 192.0.2.0/24
- An address range, such as 192.0.2.1 - 192.0.2.5
Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
-
[]**URL Category**: To identify destinations based on the domain's URL category, select any number of categories.
You can also select [custom TLD categories](/unified/about-tld-categories) from this field.
-
**Destination IP Address/Wildcard FQDN**: Enter IP addresses (IPv4 only) or FQDNs, if the domain has multiple destination IP addresses or if its IP addresses might change. You can also enter wildcard FQDNs using an asterisk (*) as the wildcard character. For guidelines on configuring wildcard FQDNs, see [Configuring Destination IP Groups](/unified/configuring-destination-ip-groups-internet-saas). For IP addresses, you can enter individual IP addresses (IPv4 only), subnets, or address ranges. You can specify IP addresses in any of the following formats:
- An individual address, such as 192.0.2.1
- A subnet, such as 192.0.2.0/24
- An address range, such as 192.0.2.1 - 192.0.2.5
If you are adding multiple items, press `Enter` after each entry.
- Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
- Forwarding rules based on Wildcard FQDNs require DNS requests from clients to be forwarded to the Zscaler service to evaluate criteria match. To learn how DNS resolution is handled by the Zscaler service, see [Handling DNS Resolution for Various Traffic Forwarding Methods](/unified/handling-dns-resolution-various-traffic-forwarding-methods).
- **Destination IPv4 Groups**: Select the [destination IPv4 groups](/unified/configuring-destination-ip-groups-internet-saas) that you want to control with this rule. You can also add a new Destination IPv4 Group by clicking the **Add **icon.
-
**Destination IPv6 Groups**: To control destination IPv6 addresses with this rule, select the **All IPv6** Group, which is the default destination IPv6 group for all IPv6 addresses.
Custom destination IPv6 groups are not currently supported. To learn more, see [About Destination IP Groups](/unified/about-destination-ip-groups-internet-saas).
- **Destination Country**: To identify destinations based on the location of a server, select **Any** to apply the rule to all countries or select the countries to which you want to control traffic.
[]You can use forwarding policies to configure appropriate rules to forward traffic using Zscaler GeoIP address that is mapped to the location from where the traffic originates.
Some applications allow access only if the traffic originates from specific countries where Zscaler's data center might not be present. In such cases, organizations can use the GeoIP forwarding policies to forward traffic with a source IP address that is mapped to the originating country. To learn more about GeoIP, see [Understanding Geolocalization IP](/unified/understanding-geolocalization-ip).
To configure a forwarding rule for GeoIP:
- Go to **Infrastructure** > **Internet & SaaS** > **Network Policies** > **Forwarding Control Policy**.
-
Click **Add Forwarding Rule**.
The** Add Forwarding Rule** window appears.
- Under the **Forwarding Rule** section, configure the following rule attributes:
- **Rule Order**: Enter the order of the rule. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value based on your requirements. However, if you've enabled **Admin Rank**, your assigned admin rank determines the** **rule order values you can select.
- **Rule Name**: Enter a user-friendly name for the rule. The Forwarding Control automatically creates a rule name, which you can change. The maximum length is 63 characters.
- **Rule Status**: Enable this option to enforce the rule actively. Disabling this option does not actively enforce the rule and the service skips it and moves to the next rule. However, the rule does not lose its place in the rule order.
- **Rule Label**: Select a rule label to associate with the rule. To learn more, see [About Rule Labels](/unified/about-rule-labels).
-
**Forwarding Method**: Select the forwarding method to be used for this rule. Choose **Geo IP** to forward traffic with the source IP address mapped to the location of the originating request.
If you select **Direct**, Zscaler forwards the traffic directly to the destination server using the Zscaler service IP address.
- Under the following tabs, configure the appropriate rule attributes:
- [General](#general-geo-ip)
- [Services](#services-geo-ip)
- [Applications](#applications-geo-ip)
- [Source](#source-geo-ip)
- [Destination](#destination-geo-ip)
- The **Forward to Gateway** field is selected as **Auto** by default. The Zscaler service automatically forwards the traffic with a source IP address mapped to the country from where the traffic originates.
- (Optional) In the **Description** field, enter a description of the rule.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
-
[]**Location/Sublocation**: Select **Any** to apply the rule to all locations, or select up to 8 locations. You can also search for a location or click the **Add** icon to add a new location. To apply this rule to unauthenticated traffic, the rule must apply to all locations.
- If you want to use the IP address mentioned in the XFF header, use this option instead of the **Source IPs Groups** option under the **Source** criteria because the sublocation is used to detect the source IP addresses based on the XFF header.
- If you want to apply this rule only to remote users’ traffic, select **Road Warrior** from the Locations field. Rules configured for locations other than **Road Warrior** also apply to remote user traffic from those locations.
The rules configured for the Road Warrior location apply to Z-Tunnel 1.0 and PAC only when the **Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors** option is enabled in [Advanced Settings](/unified/configuring-advanced-settings#firewall-remote-users).
- **Location Groups**: Select **Any** to apply the rule to all location groups, or select up to 32 location groups.
- **Users**: Select **Any** to apply the rule to all users, select **General Users** to apply the rule to all authenticated users, or select **Special Users** to apply the rule to all unauthenticated user policies. You can also manually select up to 32 general or special users. You can search for users or click the **Add** icon to add a new user.
- **Groups**: Select **Any** to apply the rule to all groups, or select up to 32 groups. You can search for groups or click the **Add** icon to add a new group.
-
**Departments**: Select **Any** to apply the rule to all departments, or select any number of departments. If you've enabled the unauthenticated user policy, you can select **Special Departments** to apply this rule to all unauthenticated transactions. You can search for departments or click the **Add** icon to add a new department.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, or **Departments**.
-
**Device Groups**: Select the [device groups](/unified/about-device-groups-internet-saas) to which the rule applies. For Zscaler Client Connector traffic, select the appropriate group based on the device platform. Select **Cloud Browser Isolation**, **IoT**, or** No Client Connector** to apply the rule to Isolation traffic, IoT traffic, or traffic that is not tunneled through Zscaler Client Connector, respectively. You can also search for a device group. Selecting no value ignores this criterion in the policy evaluation.
The** Cloud Browser Isolation** and** IoT** groups are available only if Isolation and IoT discovery are enabled for your organization.
- []**Network Service**: Select **Any** to apply the rule to all network services or select specific network services. The Zscaler Firewall has predefined services, and you can configure up to 832 additional custom services.
- **Network Service Group**: Select any number of predefined or custom network service groups to which the rule applies.
- []**Application Service Groups**: Select any number of application service groups to which the rule applies.
- []**Source IPv4 Groups**: Select the [source IPv4 groups](/unified/about-source-ip-groups-internet-saas) that you want to control with this rule. You can also add a new Source IPv4 Group by clicking the **Add **icon.
-
**Source IPv6 Groups**: To control source IPv6 addresses with this rule, select the **All IPv6** group, which is the default source IPv6 group for all IPv6 addresses.
Custom source IPv6 groups are not currently supported. To learn more, see [About Source IP Groups](/unified/about-source-ip-groups-internet-saas).
-
**IP Addresses**: Enter the source IP address (IPv4 only) in any of the following formats:
- An individual address, such as 192.0.2.1
- A subnet, such as 192.0.2.0/24
- An address range, such as 192.0.2.1 - 192.0.2.5
Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
-
[]**URL Category**: To identify destinations based on the domain's URL category, select any number of categories.
You can also select [custom TLD categories](/unified/about-tld-categories) from this field.
-
**Destination IP Address/Wildcard FQDN**: Enter IP addresses (IPv4 only) or FQDNs, if the domain has multiple destination IP addresses or if its IP addresses might change. You can also enter wildcard FQDNs using an asterisk (*) as the wildcard character. For guidelines on configuring wildcard FQDNs, see [Configuring Destination IP Groups](/unified/configuring-destination-ip-groups-internet-saas). For IP addresses, you can enter individual IP addresses (IPv4 only), subnets, or address ranges. You can specify IP addresses in any of the following formats:
- An individual address, such as 192.0.2.1
- A subnet, such as 192.0.2.0/24
- An address range, such as 192.0.2.1 - 192.0.2.5
If you are adding multiple items, press `Enter` after each entry.
- Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
- Forwarding rules based on Wildcard FQDNs require DNS requests from clients to be forwarded to the Zscaler service to evaluate criteria match. To learn how DNS resolution is handled by the Zscaler service, see [Handling DNS Resolution for Various Traffic Forwarding Methods](/unified/handling-dns-resolution-various-traffic-forwarding-methods).
- **Destination IPv4 Groups**: Select the [destination IPv4 groups](/unified/configuring-destination-ip-groups-internet-saas) that you want to control with this rule. You can also add a new Destination IPv4 Group by clicking the **Add **icon.
-
**Destination IPv6 Groups**: To control destination IPv6 addresses with this rule, select the **All IPv6** Group, which is the default destination IPv6 group for all IPv6 addresses.
Custom destination IPv6 groups are not currently supported. To learn more, see [About Destination IP Groups](/unified/about-destination-ip-groups-internet-saas).
- **Destination Country**: To identify destinations based on the location of a server, select **Any** to apply the rule to all countries or select the countries to which you want to control traffic.