# Configuring the Mobile App Store Control Policy
Source: https://help.zscaler.com/unified/configuring-mobile-app-store-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1495971.pdf

The Mobile App Store Control policy allows you to restrict app downloads to specific app stores.
To configure the Mobile App Store Control policy:
- Go to **Policies **>** Access Control **>** Internet & SaaS **>** Mobile App Store Control**.
- Click **Add Mobile App Store Control Rule**.
- Specify the Mobile App Store Control rule attributes:
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the Rule Order reflects this rule's place in the order. You can change the value, but if you've enabled [Admin Rank](/unified/about-admin-rank), your assigned admin rank determines the Rule Order values you can select.
- **Admin Rank**: This option appears if you enable [Admin Rank](/unified/about-admin-rank) on the [Advanced Settings](/unified/configuring-advanced-settings) page.
Enter a value from 0-7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule's Admin Rank determines the value you can select in the Rule Order, so that a rule with a higher Admin Rank always precedes a rule with a lower Admin Rank.
- **Rule Name**: Enter a unique name for the Mobile App Store Control rule, or use the default name.
- **Rule Status**: A rule’s status can be **Enabled** or **Disabled**. An enabled rule is actively enforced. A disabled rule is not actively enforced; neither does it lose its place in the Rule Order scheme. The service simply skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/unified/about-rule-labels).
- Define the criteria:
- **App Stores**:** **Select **Any** to block all app stores, or select any number of app stores you want to block.
- **Users**:** **Select **Any** to apply the rule to all [users](/unified/about-users), or select up to 32 users under General Users. If you've enabled the [Policy for Unauthenticated Traffic](/unified/configuring-policies-unauthenticated-traffic), you can select Special Users to apply this rule to all unauthenticated users, or select specific types of unauthenticated users. You can search for users or click the **Add** icon to add a new user.
- **Groups**:** **Select **Any** to apply the rule to all [groups](/unified/about-groups), or select up to 32 groups. You can search for groups or click the **Add** icon to add a new group.
-
**Departments**:** **Select** Any** to apply the rule to all [departments](/unified/about-departments), or select any number of departments. If you've enabled the [Policy for Unauthenticated Traffic](/unified/configuring-policies-unauthenticated-traffic), you can select Special Departments to apply this rule to all unauthenticated transactions. You can search for departments or click the **Add** icon to add a new department.
Any rule that applies to [unauthenticated traffic](/unified/configuring-policies-unauthenticated-traffic) must apply to all Groups or Departments. If you have chosen to apply this rule to unauthenticated traffic for either **Users** or **Departments**, select **Any **from the drop-down menus for **Groups** and **Departments**.
-
**Locations**:** **Select **Any** to apply the rule to all [locations](/unified/about-locations), or select up to 32 locations. You can also search for a location or click the **Add** icon to add a new location.
Contact Zscaler Support to increase the limit of Users, Groups, or Locations.
- **Location Groups**: Select **Any** to apply the rule to all [location groups](/unified/about-location-groups), or select up to 32 location groups. You can also search for a location group.
- **Time**: Select **Always** to apply this rule to all [time intervals](/unified/defining-time-intervals), or select up to two time intervals. You can also search for a time interval or click the **Add** icon to add a new time interval.
- Choose the action:
- **Application Download**: Select to **Allow** or **Block** application downloads from the app store. If you choose to block an app store, users can browse the app store, but they are blocked from downloading apps from it.
- (Optional) Enter a description. The description cannot exceed 10,240 characters.
- Click **Save** and activate the change.
To see how this policy fits into the overall order of policy enforcement, see [Understanding Policy Enforcement](/unified/understanding-policy-enforcement).