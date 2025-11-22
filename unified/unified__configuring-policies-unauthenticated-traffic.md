# Configuring Policies for Unauthenticated Traffic
Source: https://help.zscaler.com/unified/configuring-policies-unauthenticated-traffic
PDF: https://help.zscaler.com/pdf/com/en/1494596.pdf

There might be scenarios in which the Zscaler service does not identify the user sending traffic to the service. For example, the service does not authenticate user traffic to URLs or cloud apps you have selected to [exempt from authentication](/unified/exempting-urls-and-cloud-apps-authentication). In another example, the service might not authenticate user traffic because it is encrypted and [SSL inspection ](/unified/deploying-ssl-inspection)is not enabled.
For policies where you can specify users and departments in the criteria, the Zscaler service enables you to specify which rules the service applies to such unauthenticated traffic. If your organization has a default block on web traffic (i.e., a URL filtering rule that blocks all traffic, which is not explicitly allowed through the URL filtering policy), this feature can help you ensure that lack of authentication does not lead to an unnecessary block of user traffic.
The following applies when configuring a policy for unauthenticated traffic:
- You must explicitly enable this feature in [Advanced Settings](/unified/configuring-advanced-settings) before you can use it.
- Any rule that applies to unauthenticated traffic also applies to specific users, groups, and departments if they are selected.
Once the feature is enabled in Advanced Settings, you can specify whether the policy rule applies to unauthenticated traffic under the Department criteria. For more granularity, you can specify the types of unauthenticated traffic to which the policy rule applies under the Users criteria. For example, to apply a rule only when traffic is unauthenticated due to an [exemption you specified](/unified/exempting-urls-and-cloud-apps-authentication), as opposed to another factor.
To configure a policy for unauthenticated traffic:
-
Enable the Policy for Unauthenticated Traffic feature in Advanced Settings:
- Go to **Policies** > **Common Configuration **> **Advanced** > **Advanced Settings**.
- Under **Policy for Unauthenticated Traffic**, turn on **Enable Policy for Unauthenticated Traffic**.
- Click** Save**.
![Screenshot of Enable Policy for Unauthenticated Traffic](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/about-policies/how-do-i-configure-policy-unauthenticated-traffic/zia-enable-unauth-pol0.png)
-
When selecting criteria for policy rules, you can choose to apply a rule only to specific types of unauthenticated traffic, or to all unauthenticated traffic.
This option is available for all policies where you can specify Users and Departments in the criteria.
- To apply a rule to specific types of traffic:
-
Navigate to the applicable policy.
For example, **Policies** > **Access Control** > **Internet & SaaS** > **URL Filtering** or** Policies **>** Access Control **>** Firewall **>** Firewall Filtering Policy**.
-
In the **Users **drop-down, select any users from the following user categories:
- **General Users**: The users to which you want the rule to apply.
- **Special Users**: The users for which you can select the types of unauthenticated traffic to which you also want the rule to apply. The types of unauthenticated traffic are:
- **Unauthenticated User Agent**:** **User traffic that cannot be authenticated because the user-agent cannot be authenticated by the configured authentication method.
- **Unsupported Method**: User traffic that cannot be authenticated because of HTTP methods that are not normally supported, such as FIND or PROPBIND.
- **Unauthenticated Protocol**: User traffic that cannot be authenticated by the configured authentication method (for example, un-decrypted HTTPS traffic).
- **Unauthenticated Proxy Port User**: User traffic that is coming from port 9480. Internet & SaaS Public Service Edges accept web requests on ports 80, 443, 9400, 9480, and 9443. Any traffic generated from a known gateway location and destined to Public Service Edges with the proxy port of 9480 bypass authentication.
- **Miscellaneous Unauthenticated Transactions**:** **User traffic that cannot be authenticated due to miscellaneous issues.
- **Authentication Bypass URL**: User traffic to URLs or cloud apps you have selected under Authentication Bypass.
- **Unknown Kerberos User**: User traffic that cannot be authenticated because it comes from an unknown Kerberos user.
The example below is for a rule under the URL filtering policy.
[See image.](#image-2)
-
If you have chosen to apply this rule to unauthenticated traffic for either **Users** or **Departments**, don't select a group** **from the **Groups** drop-down menu.
If you don't select a value for a criterion, the system ignores it in the policy evaluation.
- After specifying other criteria for the rule as necessary, click **Save **and activate the change.
- To apply a rule to all unauthenticated traffic:
- Navigate to the applicable policy.
For example, **Policies** > **Access Control** > **Internet & SaaS** > **URL Filtering** or** Policies **>** Access Control **>** Firewall **>** Firewall Filtering Policy**.
-
In the **Departments** drop-down, select any departments from the following department categories:
- **Regular Departments**: The departments to which you want the rule to apply.
- **Special Departments**: The departments for which you can select **Unauthenticated Transactions** if you want the rule to also apply to any unauthenticated traffic.
You can choose a combination of regular departments with the **Unauthenticated Transactions **selected.
The example below is for a rule under the URL filtering policy.
[See image.](#image-3)
-
If you have chosen to apply this rule to unauthenticated traffic for either **Users** or **Departments**, don't select a group** **from the **Groups** drop-down menus.
If you don't select a value for a criterion, the system ignores it in the policy evaluation.
- After specifying other criteria for the rule as necessary, click **Save **and activate the change.
[]![Screenshot of applying a Zscaler URL Filtering policy rule to specific types of unauthenticated traffic](/downloads/zia/policies/configuring-policies-for-unauthenticated-traffic/zia-special-users_newui3.png)
[]![Applying a Zscaler URL Filtering policy rule to all unauthenticated traffic](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/about-policies/how-do-i-configure-policy-unauthenticated-traffic/ZIA-URLFiltering-UnauthenticatedDepts-6.1.png)