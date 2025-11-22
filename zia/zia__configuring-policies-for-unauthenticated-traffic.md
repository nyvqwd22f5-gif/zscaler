# Configuring Policies for Unauthenticated Traffic
Source: https://help.zscaler.com/zia/configuring-policies-for-unauthenticated-traffic
PDF: https://help.zscaler.com/pdf/com/en/1398691.pdf

There might be scenarios in which the Zscaler service does not identify the user sending traffic to the service. For example, the service does not authenticate user traffic to URLs or cloud apps you have selected to [exempt from authentication](/zia/exempting-urls-cloud-apps-authentication). In another example, the service might not authenticate user traffic because it is encrypted and [SSL inspection ](/zia/deploying-ssl-inspection)is not enabled.
For policies where you can specify users and departments in the criteria, the Zscaler service enables you to specify which rules the service applies to such unauthenticated traffic. If your organization has a default block on web traffic (i.e., a URL Filtering rule that blocks all traffic, which is not explicitly allowed through the URL Filtering policy), this feature can help you ensure that lack of authentication does not lead to an unnecessary block of user traffic.
The following applies when configuring a policy for unauthenticated traffic:
- You must explicitly enable this feature in [Advanced Settings](/zia/about-advanced-settings) before you can use it.
- Any rule that applies to unauthenticated traffic also applies to specific users, groups, and departments if they are selected.
- This feature only applies to locations that have authentication enabled.
When the feature is enabled in Advanced Settings, you can specify whether the policy rule applies to unauthenticated traffic under the Department criteria. For more granularity, you can specify the types of unauthenticated traffic to which the policy rule applies under the Users criteria. For example, to apply a rule only when traffic is unauthenticated due to an [exemption you specified](/zia/how-do-i-exempt-specific-urls-or-cloud-apps-authentication), as opposed to another factor.
Configuring a Policy for Unauthenticated Traffic
To configure a policy for unauthenticated traffic:
- Enable the Policy for Unauthenticated Traffic feature in Advanced Settings:
- Go to **Administration** > **Advanced Settings**.
-
Under **Policy for Unauthenticated Traffic**, turn on **Enable Policy for Unauthenticated Traffic**.
[See image.](#image-1)
- Click** Save**.
-
When selecting criteria for policy rules, you can choose to apply a rule only to specific types of unauthenticated traffic, or to all unauthenticated traffic.
This option is available for all policies where you can specify users and departments in the criteria.
- To apply a rule to specific types of traffic:
- Go to the applicable policy.
For example, **Policy** > **URL & Cloud App Control** > **URL Filtering Policy** or** Policy **>** Firewall Control **>** Firewall Filtering Policy**.
- In the **Users **drop-down menu, select any users from the following user categories:
- **General Users**: The users to which you want the rule to apply.
-
**Special Users**: The users you can select the types of unauthenticated traffic for and also apply the rule to. The types of unauthenticated traffic are:
- **Unauthenticated User Agent**:** **User traffic that cannot be authenticated because the user agent cannot be authenticated by the configured authentication method.
- **Unsupported Method**: User traffic that cannot be authenticated because of HTTP methods that are not normally supported, such as FIND or PROPBIND.
- **Unauthenticated Protocol**: User traffic that cannot be authenticated by the configured authentication method (for example, un-decrypted HTTPS traffic).
- **Unauthenticated Proxy Port User**: User traffic that is coming from port 9480. ZIA Public Service Edges accept web requests on ports 80, 443, 9400, 9480, and 9443. Any traffic generated from a known gateway location and destined to Public Service Edges with the proxy port of 9480 bypass authentication.
- **Miscellaneous Unauthenticated Transactions**:** **User traffic that cannot be authenticated due to miscellaneous issues.
- **Authentication Bypass URL**: User traffic to URLs or cloud apps you have exempted from authentication. HTTP requests that do not support cookie-based authentication, such as CONNECT and OPTIONS, are logged in this category.
- **Unknown Kerberos User**: User traffic that cannot be authenticated because it comes from an unknown Kerberos user.
The following image is for a rule under the URL Filtering policy.
[See image.](#image-2)
-
If you have chosen to apply this rule to unauthenticated traffic for either **Users** or **Departments**, don't select a group** **from the **Groups** drop-down menu.
If you don't select a value for a criterion, the system ignores it in the policy evaluation.
- After specifying other criteria for the rule as necessary, click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
- To apply a rule to all unauthenticated traffic:
- Go to the applicable policy.
For example, **Policy** > **URL & Cloud App Control** > **URL Filtering Policy or Policy** > **Firewall Control** > **Firewall Filtering Policy**.
-
In the **Departments** drop-down menu, select any departments from the following department categories:
- **Regular Departments**: The departments to which you want the rule to apply.
- **Special Departments**: The departments for which you can select **Unauthenticated Transactions** if you want the rule to also apply to any unauthenticated traffic.
You can choose a combination of regular departments with the **Unauthenticated Transactions **selected.
The following image is for a rule under the URL Filtering policy.
[See image.](#image-3)
-
If you have chosen to apply this rule to unauthenticated traffic for either **Users** or **Departments**, don't select a group** **from the **Groups** drop-down menus.
If you don't select a value for a criterion, the system ignores it in the policy evaluation.
- After specifying other criteria for the rule as necessary, click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![The Enable Policy for Unauthenticated Traffic toggle is enabled.](/downloads/zia/policies/configuring-policies-for-unauthenticated-traffic/ZIA-enable-policy-unauthenticated-traffic.png)
[]![Creating a URL Filtering rule for General Users.](/downloads/zia/policies/configuring-policies-for-unauthenticated-traffic/ZIA-general-users.png)
[]![Applying a Zscaler URL Filtering policy rule to all unauthenticated traffic](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/about-policies/how-do-i-configure-policy-unauthenticated-traffic/ZIA-URLFiltering-UnauthenticatedDepts-6.1.png)