# Configuring Source IP Groups for Internet & SaaS
Source: https://help.zscaler.com/unified/configuring-source-ip-groups-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1494186.pdf

You can create custom groups for source IPv4 addresses by specifying individual, subnet, or range of addresses.
Custom groups for IPv6 addresses are not currently supported.
To create a custom group for source IPv4 addresses:
- Go to **Policies **> **Access Control** > **Firewall** >** IP & FQDN Groups**.
- In the **Source IPv4 Groups** tab, click **Add Source IPv4 Group**.
- Enter a **Name** for the source IPv4 address group (e.g., Social Media). Only alphanumeric characters, underscores, hyphens, and periods are allowed.
-
Enter any number of IPv4 addresses. You can enter:
- An address (e.g., 198.51.100.100)
- A range of addresses (e.g., 192.0.2.1-192.0.2.10)
- An address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- (Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).