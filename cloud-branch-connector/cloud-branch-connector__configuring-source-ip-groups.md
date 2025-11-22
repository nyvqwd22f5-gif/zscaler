# Configuring Source IP Groups
Source: https://help.zscaler.com/cloud-branch-connector/configuring-source-ip-groups
PDF: https://help.zscaler.com/pdf/com/en/1420456.pdf

Grouping source IP addresses together enables easier creation of policies. The source IP groups are used for forwarding policies.
To create a source IP address group:
- Go to **Administration **>** ****IP & FQDN Groups**.
- On the **Source IP Groups** tab, select **Add Source IP Group**.
[See image.](#AddSourceiPGroup)
[![Adding a Source IP Group in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/firewall-filtering/configuring-source-ip-groups/Add%20Source%20IP%20Group%20Brnch.jpg)
]
- In the **Add Source IP ****Group** window:
- **Name**: Enter a name for the source IP address group. Only alphanumeric characters, underscores, hyphens, and periods are allowed.
- **IP Addresses**: Enter any number of IP addresses in the following formats.
- An IP address (for example, `198.51.100.100`)
- A range of IP addresses (for example, `192.0.2.1-192.0.2.10`)
- An IP address with a netmask (for example, `203.0.113.0/24`)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Description**: (Optional) Enter additional notes or information about the source IP group. The description cannot exceed 10,240 characters.
[See image.](#SourceIPGroupWindow)
[![Add Source IP Group window in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/firewall-filtering/configuring-source-ip-groups/Add%20Source%20IP%20Group_0.jpg)
]
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).