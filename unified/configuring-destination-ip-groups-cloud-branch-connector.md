# Configuring Destination IP Groups for Cloud & Branch Connector
Source: https://help.zscaler.com/unified/configuring-destination-ip-groups-cloud-branch-connector
PDF: https://help.zscaler.com/pdf/com/en/1520461.pdf

You can group destinations by specifying IP addresses and countries where servers are located.
To create a destination IP group:
- Go to **Policies **>** Access Control** > **Firewall** > **IP & FQDN Groups**.
-
On the **Destination IP Groups** tab, click **Add Destination IPv4 Group.**
The **Add Destination IP Group** window appears.
- In the **Add Destination IP Group **window:
- **Name**:** **Enter a name for the destination IP address group. You can only use alphanumeric characters, underscores, hyphens, and periods.
- **Type**:** **Select **IP Address**, **FQDN**, **Wildcard Domain**, or **Other**. To enter multiple items, press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page, filter the list by searching for a word, phrase, or number contained in an item, and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **IP Addresses**: You can add IP addresses in any of the following formats:
- An individual IP address (for example, `192.0.2.1`)
- A subnet (for example, `192.0.2.0/24`)
- An IP address range (for example, `192.0.2.1 - 192.0.2.5`)
- **FQDN**: For applications with multiple IP addresses or with IP addresses that frequently change, you can add fully qualified domain names (FQDNs). FQDNs are the full name of a system. The hostname is a shortened version of the full name of the system. For example, venera.isi.edu is an FQDN, and venera is a hostname.
- **Wildcard FQDN**: You can enter specific wildcard domains or enter * to denote all domains. A wildcard domain is a record, specified by an asterisk, within DNS that matches requests for nonexistent domain names. An example is `*.example.com`. Examples of invalid wildcard domains are `*abc.example.com` and `abs.*.example.com`. Zscaler cannot match invalid items.
- **Other**: Countries and Categories are the only options on this tab.
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
To use wildcard FQDN destination IP groups, design your network so that workloads, servers, and endpoints are deployed to route DNS queries through the Cloud Connector or Branch Connector.