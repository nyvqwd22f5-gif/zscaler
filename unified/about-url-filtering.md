# About URL Filtering
Source: https://help.zscaler.com/zia/about-url-filtering
PDF: https://help.zscaler.com/pdf/com/en/1399306.pdf

[Watch a video about URL Filtering Policy](https://fast.wistia.net/embed/iframe/jqu9x18c3e)
The URL Filtering policy consists of [rules](/zia/configuring-url-filtering-policy) that you define. When you add a rule, you specify criteria, such as [URL categories](/zia/about-url-categories), [users](/zia/about-users), [groups](/zia/about-groups), [departments](/zia/about-departments), [locations](/zia/about-locations), and [time intervals](/zia/about-time-intervals). There is also a [recommended policy](/zia/recommended-url-cloud-app-control-policy) for URL Filtering.
To allow granular control of filtering, the service organizes URLs into a hierarchy of categories. To learn more about URL categories, see [About URL Categories](/zia/about-url-categories).
By default, the Cloud App Control policy takes precedence over the URL Filtering policy. The service applies the Cloud App Control policy to a web transaction before applying the URL Filtering policy. To change this setting and have the service apply the URL Filtering policy even if it has already applied a Cloud App Control policy, go to Advanced Settings and enable [Allow Cascading to URL Filtering](/zia/about-advanced-settings). For information on the order in which the service enforces all policies, including this policy, see [About Policy Enforcement](/zia/about-policy-enforcement).
URL Filtering provides the following benefits and enables you to:
- Limit exposure to liability by managing access to web content based on a site's categorization using granular URL filtering rules.
- Reduce the number of uncategorized domains with the help of inline AI/ML-based content categorization.
- Quickly identify new domains (Registered, Observed, and Revived).
- Block or caution users with specific End User Notifications (EUNs).
The URL Filtering policy rules can also be applied to IoT devices from a [location](/zia/configuring-locations) or a [sublocation](/zia/configuring-sublocations) that has the Enforce IoT Policy Control option enabled. You can apply the rules to IoT devices that are identified and classified (e.g., Printers, Sensors, etc.) by the Zscaler AI/ML under the IoT group in the Device Groups criterion.
Zscaler provides the Allow Unauthenticated Traffic for IoT Classifications predefined rule for the URL Filtering policy. You can enable this rule to temporarily allow unauthenticated traffic that could be blocked by other rules, so that the Zscaler AI/ML can classify devices. This rule is disabled by default and cannot be deleted. You can modify the Rule Order, Rule Status, Rule Label, and Description for this rule and cannot edit other attributes.
Associating Rules with EUNs
You can create rules that block or caution users and associate them with specific EUNs. For example, your organization has two networks and they each have a web server that hosts an EUN. You can create two different rules that redirect users to the appropriate EUN.
The EUNs that you specify in the rules take precedence over the default EUN that you configure on the Administration > End User Notifications page. Therefore, when a user is blocked or warned due to a rule that is associated with an EUN, the service displays the EUN associated with the rule and not the default EUN.
When you configure a rule, you can specify one of the following actions:
- **Allow**:** **The service allows access to the URLs in the selected categories. You can still restrict access by specifying a daily quota for bandwidth and time. For example, you can allow your users to access Entertainment and Recreation sites, but restrict the bandwidth allowed for these sites so they don't interfere with business-critical applications. The daily time quota is based on the time that the rule is created. For example, if the rule is created at 11:00 AM PST, then the quota is renewed at 11:00 AM PST the next day.
- **Caution**:** **When a user tries to access a site, the service displays a [Caution notification](/zia/about-acceptable-use-policy-and-end-user-notifications#caution). You can use the system-defined notification, customize the text, or create your own notification and direct users to it. [See image.](#caution)
-
**Block**:** **The service displays a [Block notification](/zia/about-acceptable-use-policy-and-end-user-notifications#block). You can use the system-defined notification, customize the text, or create your own notification and direct users to it. [See image.](#block)
Additionally, you can allow some users or groups to override the block with the **Allow Override** option. For example, you can block students from accessing YouTube but allow the teachers. Teachers are prompted to enter their override password. This can be company-provided credentials such as single sign-on credentials or hosted database credentials based on the [Enable Identity-based Block Override](/zia/configuring-advanced-url-policy-settings#Enable-block-override) settings. Permitted users are allowed to access the blocked page only during their current browser session. They are required to reauthenticate when they try to access it in another browser session.
[See image.](#allow-override)
- **Isolate**: The service [isolates](/zia/about-cloud-browser-isolation) all the traffic to the URLs in the selected categories through a remote browser.
About the URL Filtering Page
On the URL Filtering page (Policy > URL & Cloud App Control), you can do the following:
- [Configure a URL Filtering rule](/zia/configuring-url-filtering-policy).
- Click **Recommended Policy **to view the policy Zscaler recommends.
- Select one of the following **View by** option to see the URL Filtering rules accordingly:
-
**Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#rule-order-URL-filtering)
-
**Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels.
You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#rule-label-URL-filtering)
- Search for a URL Filtering Rule.
- View a list of all configured URL Filtering policy rules. For each policy rule, you can view the following information:
-
**Rule Order**: The policy rule order number. URL Filtering policy rules are evaluated in ascending numerical order. You can sort this column.
The evaluation of the policy rules stops at the first match.
- **Admin Rank**: The admin rank for this rule. This is only visible if you have enabled it in the [Advanced Settings](/zia/about-advanced-settings). You can sort this column.
- **Rule Name**: The name of the policy rule. You can sort this column.
- **Criteria**: The policy rule's criteria (i.e., Users, Departments, etc.).
-
**Action**: Displays whether the policy rule is disabled or whether it's set to **Allow**,** Caution**, **Block**,** **or **Isolate**.
The **Isolate** action is available only if Isolation is enabled for your organization.
- **Label and Description**: The label and description of the policy rule, if available.
- [Modify the table and its columns](/zia/using-tables).
- [Edit or duplicate a URL Filtering policy rule](/zia/editing-deleting-duplicating-items).
- Click the **Cloud App Control Policy** tab to configure your Cloud App Control policies. To learn more, see [About Cloud App Control](/zia/about-cloud-app-control).
- Click the **Advanced Policy Settings** tab to configure your advanced URL policy settings. To learn more, see [Configuring Advanced URL Policy Settings](/zia/configuring-advanced-url-policy-settings).
![The URL Filtering Policy page showing buttons and list used to manage URL rules](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/url-filtering/configuring-url-filtering/about-url-filtering/ZIA-URL-Filtering-Policy-Page.png)
[][![Caution notification for Zscaler end users trying to access a site](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/url-filtering/configuring-url-filtering/about-url-filtering/caution_notification_for_end_users_screenshot.png)
]
[][![Block notification for Zscaler end users trying to access a blocked site](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/url-filtering/configuring-url-filtering/about-url-filtering/block_notification_for_end_users_screenshot_.png)
]
[][![Caution notification highlighting override option for Zscaler end users](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/url-filtering/configuring-url-filtering/about-url-filtering/block_notification_override_for_users_screenshot.png)
]
[]![The URL Filtering Policy page with Rule Order view selected.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/url-filtering/configuring-url-filtering/about-url-filtering/ZIA-URL-Filtering-Policy-Page-Viewby-Rule-Order.png)
[]![The URL Filtering Policy Page with Rule Label View Selected.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/url-filtering/configuring-url-filtering/about-url-filtering/ZIA-URL-Filtering-Policy-Page-Viewby-Rule-Label.png)