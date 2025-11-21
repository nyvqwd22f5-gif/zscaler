# Configuring Traffic Forwarding Rules
Source: https://help.zscaler.com/unified/configuring-traffic-forwarding-rules
PDF: https://help.zscaler.com/pdf/com/en/1516441.pdf

You can configure a traffic forwarding rule to forward select traffic to specific endpoints by different forwarding methods based on your requirements. You can forward specific traffic through Zscaler Internet Access (ZIA) or application traffic through Zscaler Private Access (ZPA). You can also use the direct or drop forwarding methods to forward your traffic.
To use traffic forwarding rules that use wildcard domains and/or fully qualified domain names (FQDNs), design your network where workloads, servers, and endpoints are deployed to route DNS queries through the Cloud Connector or Branch Connector.
- [Configuring Forwarding Rules Using ZIA](#zia)
- [Configuring Forwarding Rules Using ZPA](#zpa)
- [Configuring Forwarding Rules Using Direct](#direct)
- [Configuring Forwarding Rules Using Drop](#drop)
[]A default forwarding rule with a default gateway is predefined for Internet & SaaS. To configure rules to forward specific traffic through the ZIA gateway:
- Go to **Infrastructure **> **Connectors** > **Cloud** > **Forwarding Policy** for Cloud Connector or **Infrastructure **> **Connectors** > **Edge** > **Forwarding Policy** for Branch Connector.
-
Click **Add Traffic Forwarding Rule**.
The** Add Traffic Forwarding Rules** window appears.
- In the **Add Traffic Forwarding Rules** window:
- In the **Forwarding Rule** section, configure the following:
- **Rule Order**: Enter the order of the rule. Zscaler evaluates forwarding rules in ascending numerical order (Rule 1 before Rule 2, and so on). The rule order setting reflects this rule's place in the order. You can change the value based on your requirement.
- **Rule Name**: Enter a user-friendly name for the rule. The forwarding control feature automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**: Enable this option to actively enforce the rule. Disabling this option does not actively enforce the rule, and the service skips it and moves to the next rule. However, the rule does not lose its place in the rule order.
- **Forwarding Method**: From the drop-down menu, select the forwarding method to be used for this rule. Select **ZIA**. This method forwards internet-bound traffic that matches a ZIA rule to ZIA gateways over a configurable encrypted or unencrypted tunnel.
- In the **Criteria** section, configure the following:
- [General](#general)
- [Services](#services)
- [Applications](#ZIAApplications)
- [Source](#source)
- [Destination](#destination)
- In the **Action** section, configure the following:
- **Forward to Proxy Gateway**: (Optional) From the drop-down menu, select a proxy gateway​​​.
- (Optional) In the **Description** field, enter a description for the rule.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
- []**Location/Sublocation**: Select up to 8 locations or sublocations. If you do not select a location, the rule applies to all locations.
- **Cloud & Branch Connector Groups**: Select up to 32 Cloud Connector or Branch Connector groups to apply this rule to. If you do not select a group, the rule applies to all Cloud Connector or Branch Connector groups.
- []**Network Services**: Select any number of network services. If you do not select a network service, the rule applies to all network services.
- **Network Services Group**: Select any number of predefined or custom network services groups. If you do not select a network services group, the rule applies to all network service groups.
[]
**Application Service Groups**: Application service groups allow you to configure traffic forwarding rules based on the predefined application service groups that Zscaler provides. They also allow you to enforce condition-based actions on your network traffic, such as allowing or blocking traffic and forwarding traffic to specific destinations. Select items from the drop-down menu to use as criteria when configuring traffic forwarding rules.
[]
- **Source IP Groups**: Select any number of source IP address groups or App Connector source IP addresses. If a source IP address group is not selected, the rule applies to all source IP address groups.
-
**Source IP Addresses**: Enter source IP addresses in any of the following formats:
- An individual IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP address range (e.g., `192.0.2.1-192.0.2.5`)
To prevent App Connector looping, exclude IP addresses that your App Connector device uses to open connections or include IP addresses of all non-App Connector devices.
- []**Destination IPv4 Groups**: Select any number of destination IPv4 groups. If you do not select a destination IPv4 group, the rule applies to all destination IP address groups.
-
**IP Address Or WildCard FQDN**: If the domain has multiple destination IP addresses or if its IP addresses may change, enter IP addresses, wildcard domains, and/or fully qualified domain names (FQDNs). For IP addresses, you can enter individual IP addresses, subnets, or address ranges. If adding multiple items, press `Enter` after each entry. Your Cloud or Branch Connector does not allow you to distinguish between multi-home servers, which are the same destination IP hosts with more than one FQDN.
A wildcard domain is a record, specified by an asterisk, within DNS that matches requests for nonexistent domain names. An example is `*.example.com`. Examples of invalid wildcard domains are `*abc.example.com` and `abs.*.example.com`. Zscaler cannot match invalid items. FQDNs are the full name of a system. The hostname is a shortened version of the full name of the system. For example, `venera.isi.edu` is an FQDN and `venera` is a hostname. Wildcard domains and FQDNs are limited to 16K per organization and 8,000 per rule.
For wildcard domain or FQDN support, forward workload DNS traffic through the Cloud or Branch Connector.
[]The following default forwarding rules are predefined for Private Applications:
- **ZPA Forwarding Rule** with a default gateway is created when you are subscribed to the ZPA license.
- **ZPA Pool For Stray Traffic** with the forwarding method set to **Drop** is automatically created with view-only access when you enable a ZPA server's SKU on your Cloud or Branch Connector.
To configure rules to forward application traffic through ZPA:
- Go to **Infrastructure **> **Connectors** > **Cloud** > **Forwarding Policy** for Cloud Connector or **Infrastructure **> **Connectors** > **Edge** > **Forwarding Policy** for Branch Connector.
-
Click **Add Traffic Forwarding Rule**.
The** Add Traffic Forwarding Rules** window appears.
- In the **Add Traffic Forwarding Rules** window:
- In the **Forwarding Rule** section, configure the following:
- **Rule Order**: Enter the order of the rule. Zscaler evaluates forwarding rules in ascending numerical order (Rule 1 before Rule 2, and so on). The rule order setting reflects this rule's place in the order. You can change the value based on your requirement.
- **Rule Name**: Enter a user-friendly name for the rule. The forwarding control feature automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**: Enable this option to actively enforce the rule. Disabling this option does not actively enforce the rule, and the service skips it and moves to the next rule. However, the rule does not lose its place in the rule order.
-
**Forwarding Method**: Select the forwarding method to be used for this rule. Select **ZPA**. This method forwards the private application traffic that matches a ZPA rule to ZPA over an encrypted tunnel.
You cannot configure a forwarding gateway for ZPA. You can only use the default gateway as the forwarding gateway for ZPA.
- In the **Criteria** section, configure the following:
- [General](#general2)
- [Source](#source2)
- [Destination](#destination3)
- In the **Action** section, the **Forward to ZPA Gateway** field is set to **Default Gateway** and cannot be configured.
- (Optional) In the **Description** field, enter a description for the rule.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
- []**Location/Sublocation**: Select up to 8 locations or sublocations. If you do not select a location, the rule applies to all locations.
- **Cloud & Branch Connector Groups**: Select up to 32 Cloud Connector or Branch Connector groups to apply this rule to. If you do not select a group, the rule applies to all Cloud Connector or Branch Connector groups.
[]
- **Source IP Groups**: Select any number of source IP address groups or App Connector source IP addresses. If you do not select a source IP address group, the rule applies to all source IP address groups.
-
**Source IP Addresses**: Enter source IP addresses in any of the following formats:
- An individual IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP address range (e.g., `192.0.2.1-192.0.2.5`)
To prevent App Connector looping, exclude IP addresses that your App Connector device uses to open connections or include IP addresses of all non-App Connector devices.
[]
The **Application** **Segment** field is set to **ZPA Edge App Segment**.
[]To configure the forwarding rules to forward traffic directly to the destination server:
- Go to **Infrastructure **> **Connectors** > **Cloud** > **Forwarding Policy** for Cloud Connector or **Infrastructure **> **Connectors** > **Edge** > **Forwarding Policy** for Branch Connector.
-
Click **Add Traffic Forwarding Rule**.
The** Add Traffic Forwarding Rules** window appears.
- In the **Add Traffic Forwarding Rules** window:
- In the **Forwarding Rule** section, configure the following:
- **Rule Order**: Enter the order of the rule. Zscaler evaluates forwarding rules in ascending numerical order (Rule 1 before Rule 2, and so on). The rule order reflects this rule's place in the order. You can change the value based on your requirement.
- **Rule Name**: Enter a user-friendly name for the rule. The forwarding control feature automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**: Enable this option to actively enforce the rule. Disabling this option does not actively enforce the rule, and the service skips it and moves to the next rule. However, the rule does not lose its place in the rule order.
- **Forwarding Method**: Select the forwarding method to be used for this rule. Select **Direct**. This method bypasses ZIA/ZPA and forwards traffic directly to the destination server using the Zscaler service IP address.
- In the **Criteria** section, configure the following:
- [General](#general1)
- [Services](#services5)
- [Application](#DirectApplications)
- [Source](#source1)
- [Destination](#destination2)
- (Optional) In the **Description** field, enter a description for the rule.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
- []**Location/Sublocation**: Select up to 8 locations or sublocations. If you do not select a location, the rule applies to all locations.
- **Cloud & Branch Connector Groups**: Select up to 32 Cloud Connector or Branch Connector groups to apply this rule to. If you do not select a group, the rule applies to all Cloud Connector or Branch Connector groups.
- []**Network Services**: Select any number of network services. If you do not select a network service, the rule applies to all network services.
- **Network Services Group**: Select any number of predefined or custom network services groups. If you do not select a network services group, the rule applies to all network service groups.
[]
**Application Service Groups**: Application service groups allow you to configure traffic forwarding rules based on the predefined application service groups that Zscaler provides. They also allow you to enforce condition-based actions on your network traffic, such as allowing or blocking traffic and forwarding traffic to specific destinations. Select items from the drop-down menu to use as criteria when configuring traffic forwarding rules.
[]
- **Source IP Groups**: Select any number of source IP address groups or App Connector source IP addresses. If you do not select a source IP address group, the rule applies to all source IP address groups.
-
**Source IP Addresses**: Enter source IP addresses in any of the following formats:
- An individual IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP address range (e.g., `192.0.2.1-192.0.2.5`)
To prevent App Connector looping, exclude IP addresses that your App Connector device uses to open connections or include IP addresses of all non-App Connector devices.
- []**Destination IPv4 Groups**: Select any number of destination IPv4 groups. If you do not select a destination IPv4 group, the rule applies to all destination IP address groups.
-
**IP Address Or WildCard FQDN**: If the domain has multiple destination IP addresses or if its IP addresses may change, enter IP addresses, wildcard domains, and/or fully qualified domain names (FQDNs). For IP addresses, you can enter individual IP addresses, subnets, or address ranges. If adding multiple items, press `Enter` after each entry. Your Cloud or Branch Connector does not allow you to distinguish between multi-home servers, which are the same destination IP hosts with more than one FQDN.
A wildcard domain is a record, specified by an asterisk, within DNS that matches requests for nonexistent domain names. An example is `*.example.com`. Examples of invalid wildcard domains are `*abc.example.com` and `abs.*.example.com`. Zscaler cannot match invalid items. FQDNs are the full name of a system. The hostname is a shortened version of the full name of the system. For example, `venera.isi.edu` is an FQDN and `venera` is a hostname. Wildcard domains and FQDNs are limited to 16K per organization and 8,000 per rule.
For wildcard domain or FQDN support, forward workload DNS traffic through the Cloud or Branch Connector.
[]To configure the forwarding rules to drop traffic:
- Go to **Infrastructure **> **Connectors** > **Cloud** > **Forwarding Policy** for Cloud Connector or **Infrastructure **> **Connectors** > **Edge** > **Forwarding Policy** for Branch Connector.
-
Click **Add Traffic Forwarding Rule**.
The** Add Traffic Forwarding Rules** window appears.
- In the **Add Traffic Forwarding Rules** window:
- In the **Forwarding Rule** section, configure the following:
- **Rule Order**: Enter the order of the rule. Zscaler evaluates forwarding rules in ascending numerical order (Rule 1 before Rule 2, and so on). The rule order reflects this rule's place in the order. You can change the value based on your requirement.
- **Rule Name**: Enter a user-friendly name for the rule. The forwarding control feature automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**: Enable this option to actively enforce the rule. Disabling this option does not actively enforce the rule, and the service skips it and moves to the next rule. However, the rule does not lose its place in the rule order.
- **Forwarding Method**: Select the forwarding method to be used for this rule. Select **Drop**. This method drops all traffic matching the configured forwarding rule. The Cloud or Branch Connector appliance discards packets matching the Drop rule. The discarded packets appear in the [Sessions Logs](/cloud-branch-connector/brnch/about-insights-logs) of the Zscaler Cloud & Branch Connector Admin Portal.
- In the **Criteria** section, configure the following:
- [General](#general3)
- [Services](#services4)
- [Applications](#DropApplications)
- [Source](#source3)
- [Destination](#destination4)
- (Optional) In the **Description** field, enter a description for the rule.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
- []**Location/Sublocation**: Select up to 8 locations. If you do not select a location, the rule applies to all locations.
- **Cloud & Branch Connector Groups**: Select up to 32 Cloud Connector groups to apply this rule to. If you do not select a group, the rule applies to all Cloud Connector groups.
- []**Network Services**: Select any number of network services. If you do not select a network service, the rule applies to all network services.
- **Network Services Group**: Select any number of predefined or custom network services groups. If you do not select a network services group, the rule applies to all network service groups.
[]
**Application Service Groups**: Application service groups allow you to configure traffic forwarding rules based on the predefined application service groups that Zscaler provides. They also allow you to enforce condition-based actions on your network traffic, such as allowing or blocking traffic and forwarding traffic to specific destinations. Select items from the drop-down menu to use as criteria when configuring traffic forwarding rules.
[]
- **Source IP Groups**: Select any number of source IP address groups or App Connector source IP addresses. If you do not select a source IP address group, the rule applies to all source IP address groups.
-
**Source IP Addresses**: Enter source IP addresses in any of the following formats:
- An individual IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP address range (e.g., `192.0.2.1-192.0.2.5`)
To prevent App Connector looping, exclude IP addresses that your App Connector device uses to open connections or include IP addresses of all non-App Connector devices.
[]
- **Destination IPv4 Groups**: Select any number of destination IPv4 groups. If you do not select a destination IPv4 group, the rule applies to all destination IP address groups.
-
**IP Address Or WildCard FQDN**: If the domain has multiple destination IP addresses or if its IP addresses may change, enter IP addresses, wildcard domains, and/or fully qualified domain names (FQDNs). For IP addresses, you can enter individual IP addresses, subnets, or address ranges. If adding multiple items, press `Enter` after each entry. Your Cloud or Branch Connector does not allow you to distinguish between multi-home servers, which are the same destination IP hosts with more than one FQDN.
A wildcard domain is a record, specified by an asterisk, within DNS that matches requests for nonexistent domain names. An example is `*.example.com`. Examples of invalid wildcard domains are `*abc.example.com` and `abs.*.example.com`. Zscaler cannot match invalid items. FQDNs are the full name of a system. The hostname is a shortened version of the full name of the system. For example, `venera.isi.edu` is an FQDN and `venera` is a hostname. Wildcard domains and FQDNs are limited to 16K per organization and 8,000 per rule.
For wildcard domain or FQDN support, forward workload DNS traffic through the Cloud or Branch Connector.