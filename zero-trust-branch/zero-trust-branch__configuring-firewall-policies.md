# Configuring Firewall Policies
Source: https://help.zscaler.com/zero-trust-branch/configuring-firewall-policies
PDF: https://help.zscaler.com/pdf/com/en/1532549.pdf

Firewall policies in Zero Trust Branch allow you to define how traffic is controlled between zones, sites, or network segments. Policies are essential for defining and enforcing access controls between different network segments, applications, and user groups, thereby enhancing security and compliance. Policies can apply to individual sources and destinations or to source and destination zones, and be based on networks, MAC addresses, devices, and Software as a Service (SaaS) apps. To learn more, see [Managing Objects](/zero-trust-branch/managing-objects).
To configure a [firewall policy](/zero-trust-branch/understanding-firewall-policies) in the Zero Trust Branch Admin Portal:
- Go to **Firewall **> **Policies**. Click the tab for the scope (**Global Policies**, **Template Policies**, or **Site Policies**) under which you want to create the policy.
-
Click **Configure **> **Add Policy**.
[See image.](#add-policy-policies-page)
The **Add Policy **drawer appears.
-
In the **Add Policy **drawer:
- **Action**: Choose the policy action (**Accept**, **Reject**, **Drop**, or **Skip**) from the drop-down menu.
- **Name**: Enter a name for the policy.
- **Site**: The site to which the policy must be applied. This option is applicable only for site policies.
- **Source Zone**: (Optional) Select the LAN or WAN zone to which this policy must apply from the drop-down menu. Select the **Negate **checkbox if you want the policy to apply to all source zones except the ones selected.
- **Destination Zone**: (Optional) Select the LAN or WAN zone to which this policy must apply from the drop-down menu. Select the **Negate **checkbox if you want the policy to apply to all destination zones except the ones selected.
- **Source**: Select the sources to which this policy must apply from the drop-down menu. Select the **Negate **checkbox if you want the policy to apply to all sources except the ones selected.
- **Add CIDR**: Enter the IP address range in CIDR format for the selected sources. This option appears only if the **Subnet/host **type source is selected.
- **Destination**: Select the destinations to which this policy must apply from the drop-down menu. Select the **Negate **checkbox if you want the policy to apply to all destinations except the ones selected.
- **Add CIDR**: Enter the IP address range in CIDR format for the selected destinations. This option appears only if the **Subnet/host **type destination is selected.
- **Ports**: Select the port category to which this policy must apply from the drop-down menu. You can select **All**, **Allowed Ports**, **Custom Port**, or any objects created for ports. If you select **Custom Port**, enter the required ports, and click **Add**.
- **Time Schedule Group**: If the policy applies to a specific time schedule, select it from the drop-down menu.
- **Disable Log Throttling**: Select this option to disable throttling. When log throttling is enabled, the Zero Trust Branch log flows once per tuple per hour.
- **Ransomware Kill Switch**: Select the color code corresponding to the threat levels for this policy. To learn more, see [About the Ransomware Kill Switch.](/zero-trust-branch/about-ransomware-kill-switch)
- **Description**: Enter a description for the policy.
[See image.](#add-policy-drawer)
-
Click **Add.**
The firewall policy is created.
-
Click **Commit **to apply the changes.
[See image.](#commit-policy)
Based on your requirements, you can edit, reorder, clone, or delete policies. To learn more, see [Managing Firewall Policies](/zero-trust-branch/managing-firewall-policies).
[]![Policies page showing the Add Policy button](/downloads/zero-trust-branch/administration/firewall-configuration/configuring-firewall-policy/ztb-configure-add-policy.jpg)
[]![Configuring a firewall policy in the Zero Trust Branch Admin Portal.](/downloads/zero-trust-branch/administration/firewall-configuration/configuring-firewall-policy/ztb-add-firewall-policy-drawer.jpg)
[]![Policies page shwoing the Commit button](/downloads/zero-trust-branch/administration/firewall-configuration/configuring-firewall-policy/ztb-commit-button.jpg)