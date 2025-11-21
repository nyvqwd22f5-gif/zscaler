# Configuring the Bandwidth Control Policy
Source: https://help.zscaler.com/zia/configuring-bandwidth-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1398771.pdf

[Click to watch a video about Configuring the Bandwidth Control Policy.](https://fast.wistia.net/embed/iframe/z9h2f81rrs)
The bandwidth control policy specifies how an organization's bandwidth is allocated. You can add rules that prioritize business-critical apps and ensure that recreational or non-business-critical applications do not affect productivity. It contains a default rule, which you can edit, but not delete. To learn more, see [About Bandwidth Control](/zia/about-bandwidth-control).
You can also define the bandwidth classes that you want to include in the bandwidth control policy before you add rules to the policy or while you're adding the rules. To learn more, see [About Bandwidth Classes](/zia/about-bandwidth-classes).
To see how this policy fits into the overall order of policy enforcement, see [About Policy Enforcement](/zia/about-policy-enforcement).
Policy Execution
The Bandwidth Control rules consist of a series of logical operators between their criteria. The rules are triggered based on the result of the following logical operations between the criteria:
Bandwidth Classes (`AND`) [Location Groups (`OR`) Locations] (`AND`) Time (`AND`) Protocols.
Configuring the Bandwidth Control Policy
To configure the Bandwidth Control policy of a location:
- [Enable Bandwidth Control for the Location.](#A)
- [Enable Bandwidth Control for a Sublocation.](#B)
- [Add Rules to the Bandwidth Control Policy.](/zia/adding-rules-bandwidth-control-policy)
You can then go to the Bandwidth Control [dashboard](/zia/about-dashboards) to view your organization's bandwidth usage in real time or go to **Analytics **>** Interactive Reports** to view the Bandwidth Control standard reports.
[]To enable bandwidth control for the location:
- Go to **Administration** > **Location Management** > **Locations**.
- [Edit](/zia/editing-deleting-duplicating-items) the location.
The **Edit Location** window appears.
- In the **Edit Location** window, configure the **Bandwidth Control** section:
- **Enforce Bandwidth Control: **Enable to enforce bandwidth control for the location.
- **Download (Mbps): **Specify the maximum bandwidth limit.
- **Upload (Mbps): **Specify the maximum bandwidth limit.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]To enable bandwidth control for sublocations:
- Go to **Administration** > **Location Management** > **Locations**.
- [Edit](/zia/editing-deleting-duplicating-items) the sublocation.
The** Edit Sub-Location** window appears.
- In the **Edit Sub-Location** window, configure the **Bandwidth Control** section:
- **Use Location Bandwidth**:** **Enable this so that any potential bandwidth available at the location will be given to this sublocation. Sharing happens on a first-come, first-serve basis when using this option.
- **Override**: Enable on the sublocation and then specify the maximum bandwidth limits for **Download (Mbps)** and **Upload (Mbps)**. This bandwidth is dedicated to the sublocation and not shared with others.
- **Disable**: Disable bandwidth control for this sublocation.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).