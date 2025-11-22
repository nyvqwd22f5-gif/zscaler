# Adding Rules to the Bandwidth Control Policy
Source: https://help.zscaler.com/zia/adding-rules-bandwidth-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1399881.pdf

[Watch a video about Bandwidth Control.](https://fast.wistia.net/embed/iframe/z9h2f81rrs)
Adding rules to the [Bandwidth Control](/zia/about-bandwidth-control) policy is one of the tasks you must complete when configuring the Bandwidth Control policy. For a full list of tasks, see [Configuring the Bandwidth Control Policy](/zia/configuring-bandwidth-control-policy) and see [Bandwidth Control Policy Example](/zia/bandwidth-control-policy-example) for a sample policy. When adding a rule for the Bandwidth Control policy, you can add a rule from the beginning or copy an existing rule.
You can also define the [bandwidth classes](/zia/about-bandwidth-classes) that you want to include in the Bandwidth Control policy. This can be done before or while you're adding the rules.
Adding Rules to the Bandwidth Control Policy
You must first enable Bandwidth Control for the location before you can add rules to the Bandwidth Control policy. To learn how to enable Bandwidth Control for a location, see Step 1 in [Configuring the Bandwidth Control Policy](/zia/configuring-bandwidth-control-policy#1).
To add rules to the Bandwidth Control policy:
- Go to **Policy **> **Bandwidth Control**.
-
Click **Add Bandwidth Control Rule**. You can also copy an existing rule by clicking the [Duplicate icon](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
The **Add Bandwidth Control Rule **window appears.
[See image.](#add-bandwidth)
-
In the **Add Bandwidth Control Rule **window, enter the **Bandwidth Control Rule **attributes :
- **Rule Order:** Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule’s place in the order. You can change the value, but if you've enabled [Admin Rank](/zia/what-admin-rank), your assigned admin rank determines the rule order values you can select.
- **Rule Name: **Enter a name for the rule.
- **Admin Rank:** Enter a value from 0 to 7 (0 is the highest rank). Your assigned [admin rank](/zia/what-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule's admin rank determines the value you can select in the rule order so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Status:** An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order. The service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/zia/about-rule-labels).
[See image.](#bandwidth-control-rule)
-
Define the **Criteria**:
- **Bandwidth Classes: **Select the [bandwidth classes](/zia/about-bandwidth-classes) to which you want to apply this rule. You first must add URLs or cloud applications to predefined or custom bandwidth classes. Select any number of bandwidth classes. You can also search for bandwidth classes or click the **Add** icon to add a new bandwidth class.
-
**Locations:** Select** Any** to apply this rule to all [locations](/zia/about-locations), or select up to 32 locations. You can search for a location or click the **Add** icon to add a new location. You must enable Bandwidth Control for these locations and specify the download and upload bandwidth limits for each location.
Contact Zscaler Support to increase the limit of **Locations**.
- **Location Groups**: Select **Any** to apply the rule to all [location groups](/zia/about-location-groups), or select up to 32 location groups. You can also search for a location group.
- **Time: **Select **Always** to apply this rule to all [time intervals](/zia/about-time-intervals), or select up to two time intervals. You can also search for a time interval or click the **Add** icon to add a new time interval.
- []**Protocols**: If you have the Firewall subscription, select the protocols to which the rule applies:
- **DNS over HTTPS**: Bandwidth from DNS over HTTPS websites.
- **FTP over HTTP**: Bandwidth from FTP over HTTP websites.
- **HTTP**: Bandwidth from HTTP websites.
- **HTTP Proxy**: Bandwidth from HTTP proxy servers.
- **HTTPS**: Bandwidth from HTTP websites encrypted by TLS/SSL.
- **Native FTP**: Bandwidth from native FTP servers.
- **SSL**: Bandwidth from SSL traffic that isn't decrypted. For example, bandwidth from hosts you've [exempted from SSL Inspection](/zia/about-ssl-inspection#configure-ssl-inspection-policy).
- **Tunnel**: Bandwidth from unidentified encrypted traffic. For example, bandwidth from tunneling applications (e.g., Telnet or SSH) that are encapsulated in HTTP or HTTPS.
- **Tunnel SSL**: Undecodable protocol within an SSL connection.
- **WebSocket**: Bandwidth from WebSocket websites.
- **WebSocket SSL**: Bandwidth from WebSocket websites encrypted by SSL.
[See image.](#criteria-section)
-
Define the **Action**:
- **Min. Bandwidth: **Select the minimum percentage of a location’s [bandwidth](/zia/about-bandwidth-control) you want to be guaranteed for each selected bandwidth class. This percentage includes bandwidth for uploads and downloads.
- **Max. Bandwidth: **Select the maximum percentage of a location’s [bandwidth](/zia/about-bandwidth-control) you want to be guaranteed for each selected bandwidth class. This percentage includes bandwidth for uploads and downloads.
[See image.](#action-image)
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
The Bandwidth Control policy has two predefined rules that you can edit or delete, and a default rule that you can edit but not delete. You can also edit or delete any administrator-defined rule.
To learn how this policy fits into the overall order of policy enforcement, see [Understanding Policy Enforcement](/zia/understanding-policy-enforcement).
[]![Add Bandwidth Control Rule Window](/downloads/tech-pubs-drafts/zia-draft-articles/adding-rules-bandwidth-control-policy-draft-doc57092/Add%20Bandwidth%20Control%20Rule_1.png)
[]![Bandwidth Control Rule Section](/downloads/tech-pubs-drafts/zia-draft-articles/adding-rules-bandwidth-control-policy-draft-doc57092/Bandwidth%20Control%20Rule%20Section.png)
[]![Bandwidth Control Rule Criteria Section](/downloads/tech-pubs-drafts/zia-draft-articles/adding-rules-bandwidth-control-policy-draft-doc57092/Bandwidth%20Criteria_0.png)
[]![Bandwidth Control Rule Action Section](/downloads/tech-pubs-drafts/zia-draft-articles/adding-rules-bandwidth-control-policy-draft-doc57092/Bandwidth%20Action_0.png)