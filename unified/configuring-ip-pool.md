# Configuring IP Pool
Source: https://help.zscaler.com/unified/configuring-ip-pool
PDF: https://help.zscaler.com/pdf/com/en/1516521.pdf

You can use the default IP Pool which is automatically created, or configure a customized IP pool of IP addresses based on your requirements.
To add an IP pool:
- Go to **Policies **> **Access Control** > **Firewall **> **IP & FQDN Groups**.
- On the **IP Pool** tab, select **Add IP Pool**.
- In the **Add IP pool** window:
- **Name**: Enter a name for the IP pool. Only alphanumeric characters, underscores, hyphens, and periods are allowed.
- **IP Addresses**: Enter any number of IP addresses in the following formats.
- An IP address (for example, `198.51.100.100`)
- A range of IP addresses (for example, `192.0.2.1-192.0.2.10`)
- An IP address with a netmask (for example, `203.0.113.0/24`)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Description**: (Optional) Enter additional notes or information about the IP pool. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the changes](/unified/saving-and-activating-changes-admin-portal).