# Configuring the Bandwidth Control Policy
Source: https://help.zscaler.com/unified/configuring-bandwidth-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1497646.pdf

The bandwidth control policy specifies how an organization's bandwidth is allocated. You can add rules that prioritize business-critical apps and ensure that recreational or non-business critical applications do not affect productivity. It contains a default rule, which you can edit, but not delete. To learn more, see [About Bandwidth Control](/unified/about-bandwidth-control).
You can also define the bandwidth classes that you want to include in the bandwidth control policy before you add rules to the policy or while you're adding the rules. To learn more, see [About Bandwidth Classes](/unified/about-bandwidth-classes).
To see how this policy fits into the overall order of policy enforcement, see [Understanding Policy Enforcement](/unified/understanding-policy-enforcement).
To configure the Bandwidth Control policy of a location:
- [1. Enable Bandwidth Control for the Location.](#A)
- [2. Enable Bandwidth Control for a Sub-Location.](#B)
- [3. Add Rules to the Bandwidth Control Policy.](/unified/adding-rules-bandwidth-control-policy)
You can then go to the Bandwidth Control [dashboard](/unified/about-dashboards) to view your organization's bandwidth usage in real time or go to **Analytics **> **Internet & SaaS **> **Analytics **>** Interactive Reports** to view the Bandwidth Control standard reports.
[]To enable bandwidth control for the location:
- Go to **Infrastructure** > **Internet & SaaS** > **Traffic Forwarding** > **Location Management** > **Locations**.
-
[Edit](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal) the location.
The **Edit Location** window appears.
- In the **Edit Location** window, configure the **Bandwidth Control** section:
- **Enforce Bandwidth Control: **Enable to enforce bandwidth control for the location.
- **Download (Mbps): **Specify the maximum bandwidth limit.
- **Upload (Mbps): **Specify the maximum bandwidth limit.
- Click **Save** and activate the change.
[]To enable bandwidth control for sub-locations:
- Go to **Infrastructure** > **Internet & SaaS** > **Traffic Forwarding** > **Location Management** > **Locations**.
-
[Edit](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal) the sub-location.
The** Edit Sub-Location** window appears.
- In the **Edit Sub-Location** window, configure the **Bandwidth Control** section:
- **Use Location Bandwidth**:** **Enable this so that any potential bandwidth available at the location will be given to this sub-location. Sharing happens on a first-come, first-serve basis when using this option.
- **Override**: Enable on the sub-location and then specify the maximum bandwidth limits for **Download (Mbps)** and **Upload (Mbps)**. This bandwidth is dedicated to the sub-location and not shared with others.
- **Disable**: Disable bandwidth control for this sub-location.
- Click **Save** and activate the change.