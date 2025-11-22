# Configuring Routing Policies
Source: https://help.zscaler.com/zero-trust-branch/configuring-routing-policies
PDF: https://help.zscaler.com/pdf/com/en/1525141.pdf

Zero Trust Branch routing policies provide a secure, scalable, and highly available framework for branch network traffic, enabling you to control traffic from branch sites to specific destinations based on defined criteria.
To configure a [routing policy](/tech-pubs-drafts/understanding-routing-policies) in the Zero Trust Branch Admin Portal:
- Go to **Deployment **> **Sites**.
-
On the **Sites **page, locate the entry for the site for which you want to configure a routing policy, and click the name of the site in the **Site Name **column.
[See image.](#select-site-routing-policy)
-
On the site details page, click the **Routing Policy **tab and then click **Configure**.
[See image.](#click-configure)
-
Click **Add route**.
[See image.](#add-route-button)
The **Add Routing Rule** drawer appears.
-
In the **Add Routing Rule **drawer:
- **Rule Name**: Enter a name for the routing rule.
- **Sources**: Select the sources to which the routing rule must apply from the drop-down menu. Sources can include one or more networks, MAC addresses, devices, and Active Directory (AD) users. Select the **Negate **checkbox if you want the policy to apply to all sources except the ones selected.
- **Add CIDR**: Enter the IP address range in CIDR format for the selected sources. This option appears only if the **Subnet/host** type source is selected.
- **Destinations**: Select the destinations to which the routing rule must apply from the drop-down menu. Destinations can include one or more networks, devices, domains, AD users, Software as a Service (SaaS) apps, and Zscaler Private Access (ZPA) application segments. Select the **Negate **checkbox if you want the policy to apply to all destinations except the ones selected.
- **Add CIDR**: Enter the IP address range in CIDR format for the selected destinations. This option appears only if the **Subnet/host** type destination is selected.
- **Ports**: Select the port category to which this routing rule must apply from the drop-down menu. Select the **Negate **checkbox if you want the policy to apply to all ports except the ones selected. You can select **All**, **Allowed Ports**, **Custom Port**, or any objects created for ports. If you select **Custom Port**, enter the required ports, and click **Add**.
-
**Gateway 1**: The gateway for the site is filled in automatically.
If the site is running Zero Trust Branch gateways in a cluster, the** Gateway 2** section also appears.
- **Nexthop Interface Type**: Select **LAN/WAN**, **ZIA**, or **ZPA **from the drop-down menu. This decides how the traffic should be routed. If you select **LAN/WAN**, provide the following information:
- **Primary Interface**: Select the primary WAN or LAN interface.
- **Nexthop IP**: Enter the IP address of the primary router or gateway to which the traffic must be routed.
- **Secondary Interface**: Select the secondary WAN or LAN interface.
- **Nexthop IP**: Enter the IP address of the secondary router or gateway to which the traffic must be routed.
- **Traffic Distribution**: If WAN is selected as both primary and secondary interfaces, you can select how you want to balance traffic between the primary and secondary nexthops:
- **Best**: Zero Trust Branch decides programmatically how to distribute traffic.
- **Balanced**: Load is balanced between primary and secondary WANs.
- **None**: The primary interface takes as much load as possible.
[See image.](#add-routing-rule-drawer)
-
Click **Save**.
The routing policy is created.
-
Click **Commit **to apply the changes.
[See image.](#commit-rule)
Based on your requirements, you can edit, reorder, or delete policies and configure routing settings. To learn more, see [Managing Routing Policies](/tech-pubs-drafts/managing-routing-policies).
[]![Selecting a site to configure routing policies](/downloads/zero-trust-branch/administration/deployment-configuration/configuring-routing-policies/ztb-select-site-for-routing-policies.jpg)
[]![Site details page showing the option to configure routing policies](/downloads/zero-trust-branch/administration/deployment-configuration/configuring-routing-policies/ztb-click-configure.jpg)
[]![Site details page showing the option to add a route](/downloads/zero-trust-branch/administration/deployment-configuration/configuring-routing-policies/ztb-add-rule-button.jpg)
[]![Configuring a routing rule](/downloads/zero-trust-branch/administration/deployment-configuration/configuring-routing-policies/ztb-add-routing-rule.jpg)
[]![Site details page showing the option to commit changes](/downloads/zero-trust-branch/administration/deployment-configuration/configuring-routing-policies/ztb-commit-routing-rulw.jpg)