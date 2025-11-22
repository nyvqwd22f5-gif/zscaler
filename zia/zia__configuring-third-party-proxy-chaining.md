# Configuring Third-Party Proxy Chaining
Source: https://help.zscaler.com/zia/configuring-third-party-proxy-chaining
PDF: https://help.zscaler.com/pdf/com/en/1401556.pdf

The Third-Party Proxy Chaining feature allows Zscaler to forward certain outbound traffic to a specific third-party proxy service. To learn more, see [Understanding Third-Party Proxy Chaining](/zia/about-third-party-proxy-chaining).
To configure the third-party proxy chaining feature:
- [Step 1: Configure Proxies for the Third-Party Proxy Service](#proxy)
- [Step 2: Create a Gateway for the Proxies Configured](#gateway)
- [Step 3: Configure the Forwarding Policies for Third-Party Proxy Chaining Using the Gateways Created](#forwarding-policy)
[]
You can create gateway objects to configure the [Third-Party Proxy Chaining](/zia/about-third-party-proxy-chaining) feature which enables you to forward traffic to a third-party proxy service. A proxy gateway allows you to define a primary proxy and a secondary proxy to which the traffic can be forwarded from Zscaler and define how traffic should be handled when both the proxies are not reachable. You can also define if SSL inspection should be performed on the proxy chain traffic or not.
To configure a proxy gateway for the third-party proxy service:
- Go to **Administration** >** Proxies & Gateways **page.
- Select the **Proxy** **Gateways** tab.
- Click **Add Gateway for Proxies**. The **Add Gateway for Proxies** window appears.
- Enter the following information:
- **Gateway Name**: Enter a user-friendly name for the gateway to be created for a third party proxy service.
- **Fail Close**: Choose how to handle the traffic when both primary and secondary proxies defined in this gateway are unreachable:
- **Enable**: (Default) Drops the traffic when both proxies are unreachable.
- **Disable**: Allows the traffic directly to the web server without forwarding it to the proxy service when both proxies are unreachable.
- **Primary Proxy**: Select the primary proxy for the gateway. For information on configuring a proxy, see [Configuring Third-Party Proxies](/zia/configuring-third-party-proxies).
- **Secondary Proxy**: Select the secondary proxy for the gateway. This is used when the primary proxy is unreachable.
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 256 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
You can create up to 32 gateway objects.
[]
You can configure proxy objects using the IP address or FQDN of a third-party proxy service to which you want to forward the traffic using the [Third-Party Proxy Chaining](/zia/about-third-party-proxy-chaining) feature.
To configure a proxy:
- Go to **Administration** >** Proxies & Gateways **page.
- Select the **Proxies** tab.
- Click **Add Proxy**. The **Add Proxy** window appears.
- In the **Add Proxy** window:
- **Proxy Name**:** **Enter a user-friendly name for the third-party proxy that you are defining.
- **IP/FQDN**:** **Enter the IP address or the FQDN of the third-party proxy service.
- **Port**: Enter the port number on which the third-party proxy service listens to the requests forwarded from Zscaler.
- **Root Certificate**: (Optional) Select the root certificate used by the third-party proxy to perform SSL inspection. This root certificate is used by Zscaler to validate the SSL leaf certificates signed by the upstream proxy. The required root certificate appears in this drop-down list only if it is uploaded from the **Administration **> **Root Certificates** page. To learn more, see [Adding Third-Party SSL Root Certificates](/zia/adding-third-party-ssl-root-certificates).
-
**Insert X-Authenticated-User**: Enable to automatically insert authenticated user ID to the HTTP header, X-Authenticated-User. This field is disabled by default.
This allows the upstream proxies to consume authenticated user ID information from the X-Authenticated-User header value, avoiding re-authentication of users.
For unauthenticated user traffic, the service inserts the value Unknown to the X-Authenticated-User header. Ensure that the third-party proxy servers are configured to re-authenticate the users if the user ID value is Unknown in the HTTP header request.
- **Enable Base64 Encoding for X-Authenticated-User Value**: If you enabled **Insert X-Authenticated-User**, select this option to encode the user ID using the base64 encoding method.
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 256 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
You can configure up to eight proxy objects.
[]
You can use forwarding policies to configure appropriate rules for traffic that needs to be forwarded to a third-party proxy service of your choice.
To configure a forwarding rule for third-party proxy chaining:
- Go to **Policy** > **Forwarding Control**.
-
Click **Add Forwarding Rule**.
The **Add Forwarding Rule** window appears.
- In the **Add Forwarding Rule** window, configure the following rule attributes:
- **Rule Order**: Enter the order of the rule. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value based on your requirements. However, if you've enabled [Admin Rank](/zia/about-admin-rank), your assigned admin rank determines the rule order values you can select.
- **Rule Name**: Enter a user-friendly name for the rule. The Forwarding Control automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**: Enable this option to enforce the rule actively. Disabling this option does not actively enforce the rule and the service skips it and moves to the next rule. However, the rule does not lose its place in the rule order.
- **Rule Label**: Select a rule label to associate with the rule. To learn more, see [About Rule Labels](/zia/about-rule-labels).
-
**Forwarding Method**: Select the forwarding method to be used for this rule. Choose **Proxy Chaining** to forward the traffic to a third-party proxy service.
If you select **Direct**, Zscaler forwards the traffic directly to the destination server using the Zscaler service IP address.
- Under the following tabs, configure the appropriate rule attributes:
- [General](#general-third-party-proxy-chaining)
- [Services](#services-third-party-proxy-chaining)
- [Applications](#applications-third-party-proxy-chaining)
- [Source](#source-third-party-proxy-chaining)
- [Destination](#destination-third-party-proxy-chaining)
- From the **Forward to Proxy Gateway** drop-down menu, choose the appropriate proxy gateway. To configure a proxy gateway, see [Configuring Gateways for Proxies](/zia/configuring-gateways-proxies).
- **Description**: (Optional) Enter a description of the rule.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
-
[]**Location/Sublocation**: Select **Any** to apply the rule to all locations, or select up to 32 locations. You can also search for a location or click the **Add** icon to add a new location. To apply this rule to unauthenticated traffic, the rule must apply to all locations.
- If you want to use the IP address mentioned in the XFF header, use this option instead of the **Source IPs Groups** option under the **Source** criteria because the sublocation is used to detect the source IP addresses based on the XFF header.
- If you want to apply this rule only to remote users’ traffic, select **Road Warrior** from the **Locations** field. Rules configured for locations other than **Road Warrior** also apply to remote user traffic from those locations.
The rules configured for the Road Warrior location apply to Z-Tunnel 1.0 and PAC only when the **Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors** option is enabled in [Advanced Settings](/zia/about-advanced-settings#firewall-remote-users).
- **Location Groups**: Select **Any** to apply the rule to all location groups, or select up to 32 location groups.
- **Users**: Select **Any** to apply the rule to all users, select **General Users** to apply the rule to all authenticated users, or select **Special Users** to apply the rule to all unauthenticated user policies. You can also manually select up to 32 general or special users. You can search for users or click the **Add** icon to add a new user.
- **Groups**: Select **Any** to apply the rule to all groups, or select up to 32 groups. You can search for groups or click the **Add** icon to add a new group.
-
**Departments**: Select **Any** to apply the rule to all departments, or select up to 32 departments. If you've enabled the unauthenticated user policy, you can select **Special Departments** to apply this rule to all unauthenticated transactions. You can search for departments or click the **Add** icon to add a new department.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, **Departments**, or **Locations**.
-
**Device Groups**: Select the [device groups](/zia/about-device-groups) to which the rule applies. For Zscaler Client Connector traffic, select the appropriate group based on the device platform. Select **Cloud Browser Isolation**, **IoT**, or** No Client Connector** to apply the rule to Isolation traffic, IoT traffic, or traffic that is not tunneled through Zscaler Client Connector, respectively. You can also search for a device group. Selecting no value ignores this criterion in the policy evaluation.
The** Cloud Browser Isolation** and** IoT** groups are available only if Isolation and IoT discovery are enabled for your organization.
- []**Network Service**: Select **Any** to apply the rule to all network services or select specific network services. The Zscaler Firewall has predefined services, and you can configure up to 832 additional custom services.
- **Network Service Group**: Select any number of predefined or custom network service groups to which the rule applies.
- []**Application Service Groups**: Select any number of application service groups to which the rule applies.
- []**Source IPv4 Groups**: Select the [source IPv4 groups](/zia/about-source-ip-groups) that you want to control with this rule. You can also add a new Source IPv4 Group by clicking the **Add **icon.
-
**Source IPv6 Groups**: To control source IPv6 addresses with this rule, select the **All IPv6** group, which is the default source IPv6 group for all IPv6 addresses.
Custom source IPv6 groups are not currently supported. To learn more, see [About Source IP Groups](/zia/about-source-ip-groups).
-
**IP Addresses**: Enter the source IP address (IPv4 only) in any of the following formats:
- An individual address, such as 192.0.2.1
- A subnet, such as 192.0.2.0/24
- An address range, such as 192.0.2.1 - 192.0.2.5
Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
-
[]**URL Category**: To identify destinations based on the domain's URL category, select any number of categories.
You can also select [custom TLD categories](/zia/about-tld-categories) from this field.
-
**Destination IP Address/Wildcard FQDN**: Enter IP addresses (IPv4 only) or FQDNs, if the domain has multiple destination IP addresses or if its IP addresses might change. You can also enter wildcard FQDNs using an asterisk (*) as the wildcard character. For guidelines on configuring wildcard FQDNs, see [Configuring Destination IP Groups](/zia/configuring-destination-ip-groups). For IP addresses, you can enter individual IP addresses (IPv4 only), subnets, or address ranges. You can specify IP addresses in any of the following formats:
- An individual address, such as 192.0.2.1
- A subnet, such as 192.0.2.0/24
- An address range, such as 192.0.2.1 - 192.0.2.5
If you are adding multiple items, press `Enter` after each entry.
- Specifying individual, subnet, or range of IPv6 addresses is not currently supported.
- Forwarding rules based on Wildcard FQDNs require DNS requests from clients to be forwarded to the Zscaler service to evaluate criteria match. To learn how DNS resolution is handled by the Zscaler service, see [Handling DNS Resolution for Various Traffic Forwarding Methods](/zia/handling-dns-resolution-various-traffic-forwarding-methods).
- **Destination IPv4 Groups**: Select the [destination IPv4 groups](/zia/how-do-i-configure-destination-ip-groups) that you want to control with this rule. You can also add a new Destination IPv4 Group by clicking the **Add **icon.
-
**Destination IPv6 Groups**: To control destination IPv6 addresses with this rule, select the **All IPv6** Group, which is the default destination IPv6 group for all IPv6 addresses.
Custom destination IPv6 groups are not currently supported. To learn more, see [About Destination IP Groups](/zia/about-destination-ip-groups).
- **Destination Country**: To identify destinations based on the location of a server, select **Any** to apply the rule to all countries or select the countries to which you want to control traffic.