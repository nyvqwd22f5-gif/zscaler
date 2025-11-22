# Configuring DNS Application Groups
Source: https://help.zscaler.com/zia/adding-dns-application-groups
PDF: https://help.zscaler.com/pdf/com/en/1400681.pdf

[Watch a video about DNS Application Groups](https://fast.wistia.net/embed/iframe/31ohx9mn1h)
To group together the types of [DNS tunnels](/zia/detecting-and-controlling-dns-tunnels) and other web applications that you want to control in a [DNS Control rule](/zia/configuring-dns-control-policy), create a DNS Application Group. To learn more, see [About DNS Application Groups](/zia/about-dns-application-groups).
To create a group:
- Go to **Administration** > **Network Applications**.
[See image.](#img1)
- Go to the **DNS Applications Groups** tab.
- In the **DNS Application Groups **tab, click **Add DNS Application Group**.
[See image.](#img2)
- Enter a **Name** for the application group. It can have a maximum of 255 characters and can include any standard characters including spaces.
- Add **DNS Tunnels & Network Apps** to the rule. Click the down arrow by and select any number of tunnels and applications that you want to include in the group. You might create a group to include DNS tunnel methods and web applications. that should be allowed for some users, while another could include tunnel methods that are blocked for all users. Click the category name to include all the tunnels or applications in a category. When you are finished, click **Done**.
[See image.](#img3)
- (Optional) Enter a **Description** to add any additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal). After saving and activation, the DNS Application Groups are available for use when creating DNS Filtering rules. They will enable you to Allow or Block the types of traffic that you have identified in your group.
[]![Screenshot of the Administration menu with Network Applications highlighted](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/firewall/firewall-policies-resources/adding-dns-application-groups/zia-select-network-apps.png)
[]![Screenshot of the DNS Application Group menu with the Add DNS Application Group highlighted](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/firewall/firewall-policies-resources/draft-adding-dns-application-groups/zia-add-dns-application-group.png)
[]![Screenshot of the Add DNS Application group with the drop-down menu exposed.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/firewall/firewall-policies-resources/adding-dns-application-groups/zia-select-dns-apps.png)