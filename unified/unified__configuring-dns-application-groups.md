# Configuring DNS Application Groups
Source: https://help.zscaler.com/unified/configuring-dns-application-groups
PDF: https://help.zscaler.com/pdf/com/en/1494206.pdf

To group together the types of [DNS tunnels](/unified/detecting-and-controlling-dns-tunnels) and other web applications that you want to control in a [DNS Control rule](/unified/configuring-dns-control-policy), create a DNS Application Group. To learn more, see [About DNS Application Groups](/unified/about-dns-application-groups).
To create a group:
- Go to **Policies** > **Access Control** > **Firewall** > **DNS Application Group**.
- In the **DNS Application Group **tab, click **Add DNS Application Group**.
- Enter a **Name** for the application group. It can have a maximum of 255 characters and can include any standard characters, including spaces.
-
Add **DNS Tunnels & Network Apps** to the rule. Click the down arrow and select any number of tunnels and applications that you want to include in the group. You might create a group to include DNS tunnel methods and web applications that should be allowed for some users, while another could include tunnel methods that are blocked for all users. Click the category name to include all the tunnels or applications in a category. When you are finished, click **Done**.
[See image.](#img3)
- (Optional) Enter a **Description** to add any additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and activate the change. After saving and activation, the DNS Application Groups are available for use when creating DNS Filtering rules. They will enable you to Allow or Block the types of traffic that you have identified in your group.
[]![Screenshot of the Add DNS Application group with the drop-down menu exposed.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/firewall/firewall-policies-resources/adding-dns-application-groups/zia-select-dns-apps.png)