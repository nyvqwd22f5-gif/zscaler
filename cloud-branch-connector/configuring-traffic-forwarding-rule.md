# Configuring Traffic Forwarding Rules
Source: https://help.zscaler.com/cloud-branch-connector/configuring-traffic-forwarding-rule
PDF: https://help.zscaler.com/pdf/com/en/1420496.pdf

[Watch a video on Traffic Forwarding.](https://fast.wistia.net/embed/iframe/90oj4vknhx)
You can configure a traffic forwarding rule to forward select traffic to specific endpoints by different forwarding methods based on your requirements. You can forward specific traffic through Zscaler Internet Access (ZIA) or application traffic through Zscaler Private Access (ZPA). You can also use the direct, drop, or local forwarding methods to forward your traffic. The local forwarding method is only available for Cloud Connector and Zscaler Zero Trust Gateways.
To use traffic forwarding rules that use wildcard domains and/or FQDNs, design your network where workloads, servers, and endpoints are deployed to route DNS queries through the Cloud Connector or Branch Connector. If you are forwarding HTTP/HTTPS traffic, DNS is not required for wildcard domain and FQDN traffic. However, UDP and non-web traffic requires DNS to function.
- [Configuring Forwarding Rules Using ZIA](#zia)
- [Configuring Forwarding Rules Using ZPA](#zpa)
- [Configuring Forwarding Rules Using Direct](#direct)
- [Configuring Forwarding Rules Using Drop](#drop)
- [Configuring Forwarding Rules Using Local](#local)
[]A default forwarding rule with a default gateway is predefined for ZIA. To configure rules to forward specific traffic through the ZIA gateway:
- Go to **Forwarding **> **Traffic** **Forwarding**.
-
Click **Add Traffic Forwarding Rule**.
The** Add Traffic Forwarding Rules** window appears.
- In the **Add Traffic Forwarding Rules** window:
- In the **Forwarding Rule** section, configure the following:
- **Rule Order**: Enter the order of the rule. Zscaler evaluates forwarding rules in ascending numerical order (Rule 1 before Rule 2, and so on). The rule order setting reflects this rule's place in the order. You can change the value based on your requirement.
- **Rule Name**: Enter a user-friendly name for the rule. The forwarding control feature automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**: Enable this option to actively enforce the rule. If you disable this option, the service skips the rule and moves to the next one. However, the rule does not lose its place in the rule order.
-
**Forwarding Method**: From the drop-down menu, select the forwarding method to be used for this rule. Select **ZIA**. This method forwards internet-bound traffic that matches a ZIA rule to ZIA gateways over a configurable encrypted or unencrypted tunnel.
[See image.](#ZIAForwardingRule)
- In the **Criteria** section, configure the following:
- [General](#ZIAGeneral)
- [Services](#ZIAServices)
- [Applications](#ZIAApplications)
- [Source](#ZIASource)
- [Destination](#ZIADestination)
-
In the **Action** section, configure the following:
- **Forward to Proxy Gateway**: (Optional) From the drop-down menu, select a proxy gateway​​​.
-
**WAN Selection**: This field is set to **None** by default. If **None** is selected, the wide-area network (WAN) is set to the configuration selected in the Traffic Distribution section of [Configuring a Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template#GatewayWAN). To distribute traffic evenly, select **Balanced**. To always forward the traffic via the best-performing WAN link, select **Best Link**.
WAN selection is only applicable when configuring a hardware device deployed in gateway mode. In the Cloud & Branch Connector group column, ensure that the Branch Connector group or location is only for devices deployed in gateway mode.
[See image.](#ZIAForwardtoProxyGateway)
- (Optional) In the **Description** field, enter a description for the rule.
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
- []**Location/Sublocation**: Select up to 8 locations or sublocations. If you do not select a location, the rule applies to all locations.
-
**Cloud & Branch Connector Groups**: Select up to 32 Cloud Connector or Branch Connector groups to apply this rule to. If you do not select a group, the rule applies to all Cloud Connector or Branch Connector groups.
[See image.](#ZIAGeneraldetails)
- []**Network Services**: Select any number of network services. If you do not select a network service, the rule applies to all network services.
-
**Network Services Group**: Select any number of predefined or custom network services groups. If you do not select a network services group, the rule applies to all network service groups.
[See image.](#ZIAServicesdetails)
[]
**Application Service Groups**: Application service groups allow you to configure traffic forwarding rules based on the predefined application service groups that Zscaler provides. They also allow you to enforce condition-based actions on your network traffic, such as allowing or blocking traffic and forwarding traffic to specific destinations. Select items from the drop-down menu to use as criteria when configuring traffic forwarding rules:
- **OFFICE365**
- **ZOOM**
- **WEBEX**
- **RINGCENTRAL**
- **LOGMEIN**
- **Zscaler Cloud Endpoints**
[See image.](#ZIAApplicationServiceGroups)
[]
- **Source IP Groups**: Select any number of source IP address groups or App Connector source IP addresses. If a source IP address group is not selected, the rule applies to all source IP address groups.
- **Source IP Addresses**: Enter source IP addresses in any of the following formats:
- An individual IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP address range (e.g., `192.0.2.1-192.0.2.5`)
-
**Source Workload Groups**: Select any number of source workload groups, which are applied to security policies for your cloud workloads deployed on the public cloud service provider. They can be referenced as a source object for the Local, Direct, ZIA, and ZPA criteria. Firewall rules that forward traffic to the internet can include and extend to the forwarding policy. Source workload groups are only applicable to Cloud Connector traffic forwarding policies. To learn more about workload groups, see [Understanding Workload Groups](/zia/understanding-workload-groups).
[See image.](#ZIASourcedetails)
- []**Destination IPv4 Groups**: Select any number of destination IPv4 groups. If you do not select a destination IPv4 group, the rule applies to all destination IP address groups.
-
**IP Address Or WildCard FQDN**: If the domain has multiple destination IP addresses or if its IP addresses may change, enter IP addresses, wildcard domains, and/or fully qualified domain names (FQDNs). For IP addresses, you can enter individual IP addresses, subnets, or address ranges. If adding multiple items, press `Enter` after each entry. Your Cloud or Branch Connector does not allow you to distinguish between multi-home servers, which are the same destination IP hosts with more than one FQDN.
A wildcard domain is a record, specified by an asterisk, within DNS that matches requests for nonexistent domain names. An example is `*.example.com`. Examples of invalid wildcard domains are `*abc.example.com` and `abs.*.example.com`. Zscaler cannot match invalid items. FQDNs are the full name of a system. The hostname is a shortened version of the full name of the system. For example, `venera.isi.edu` is an FQDN and `venera` is a hostname. Wildcard domains and FQDNs are limited to 16K per organization and 8,000 per rule.
For wildcard domain or FQDN support, forward workload DNS traffic through the Cloud or Branch Connector.
[See image.](#ZIADestinationdetails)
[]The following default forwarding rules are predefined for ZPA:
- **ZPA Forwarding Rule** with a default gateway is created when you are subscribed to the ZPA license.
- **ZPA Pool For Stray Traffic** with the forwarding method set to **Drop** is automatically created with view-only access when you enable a ZPA server's SKU on your Cloud or Branch Connector.
To configure rules to forward application traffic through ZPA:
- Go to **Forwarding **> **Traffic** **Forwarding**.
-
Click **Add Traffic Forwarding Rule**.
The** Add Traffic Forwarding Rules** window appears.
- In the **Add Traffic Forwarding Rules** window:
- In the **Forwarding Rule** section, configure the following:
- **Rule Order**: Enter the order of the rule. Zscaler evaluates forwarding rules in ascending numerical order (Rule 1 before Rule 2, and so on). The rule order setting reflects this rule's place in the order. You can change the value based on your requirement.
- **Rule Name**: Enter a user-friendly name for the rule. The forwarding control feature automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**: Enable this option to actively enforce the rule. If you disable this option, the service skips the rule and moves to the next one. However, the rule does not lose its place in the rule order.
-
**Forwarding Method**: Select the forwarding method to be used for this rule. Select **ZPA**. This method forwards the private application traffic that matches a ZPA rule to ZPA over an encrypted tunnel.
You cannot configure a forwarding gateway for ZPA. You can only use the default gateway as the forwarding gateway for ZPA.
[See image.](#ZPAForwardingRule)
- In the **Criteria** section, configure the following:
- [General](#ZPAGeneral)
- [Source](#ZPASource)
- [Destination](#ZPADestination)
- In the **Action** section, configure the following:
- **Forward to ZPA Gateway**: This field is set to **Default Gateway** and cannot be configured.
-
**WAN Selection**: This field is set to **None** by default. If **None** is selected, the wide-area network (WAN) is set to the configuration selected in the Traffic Distribution section of [Configuring a Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template#GatewayWAN). To distribute traffic evenly, select **Balanced**. To always forward the traffic via the best-performing WAN link, select **Best Link**.
WAN selection is only applicable when configuring a hardware device deployed in gateway mode. In the Cloud & Branch Connector group column, ensure that the Branch Connector group or location is only for devices deployed in gateway mode.
[See image.](#ZPAAction)
- (Optional) In the **Description** field, enter a description for the rule.
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
- []**Location/Sublocation**: Select up to 8 locations or sublocations. If you do not select a location, the rule applies to all locations.
-
**Cloud & Branch Connector Groups**: Select up to 32 Cloud Connector or Branch Connector groups to apply this rule to. If you do not select a group, the rule applies to all Cloud Connector or Branch Connector groups.
[See image.](#ZPAGeneraldetails)
[]
- **Source IP Groups**: Select any number of source IP address groups or App Connector source IP addresses. If you do not select a source IP address group, the rule applies to all source IP address groups.
- **Source IP Addresses**: Enter source IP addresses in any of the following formats:
- An individual IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP address range (e.g., `192.0.2.1-192.0.2.5`)
-
**Source Workload Groups**: Select any number of source workload groups, which are applied to security policies for your cloud workloads deployed on the public cloud service provider. They can be referenced as a source object for the Local, Direct, ZIA, and ZPA criteria. Firewall rules that forward traffic to the internet can include and extend to the forwarding policy. Source workload groups are only applicable to Cloud Connector traffic forwarding policies. To learn more about workload groups, see [Understanding Workload Groups](/zia/understanding-workload-groups).
To prevent App Connector looping, exclude IP addresses that your App Connector device uses to open connections or include IP addresses of all non-App Connector devices.
[See image.](#ZPASourcedetails)
[]
**Apply to All App Segments**: Enable this setting to apply the traffic forwarding rule to all existing and future App Segments that are created. Disable this setting to configure the following settings:
- **Application Segments**: Select the application segments to which to apply the traffic forwarding rule. There is no limit to how many you can select. If you do not select any segments, the rule is not applied to any segments.
- **Segment Groups**: Select the segment groups to which to apply the traffic forwarding rule. There is no limit to how many you can select. If you do not select any groups, the rule is not applied to any groups.
[See image.](#ZPADestinationdetails)
[]To configure the forwarding rules to forward traffic directly to the destination server:
- Go to **Forwarding **> **Traffic** **Forwarding**.
-
Click **Add Traffic Forwarding Rule**.
The** Add Traffic Forwarding Rules** window appears.
- In the **Add Traffic Forwarding Rules** window:
- In the **Forwarding Rule** section, configure the following:
- **Rule Order**: Enter the order of the rule. Zscaler evaluates forwarding rules in ascending numerical order (Rule 1 before Rule 2, and so on). The rule order reflects this rule's place in the order. You can change the value based on your requirement.
- **Rule Name**: Enter a user-friendly name for the rule. The forwarding control feature automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**: Enable this option to actively enforce the rule. If you disable this option, the service skips the rule and moves to the next one. However, the rule does not lose its place in the rule order.
-
**Forwarding Method**: Select the forwarding method to be used for this rule. Select **Direct**. This method bypasses ZIA/ZPA and forwards traffic directly to the destination server using the Zscaler service IP address.
[See image.](#DirectForwardingRule)
- In the **Criteria** section, configure the following:
- [General](#DirectGeneral)
- [Services](#DirectServices)
- [Application](#DirectApplications)
- [Source](#DirectSource)
- [Destination](#DirectDestination)
-
In the **Action** section, from the **WAN Selection** drop-down menu, **None** is set by default. If **None** is selected, the WAN is set to the configuration selected in the Traffic Distribution section of [Configuring a Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template#GatewayWAN). Select **Balanced** for the traffic to be evenly distributed or select **Best Link** for the traffic to always be forwarded via the best-performing WAN link.
[See image.](#DirectAction)
WAN selection is only applicable when configuring a hardware device deployed in gateway mode. In the Cloud & Branch Connector group column, ensure that the Branch Connector group or location is only for devices deployed in gateway mode.
- (Optional) In the **Description** field, enter a description for the rule.
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
- []**Location/Sublocation**: Select up to 8 locations or sublocations. If you do not select a location, the rule applies to all locations.
-
**Cloud & Branch Connector Groups**: Select up to 32 Cloud Connector or Branch Connector groups to apply this rule to. If you do not select a group, the rule applies to all Cloud Connector or Branch Connector groups.
[See image.](#DirectGeneraldetails)
- []**Network Services**: Select any number of network services. If you do not select a network service, the rule applies to all network services.
-
**Network Services Group**: Select any number of predefined or custom network services groups. If you do not select a network services group, the rule applies to all network service groups.
[See image.](#DirectServicesdetails)
[]
**Application Service Groups**: Application service groups allow you to configure traffic forwarding rules based on the predefined application service groups that Zscaler provides. They also allow you to enforce condition-based actions on your network traffic, such as allowing or blocking traffic and forwarding traffic to specific destinations. Select items from the drop-down menu to use as criteria when configuring traffic forwarding rules:
- **OFFICE365**
- **ZOOM**
- **WEBEX**
- **RINGCENTRAL**
- **LOGMEIN**
- **Zscaler Cloud Endpoints**
[See image.](#DirectApplicationServiceGroups)
[]
- **Source IP Groups**: Select any number of source IP address groups or App Connector source IP addresses. If you do not select a source IP address group, the rule applies to all source IP address groups.
- **Source IP Addresses**: Enter source IP addresses in any of the following formats:
- An individual IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP address range (e.g., `192.0.2.1-192.0.2.5`)
-
**Source Workload Groups**: Select any number of source workload groups, which are applied to security policies for your cloud workloads deployed on the public cloud service provider. They can be referenced as a source object for the Local, Direct, ZIA, and ZPA criteria. Firewall rules that forward traffic to the internet can include and extend to the forwarding policy. Source workload groups are only applicable to Cloud Connector traffic forwarding policies. To learn more about workload groups, see [Understanding Workload Groups](/zia/understanding-workload-groups).
To prevent App Connector looping, exclude IP addresses that your App Connector device uses to open connections or include IP addresses of all non-App Connector devices.
[See image.](#DirectSourcedetails)
- []**Destination IPv4 Groups**: Select any number of destination IPv4 groups. If you do not select a destination IPv4 group, the rule applies to all destination IP address groups.
-
**IP Address Or WildCard FQDN**: If the domain has multiple destination IP addresses or if its IP addresses may change, enter IP addresses, wildcard domains, and/or fully qualified domain names (FQDNs). For IP addresses, you can enter individual IP addresses, subnets, or address ranges. If adding multiple items, press `Enter` after each entry. Your Cloud or Branch Connector does not allow you to distinguish between multi-home servers, which are the same destination IP hosts with more than one FQDN.
A wildcard domain is a record, specified by an asterisk, within DNS that matches requests for nonexistent domain names. An example is `*.example.com`. Examples of invalid wildcard domains are `*abc.example.com` and `abs.*.example.com`. Zscaler cannot match invalid items. FQDNs are the full name of a system. The hostname is a shortened version of the full name of the system. For example, `venera.isi.edu` is an FQDN and `venera` is a hostname. Wildcard domains and FQDNs are limited to 16K per organization and 8,000 per rule.
For wildcard domain or FQDN support, forward workload DNS traffic through the Cloud or Branch Connector.
[See image.](#DirectDestinationdetails)
[]To configure the forwarding rules to drop traffic:
- Go to **Forwarding **> **Traffic** **Forwarding**.
-
Click **Add Traffic Forwarding Rule**.
The** Add Traffic Forwarding Rules** window appears.
- In the **Add Traffic Forwarding Rules** window:
- In the **Forwarding Rule** section, configure the following:
- **Rule Order**: Enter the order of the rule. Zscaler evaluates forwarding rules in ascending numerical order (Rule 1 before Rule 2, and so on). The rule order reflects this rule's place in the order. You can change the value based on your requirement.
- **Rule Name**: Enter a user-friendly name for the rule. The forwarding control feature automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**: Enable this option to actively enforce the rule. If you disable this option, the service skips the rule and moves to the next one. However, the rule does not lose its place in the rule order.
-
**Forwarding Method**: Select the forwarding method to be used for this rule. Select **Drop**. This method drops all traffic matching the configured forwarding rule. The Cloud or Branch Connector appliance discards packets matching the Drop rule. The discarded packets appear in the [Sessions Logs](/cloud-branch-connector/brnch/about-insights-logs) of the Zscaler Cloud & Branch Connector Admin Portal.
[See image.](#DropForwardingRule)
- In the **Criteria** section, configure the following:
- [General](#DropGeneral)
- [Services](#DropServices)
- [Applications](#DropApplications)
- [Source](#DropSource)
- [Destination](#DropDestination)
- (Optional) In the **Description** field, enter a description for the rule.
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
- []**Location**: Select up to 8 locations. If you do not select a location, the rule applies to all locations.
-
**Cloud & Branch Connector Groups**: Select up to 32 Cloud Connector groups to apply this rule to. If you do not select a group, the rule applies to all Cloud Connector groups.
[See image.](#DropGeneraldetails)
- []**Network Services**: Select any number of network services. If you do not select a network service, the rule applies to all network services.
-
**Network Services Group**: Select any number of predefined or custom network services groups. If you do not select a network services group, the rule applies to all network service groups.
[See image.](#DropServicesdetails)
[]
**Application Service Groups**: Application service groups allow you to configure traffic forwarding rules based on the predefined application service groups that Zscaler provides. They also allow you to enforce condition-based actions on your network traffic, such as allowing or blocking traffic and forwarding traffic to specific destinations. Select items from the drop-down menu to use as criteria when configuring traffic forwarding rules:
- **OFFICE365**
- **ZOOM**
- **WEBEX**
- **RINGCENTRAL**
- **LOGMEIN**
- **Zscaler Cloud Endpoints**
[See image.](#DropApplicationServiceGroups)
[]
- **Source IP Groups**: Select any number of source IP address groups or App Connector source IP addresses. If you do not select a source IP address group, the rule applies to all source IP address groups.
- **Source IP Addresses**: Enter source IP addresses in any of the following formats:
- An individual IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP address range (e.g., `192.0.2.1-192.0.2.5`)
-
**Source Workload Groups**: Select any number of source workload groups, which are applied to security policies for your cloud workloads deployed on the public cloud service provider. They can be referenced as a source object for the Local, Direct, ZIA, and ZPA criteria. Firewall rules that forward traffic to the internet can include and extend to the forwarding policy. Source workload groups are only applicable to Cloud Connector traffic forwarding policies. To learn more about workload groups, see [Understanding Workload Groups](/zia/understanding-workload-groups).
To prevent App Connector looping, exclude IP addresses that your App Connector device uses to open connections or include IP addresses of all non-App Connector devices.
[See image.](#DropSourcedetails)
- []**Apply to All App Segments**: Enable this setting to apply the traffic forwarding rule to all existing and future App Segments that are created. Disable this setting to configure the following settings:
- **Application Segments**: Select the application segments to which to apply the traffic forwarding rule. There is no limit to how many you can select. If you do not select any segments, the rule is not applied to any segments.
- **Segment Groups**: Select the segment groups to which to apply the traffic forwarding rule. There is no limit to how many you can select. If you do not select any groups, the rule is not applied to any groups.
- **Destination IPv4 Groups**: Select any number of destination IPv4 groups. If you do not select a destination IPv4 group, the rule applies to all destination IP address groups.
-
**IP Address Or WildCard FQDN**: If the domain has multiple destination IP addresses or if its IP addresses may change, enter IP addresses, wildcard domains, and/or fully qualified domain names (FQDNs). For IP addresses, you can enter individual IP addresses, subnets, or address ranges. If adding multiple items, press `Enter` after each entry. Your Cloud or Branch Connector does not allow you to distinguish between multi-home servers, which are the same destination IP hosts with more than one FQDN.
A wildcard domain is a record, specified by an asterisk, within DNS that matches requests for nonexistent domain names. An example is `*.example.com`. Examples of invalid wildcard domains are `*abc.example.com` and `abs.*.example.com`. Zscaler cannot match invalid items. FQDNs are the full name of a system. The hostname is a shortened version of the full name of the system. For example, `venera.isi.edu` is an FQDN and `venera` is a hostname. Wildcard domains and FQDNs are limited to 16K per organization and 8,000 per rule.
For wildcard domain or FQDN support, forward workload DNS traffic through the Cloud or Branch Connector.
[See image.](#DropDestinationdetails)
[]
The local forwarding method facilitates subnet-to-subnet or virtual private cloud (VPC)-to-VPC communication across Amazon Web Services (AWS), Microsoft Azure, and Google Cloud Platform (GCP), allowing you to permit ingress traffic to publicly hosted applications in AWS. To configure the rules to forward traffic back to its origin or control traffic for east-west segmentation and macrosegmentation using 5-tuples:
- Go to **Forwarding **> **Traffic** **Forwarding**.
-
Click **Add Traffic Forwarding Rule**.
The** Add Traffic Forwarding Rules** window appears.
- In the **Add Traffic Forwarding Rules** window:
- In the **Forwarding Rule** section, configure the following:
- **Rule Order**: Enter the order of the rule. Zscaler evaluates forwarding rules in ascending numerical order (Rule 1 before Rule 2, and so on). The rule order setting reflects this rule's place in the order. You can change the value based on your requirement.
- **Rule Name**: Enter a user-friendly name for the rule. The forwarding control feature automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**: Enable this option to actively enforce the rule. If you disable this option, the service skips the rule and moves to the next one. However, the rule does not lose its place in the rule order.
-
**Forwarding Method**: From the drop-down menu, select the forwarding method to be used for this rule. Select **Local**. This method forwards traffic locally in the public cloud to the intended destination, such as an IP address or tag. Traffic does not egress out of the public cloud and can be forwarded from any IP address or tag in a VPC to another IP address or tag in the same or a different VPC. The local forwarding method is only available for Cloud Connector and Zero Trust Gatways.
[See image.](#LocalForwardingRule)
- In the **Criteria** section, configure the following:
- [General](#LocalGeneral)
- [Services](#LocalServices)
- [Applications](#LocalApplications)
- [Source](#LocalSource)
- [Destination](#LocalDestination)
- (Optional) In the **Description** field, enter a description for the rule.
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]
- **Location/Sublocation**: Select up to 8 locations or sublocations. If you do not select a location, the rule applies to all locations.
-
**Cloud & Branch Connector Groups**: Select up to 32 Cloud Connector groups to apply this rule to. If you do not select a group, the rule applies to all Cloud Connector groups.
[See image.](#LocalGeneraldetails)
[]
- **Network Services**: Select any number of network services. If you do not select a network service, the rule applies to all network services.
-
**Network Services Group**: Select any number of predefined or custom network services groups. If you do not select a network services group, the rule applies to all network service groups.
[See image.](#LocalServicesdetails)
[]
**Application Service Groups**: Application service groups allow you to configure traffic forwarding rules based on the predefined application service groups that Zscaler provides. They also allow you to enforce condition-based actions on your network traffic, such as allowing or blocking traffic and forwarding traffic to specific destinations. Select items from the drop-down menu to use as criteria when configuring traffic forwarding rules:
- **OFFICE365**
- **ZOOM**
- **WEBEX**
- **RINGCENTRAL**
- **LOGMEIN**
- **BlueJeans**
- **Amazon Web Services**
- **Azure**
- **GCP**
- **Zscaler Cloud Endpoints**
-
**TALK_DESK**
[See image.](#LocalApplicationsdetails)
[]
- **Source IP Groups**: Select any number of source IP address groups or App Connector source IP addresses. If you do not select a source IP address group, the rule applies to all source IP address groups.
- **Source IP Addresses**: Enter source IP addresses in any of the following formats:
- An individual IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP address range (e.g., `192.0.2.1-192.0.2.5`)
-
**Source Workload Groups**: Select any number of source workload groups, which are applied to security policies for your cloud workloads deployed on the public cloud service provider. They can be referenced as a source object for the Local, Direct, ZIA, and ZPA criteria. Firewall rules that forward traffic to the internet can include and extend to the forwarding policy. Source workload groups are only applicable to Cloud Connector traffic forwarding policies. To learn more about workload groups, see [Understanding Workload Groups](/zia/understanding-workload-groups).
To prevent App Connector looping, exclude IP addresses that your App Connector device uses to open connections or include IP addresses of all non-App Connector devices.
[See image.](#LocalSourcedetails)
[]
- **Destination IPv4 Groups**: Select any number of destination IPv4 groups. If you do not select a destination IPv4 group, the rule applies to all destination IP address groups.
-
**IP Address Or WildCard FQDN**: If the domain has multiple destination IP addresses or if its IP addresses may change, enter IP addresses, wildcard domains, and/or fully qualified domain names (FQDNs). For IP addresses, you can enter individual IP addresses, subnets, or address ranges. If adding multiple items, press `Enter` after each entry. Your Cloud Connector does not allow you to distinguish between multi-home servers, which are the same destination IP hosts with more than one FQDN.
A wildcard domain is a record, specified by an asterisk, within DNS that matches requests for nonexistent domain names. An example is `*.example.com`. Examples of invalid wildcard domains are `*abc.example.com` and `abs.*.example.com`. Zscaler cannot match invalid items. FQDNs are the full name of a system. The hostname is a shortened version of the full name of the system. For example, `venera.isi.edu` is an FQDN and `venera` is a hostname. Wildcard domains and FQDNs are limited to 16K per organization and 8,000 per rule.
For wildcard domain or FQDN support, forward workload DNS traffic through the Cloud Connector.
-
**Destination Workload Groups**: Select any number of destination workload groups, which create tags to define the criteria for a VPC and traffic within your AWS network. Destination workload groups can only be applied to Cloud Connector traffic forwarding policies and are only applicable to the Local traffic forwarding method.
[See image.](#LocalDestinationdetails)
[]![The ZIA Forwarding Rule section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-zia.png)
[]![The ZPA Forwarding Rule section of the Add Traffic Forwarding Rule window in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-zpa.png)
[]![The Direct Forwarding Rule section of the Add Traffic Forwarding Rule window in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-direct.png)
[]![The Drop Forwarding Rule section of the Add Traffic Forwarding Rule window in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-drop.png)
[]
![The Forwarding Rule details in the Edit Traffic Forwarding Rules window of the Traffic Forwarding page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/LocalForwardingRule.png)
[]![The ZIA General tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-zia-general.png)
[]![The ZIA Services tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-service-zia.png)
[]![The Application Service Groups option on the Applications tab of the Add Traffic Forwarding Rules tab in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-applications-zia.png)
[]![The ZIA Source tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-source-zia.png)
[]![The ZIA Destination tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-destination-zia.png)
[]![The Forward to Proxy Gateway of the Action section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-action-zia.png)
[]![The ZPA General tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-zpa-general.png)
[]![The ZPA Source tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-source-zpa.png)
[]![The ZPA Destination tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-destination-zpa.png)
[]![The Forward to ZPA Gateway and WAN Selection fields in the Action section of the Add Traffic Forwarding Rules window in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-action-zpa.png)
[]![The Direct General tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-direct-general.png)
[]![The Direct Services tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-service-direct.png)
[]![The Application Service Groups option on the Applications tab of the Add Traffic Forwarding Rules tab in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-applications-direct.png)
[]![The Direct Source tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-source-direct.png)
[]![The Direct Destination tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-destination-direct.png)
[]![The WAN Selection field in the Action section of the Add Traffic Forwarding Rules window in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-action-direct.png)
[]![The Drop General tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-drop-general.png)
[]![The Drop Services tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-service-drop.png)
[]![The Application Service Groups option on the Applications tab of the Add Traffic Forwarding Rules tab in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-applications-drop.png)
[]![The Drop Source tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-source-drop.png)
[]![The Drop Destination tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-destination-drop.png)
[]
![The Local General tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/LocalGeneraldetails.png)
[]
![The Local Services tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/LocalServicesdetails.png)
[]
![The Local Applications tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/LocalApplicationsdetails.png)
[]
![The Local Source tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/configuring-traffic-forwarding-rules-source-local.png)
[]
![The Local Destination tab of the Criteria section in the Add Traffic Forwarding Rule window of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/forwarding/traffic-forwarding/configuring-traffic-forwarding-rule/LocalDestinationdetails.png)