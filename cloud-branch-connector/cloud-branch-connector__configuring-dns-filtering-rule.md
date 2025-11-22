# Configuring the DNS Filtering Rule
Source: https://help.zscaler.com/cloud-branch-connector/configuring-dns-filtering-rule
PDF: https://help.zscaler.com/pdf/com/en/1420516.pdf

Configuring a DNS Filtering rule provides you with greater control over your DNS traffic.
To configure a DNS Filtering forwarding rule:
- Go to **Forwarding **>** DNS Policies**.
-
Click **Add DNS Filtering Rule**.
The **Add DNS Filtering Rule** window appears.
[See image.](#ADDDNS)
- In the **Add DNS Filtering Rule** window:
- In the **DNS Filtering Rule** section, enter the rule attributes:
- **Rule Order**: Enter the order of the rule. Zscaler evaluates forwarding rules in ascending numerical order (Rule 1 before Rule 2, and so on). The rule order setting reflects this rule's place in the order. You can change the value based on your requirement.
- **Rule Name**: Enter a user-friendly name for the rule. The maximum length is 31 characters. (Avoid using the names of rules that were previously deleted. If you reuse an old name, the service displays the logs for both the deleted rule and the new rule when you view the logs.)
- **Rule Status**: Enable this option to actively enforce the rule. Disabling this option does not actively enforce the rule, and the service skips it and moves to the next rule. However, the rule does not lose its place in the rule order.
- In the **Criteria **section, configure the following:
- On the **General** tab, define the following criteria to which this rule applies:
- **Location/Sublocation**: Select **Any** to apply the rule to all locations, or select up to 8 locations or sublocations. You can also search for and select a location.
-
**Cloud & Branch Connector Groups**: Select **Any** to apply the rule to all groups, or select specific groups to apply the rule to. You can also search for groups and select them.
In the **Destination** field, the application segment field is automatically set to **Any**.
- On the **Source** tab, define the following criteria to which this rule applies:
- **Source IP Groups**: Select any number of source IP address groups. If you do not select a source IP address group, the rule applies to all source IP address groups.
-
**Source IP Addresses**: Enter the source IP address in any of the following formats:
- An individual IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP address range (e.g., `192.0.2.1-192.0.2.5`)
To prevent App Connector looping, either exclude IP addresses that your App Connector device uses to open connections or include IP addresses of all non-App Connector devices.
- On the **DNS Application** tab, define the following criteria to which this rule applies:
- **Destination IPv4 Groups**: Although you can configure this field, Zscaler does not support destination IPv4 groups for DNS filtering rules.
- **FQDN / Domains**: Enter one or more FQDN/domains.
- In the **Action** section, choose the **Network Traffic** action that the Zscaler service takes when a session matches the criteria:
- **Allow**: Allows DNS requests and responses that match the rule.
- **Block**: Silently blocks all DNS requests and responses that match the rule.
- **Resolved by ZPA**: Requests the Cloud or Branch Connector to resolve DNS requests using the IP pool.
- In the **IP Pool **field, you can select the default ZPA IP pool or any other IP pool from the drop-down menu based on your requirement.
- **Redirect Request**: Redirect all DNS requests and responses to a DNS gateway.
- **DNS Gateway**: Select a DNS gateway where requests are redirected.
-
In the **Description** field, enter additional notes or information. The description cannot exceed 10,240 characters.
[See image.](#AddDNSFilteringRule)
- Click **Save** and [activate the change](/cloud-branch-connector/brnch/saving-and-activating-changes).
![Add the DNS Filtering Rule window in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/configuring-dns-filtering-rule-draft-doc-49777/Add%20DNS%20Filtering%20Rule%20update.png)
[]
![Add DNS Filtering Rule](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/configuring-dns-filtering-rule-draft-doc-54300/AddDNSFilteringRule.png)
[]