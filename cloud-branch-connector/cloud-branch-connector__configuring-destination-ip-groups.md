# Configuring Destination IP Groups
Source: https://help.zscaler.com/cloud-branch-connector/configuring-destination-ip-groups
PDF: https://help.zscaler.com/pdf/com/en/1420461.pdf

You can group destinations by specifying IP addresses and countries where servers are located.
To create a destination IP group:
- Go to **Administration** >** IP & FQDN Groups**.
-
On the **Destination IP Groups** tab, click **Add Destination IP Group.**
The **Add Destination IP Group** window appears.
[See image.](#DestinationIPButton)
- In the **Add Destination IP Group **window:
- **Name**:** **Enter a name for the destination IP address group. You can only use alphanumeric characters, underscores, hyphens, and periods.
- **Type**:** **Select **IP Address**, **FQDN**, **Wildcard Domain**, or **Other**. To enter multiple items, press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page, filter the list by searching for a word, phrase, or number contained in an item, and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **IP Address**: You can add IP addresses in any of the following formats:
- An individual IP address (for example, `192.0.2.1`)
- A subnet (for example, `192.0.2.0/24`)
- An IP address range (for example, `192.0.2.1 - 192.0.2.5`)
- **FQDN**: For applications with multiple IP addresses or with IP addresses that frequently change, you can add fully qualified domain names (FQDNs). FQDNs are the full name of a system. The hostname is a shortened version of the full name of the system. For example, venera.isi.edu is an FQDN, and venera is a hostname.
- **Wildcard Domain**: You can enter specific wildcard domains or enter * to denote all domains. A wildcard domain is a record, specified by an asterisk, within DNS that matches requests for nonexistent domain names. An example is `*.example.com`. Examples of invalid wildcard domains are `*abc.example.com` and `abs.*.example.com`. Zscaler cannot match invalid items.
- **Other**: Countries are the only option on this tab, but you cannot configure countries.
-
**Description**: (Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
[See image.](#AddDestinationIpGroupWindow)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
To use wildcard FQDN destination IP groups, design your network so that workloads, servers, and endpoints are deployed to route DNS queries through the Cloud Connector or Branch Connector. If you are forwarding HTTP/HTTPS traffic, DNS is not required for wildcard domain and FQDN traffic. However, UDP and non-web traffic requires DNS to function.
[![Add Destination IP Group in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/firewall-filtering/configuring-destination-ip-groups/Add%20Destination%20IP%20Group.jpg)
][]
[![Add Destination IP Group configuraton window](/downloads/cloud-connector/administration/firewall-filtering/configuring-destination-groups/Add%20Destination%20IP%20Group.jpg)
][]