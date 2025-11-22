# About Cloud App Control
Source: https://help.zscaler.com/zia/about-cloud-app-control
PDF: https://help.zscaler.com/pdf/com/en/1399386.pdf

[Watch a video about Cloud App Control Policy](https://fast.wistia.net/embed/iframe/0bvxqh6pko)
The Cloud App Control policy provides granular control over popular websites and applications. Cloud apps are organized by function into [categories](/zia/cloud-app-categories) for easy reference and to facilitate defining rules for similar apps.
You can [create rules](/zia/how-do-i-add-rules-cloud-app-control-policy) to control how your users access specific cloud applications. For example, you can define a rule for instant messaging apps that allows chatting, but blocks file transfers.
The Cloud App Control policy rules can also be applied to Internet of Things (IoT) devices from a [location](/zia/configuring-locations) or a [sublocation](/zia/configuring-sublocations) that has the Enforce IoT Policy Control option enabled. You can apply the rules to IoT devices that are identified and classified (e.g., printers, sensors, etc.) by the Zscaler AI/ML under the IoT group in the Device Groups criterion.
The Cloud App Control policy provides the following benefits and enables you to:
- Provide enhanced security and management of cloud application usage.
- Monitor actions within cloud applications.
- Allow administrators to set rules for applications and specific application instances.
- Ensure secure data-usage policies.
Zscaler provides the Allow Unauthenticated Traffic for IoT Classifications predefined rules for all the [categories](/zia/cloud-app-categories). You can enable these rules to temporarily allow unauthenticated traffic that could be blocked by other rules, so that the Zscaler AI/ML can classify devices. These rules are disabled by default and cannot be deleted. You can modify the Rule Order, Rule Status, Rule Label, and Description for these rules and cannot edit other attributes.
Additionally, you can define a daily quota by bandwidth or time. When users browse these sites after their quota has been reached, the Zscaler service displays a message that explains that the content cannot be viewed because they exceeded their daily quota.
For information on the order in which the service enforces all policies, including this policy, see [Understanding Policy Enforcement](/zia/understanding-policy-enforcement).
About the Cloud App Control Policy Page
On the Cloud App Control Policy page (Policy > URL & Cloud App Control > Cloud App Control Policy), you can do the following:
- [Configure a Cloud App Control rule](/zia/adding-rules-cloud-app-control-policy).
- View the** **[Recommended Policy](/zia/recommended-url-cloud-app-control-policy).
- Select one of the following **View by** options to see the Cloud App Control rules accordingly:
-
**Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#rule-order-cloud-app)
-
**Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels.
You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#rule-label-cloud-app)
- Search for a Cloud App Control rule.
- View a list of all configured Cloud App Control rules. For each rule, you can see the following:
- **Rule Order**: The policy rule order number. Cloud App Control rules are evaluated in ascending numerical order.
- **Admin Rank**: The Admin Rank for this rule. This is only visible if you have enabled it in the [Advanced Settings](/zia/about-advanced-settings).
- **Rule Name**: The name of the policy rule.
- **Criteria**: The policy rule's criteria (i.e., Applications, Users, Departments, etc.).
-
**Action**: Displays whether the policy rule is disabled or what's set to **Allow**, **Block**, or **Isolate**.
The **Isolate** action is available only if Isolation is enabled for your organization and if the rule is not for DNS over HTTPS apps.
- **Label and Description**: The label and description of the policy rule, if available.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- [Edit or duplicate a Cloud App Control rule](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- Go to the **URL Filtering Policy** tab. To learn more, see [About URL Filtering](/zia/about-url-filtering).
- Go to the **Advanced Policy Settings** tab. To learn more, see [Configuring Advanced Policy Settings](/zia/configuring-advanced-url-policy-settings).
**![Zscaler's Cloud App Control page and the buttons, icons, and fields used to manage Cloud App policies](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/about-cloud-app-control/URL%26CLOUD%20APP%20CONTROL_0.png)
**
[]![Zscaler's Cloud App Control page with Rule Order view selected.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/cloud-apps/configuring-cloud-app-policies/about-cloud-app-control/ZIA-Cloud-App-Control-Policy-Page-Viewby-Rule-Order.png)
[]![Zscaler's Cloud App Control page with Rule Label view selected.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/cloud-apps/configuring-cloud-app-policies/about-cloud-app-control/ZIA-Cloud-App-Control-Policy-Page-Viewby-Rule-Label.png)