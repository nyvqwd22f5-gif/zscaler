# Configuring Source IP Groups for Cloud & Branch Connector
Source: https://help.zscaler.com/unified/configuring-source-ip-groups-cloud-branch-connector
PDF: https://help.zscaler.com/pdf/com/en/1520441.pdf

Grouping source IP addresses together enables easier creation of policies. The source IP groups are used for forwarding policies.
To create a source IP address group:
- Go to **Policies **>** Access Control** > **Firewall** > **IP & FQDN Groups**.
- On the **Source IPv4 Groups** tab, select **Add Source IPv4 Group.**
- In the **Add Source IPv4 Group** window:
- **Name**: Enter a name for the source IP address group. Only alphanumeric characters, underscores, hyphens, and periods are allowed.
- **IP Addresses**: Enter any number of IP addresses in the following formats.
- An IP address (for example, `198.51.100.100`)
- A range of IP addresses (for example, `192.0.2.1-192.0.2.10`)
- An IP address with a netmask (for example, `203.0.113.0/24`)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Description**: (Optional) Enter additional notes or information about the source IP group. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).