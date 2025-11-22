# Adding Rules to the Bandwidth Control Policy
Source: https://help.zscaler.com/unified/adding-rules-bandwidth-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1497011.pdf

Adding rules to the [Bandwidth Control](/unified/about-bandwidth-control) policy is one of the tasks you must complete when configuring the Bandwidth Control policy. For a full list of tasks, see [Configuring the Bandwidth Control Policy](/unified/configuring-bandwidth-control-policy) and see [Bandwidth Control Policy Example](/unified/bandwidth-control-policy-example) for a sample policy. When adding a rule for the Bandwidth Control policy, you can add a rule from the beginning or copy an existing rule.
You can also define the [bandwidth classes](/unified/about-bandwidth-classes) that you want to include in the Bandwidth Control policy. This can be done before or while you're adding the rules.
Adding Rules to the Bandwidth Control Policy
You must first enable Bandwidth Control for the location before you can add rules to the Bandwidth Control policy. To learn how to enable Bandwidth Control for a location, see Step 1 in [Configuring the Bandwidth Control Policy](/unified/configuring-bandwidth-control-policy).
To add rules to the Bandwidth Control policy:
- Go to **Infrastructure **> **Internet & SaaS** > **Network Policies** > **Bandwidth Control**.
-
Do one of the following:
- Click **Add Bandwidth Control Rule **to add a rule from scratch.
or
- Click the Duplicate icon to copy an existing rule.
The **Add Bandwidth Control Rule **window appears.
- In the **Add Bandwidth Control Rule **window, specify the:
- **Rule Order:** Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the Rule Order reflects this rule’s place in the order. You can change the value, but if you've enabled [Admin Rank](/unified/about-admin-rank), your assigned admin rank determines the Rule Order values you can select.
- **Rule Name: **Enter a name for the rule.
- **Admin Rank:** Enter a value from 0-7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule's Admin Rank determines the value you can select in the rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Status:** An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order. The service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/unified/about-rule-labels).
- Specify the criteria:
- **Bandwidth Classes: **Select the [bandwidth classes](/unified/about-bandwidth-classes) to which you want to apply this rule. You first must add URLs or cloud applications to predefined or custom bandwidth classes. Select any number of bandwidth classes. You can also search for bandwidth classes or click the **Add** icon to add a new bandwidth class.
-
**Locations:** Select** Any** to apply this rule to all [locations](/unified/about-locations), or select up to 32 locations. You can search for a location or click the **Add** icon to add a new location. You must enable Bandwidth Control for these locations and specify the download and upload bandwidth limits for each location.
Contact Zscaler Support to increase the limit of **Locations**.
- **Location Groups**: Select **Any** to apply the rule to all [location groups](/unified/about-location-groups), or select up to 32 location groups. You can also search for a location group.
- **Time: **Select **Always** to apply this rule to all [time intervals](/unified/about-time-intervals), or select up to two time intervals. You can also search for a time interval or click the **Add** icon to add a new time interval.
- []**Protocols**: If you have the Firewall subscription, select the protocols to which the rule applies:
- **DNS over HTTPS**: Bandwidth from DNS over HTTPS websites.
- **FTP over HTTP**: Bandwidth from FTP over HTTP websites.
- **HTTP**: Bandwidth from HTTP websites.
- **HTTP Proxy**: Bandwidth from HTTP proxy servers.
- **HTTPS**: Bandwidth from HTTP websites encrypted by TLS/SSL.
- **Native FTP**: Bandwidth from native FTP servers.
- **SSL**: Bandwidth from SSL traffic that isn't decrypted. For example, bandwidth from hosts you've [exempted from SSL inspection](/unified/about-ssl-inspection).
- **Tunnel**: Bandwidth from unidentified encrypted traffic. For example, bandwidth from tunneling applications (e.g., Telnet or SSH) that are encapsulated in HTTP or HTTPS.
- **Tunnel SSL**: Undecodable protocol within an SSL connection.
- **WebSocket**: Bandwidth from WebSocket websites.
- **WebSocket SSL**: Bandwidth from WebSocket websites encrypted by SSL.
- Specify the action:
- **Min. Bandwidth: **Select the minimum percentage of a location’s [bandwidth](/unified/about-bandwidth-control) you want to be guaranteed for each selected bandwidth class. This percentage includes bandwidth for uploads and downloads.
- **Max. Bandwidth: **Select the maximum percentage of a location’s [bandwidth](/unified/about-bandwidth-control) you want to be guaranteed for each selected bandwidth class. This percentage includes bandwidth for uploads and downloads.
- In the **Description** field, optionally enter additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and activate the change.
The Bandwidth Control policy has two predefined rules that you can edit or delete, and a default rule that you can edit but not delete. You can also edit or delete any administrator-defined rule.
To see how this policy fits into the overall order of policy enforcement, see [Understanding Policy Enforcement](/unified/understanding-policy-enforcement).