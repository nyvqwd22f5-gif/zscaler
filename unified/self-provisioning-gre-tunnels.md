# Self-Provisioning of GRE Tunnels
Source: https://help.zscaler.com/zia/self-provisioning-gre-tunnels
PDF: https://help.zscaler.com/pdf/com/en/1401931.pdf

[Watch a video about GRE Tunnels and Static IP.](https://fast.wistia.net/embed/iframe/4lx8k9aqum)
You can self-provision your GRE tunnels to connect to the Zscaler service via the ZIA Admin Portal. To learn more, see [About GRE Tunnels](/zia/about-gre-tunnels).
Self-provisioning of GRE tunnels towards ZIA Private Service Edge clusters is only supported for clusters deployed on public IP space (i.e., a non-NAT environment). If you need to build a GRE tunnel towards a Private Service Edge cluster deployed within a NAT environment, submit a support ticket from your Admin Portal.
To configure the self-service GRE tunnels from the ZIA Admin Portal:
- Go to **Administration** > **Static IPs & GRE Tunnels**.
- Click **Add GRE Tunnels**. The** Add GRE Tunnel Configuration** wizard opens. If you edit an existing configuration, the **Edit GRE Tunnel Configuration** wizard opens.
- On the **Source IP** tab:
-
**Static IP Address**: Select an available static IP address that you want to map to your GRE tunnel. You can map only one static IP address with a GRE tunnel. You cannot modify this field if you are editing an existing configuration.
A static IP address that is already mapped with a location is not available for mapping with a GRE tunnel and therefore does not appear in the drop-down menu.
- **Description**: (Optional) Enter additional information or note about the GRE Tunnel.
- **Managed By**: Select if the GRE tunnel is managed by yourself or a specific Zscaler partner. You cannot modify this field if you are editing an existing configuration.
- Click **Next**.
- On the **Data Center** tab:
- **Domestic Preference**: <!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Enable this option to prioritize Zscaler data centers from the country of origin of the IP address, even if they are farther away from other Zscaler data centers.
- **Primary Data Center VIP**: <!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}-->
Select a primary data center VIP address that is active on the Zscaler cloud. This field lists the 5 geographically closest data centers to choose from. By default, an active data center VIP is auto-selected based on geographical proximity. If **Domestic Preference** is enabled, then an active data center VIP within the country of origin of the IP address is auto-selected.
-
**Secondary Data Center VIP**: Select a secondary data center VIP address that is active on the Zscaler cloud. Ensure that the primary and the secondary VIP destinations do not point to the same data center. This field lists the 5 geographically closest data centers to choose from. By default, an active data center VIP is auto-selected based on geographical proximity. If **Domestic Preference** is enabled, then an active data center VIP within the country of origin of the IP address is auto-selected.
- If your organization uses Private Service Edges, the **Primary** and **Secondary Data Center VIP** fields first list Private Service Edge VIP addresses.
- Data centers marked with the Do Not Provision (DNP) flag on the [config.zscaler.com](http://config.zscaler.com) page are not displayed in the **Primary **and **Secondary Data Center VIP** lists. To learn more about these data centers, contact Zscaler Support.
- Click **Next**.
- On the **Internal IP Range** tab:
- **Is Unnumbered IP**: Enable this option if you do not require an internal IP address on each side of your GRE tunnel.
- **Select Internal GRE IP Range**: Select an internal IP address range from the default pool of ten available IP address ranges on the Zscaler cloud. You can also use the search bar to search for and select from other available RFC1918 IP address ranges (10.0. 0.0/8, 172.16. 0.0/12, 192.168. 0.0/16).
- Click **Next**.
- From the **Review** tab, review and edit your configurations if you want to change any of the values.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).