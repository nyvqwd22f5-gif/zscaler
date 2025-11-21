# Understanding Policies
Source: https://help.zscaler.com/unified/understanding-policies
PDF: https://help.zscaler.com/pdf/com/en/1494996.pdf

Users cannot access any internal applications you've configured for Private Applications, regardless of whether you [explicitly defined your applications](/zpa/about-application-access) or [enable application discovery](/unified/about-application-discovery), until you configure policies for them. You can configure the following policy types: access policies, client forwarding policies, isolation policies, and timeout policies. If you are using the Log Streaming Service (LSS), you can also configure log streaming policies for information captured by a log receiver. To learn more, see [Configuring a Log Receiver](/unified/configuring-log-receiver#Step2).
Private Applications use the Name Identifier (NameID) within a SAML assertion for [IdP configuration](/unified/about-idp-configuration) and authentication. Using NameID as a SAML attribute within access and timeout policy rules is not supported.
However, you can use the value associated with NameID within your policy rule criteria by explicitly defining a user attribute (e.g., Email Address, User Name, etc.). In your IdP's SAML assertion, the user attribute can use the same value, and then you can include this attribute in your policy rule criteria.
- [See example SAML JSON](#SAMLJSON_NameIDExample)
The following policies can be applied to your organization:
- Access Policy (Policies > Access Control > Private Applications > Access Policy): Access policy rules enable you to implement role-based access control. This allows you to define rules that determine who has access to an application. To learn more, see [About Access Policy](/unified/about-access-policy). To view examples of how an organization can configure access policy rules for a variety of scenarios, see [Access Policy Configuration Examples](/unified/access-policy-configuration-examples).
- AppProtection Policy (Policies > Cybersecurity > Inline Security > Protection Policies): AppProtection policy rules allow you to create rules that define when application requests need to go through an AppProtection control. To learn more, see [About AppProtection Policy](/unified/about-appprotection-policy).
- Browser Protection Policy (Policies > Cybersecurity > Inline Security > Protection Policies): Browser Protection policy rules allow you to create rules that define Browser Protection requests for Browser Protection profiles. To learn more, see [About Browser Protection Policy](/unified/about-browser-protection-policy).
- Client Forwarding Policy (Infrastructure > Private Access > Client Connector Policies > Client Forwarding Policies): Client forwarding policy rules allow you to create rules that define when application requests are forwarded from the Zscaler Client Connector. To learn more, see [About Client Forwarding Policy](/unified/about-client-forwarding-policy).
- Isolation Policy (Policies > Access Control > Clientless > Isolation Policy: Isolation policy rules allow you to create rules that define what isolation profiles to use or bypass. To learn more, see [About Isolation Policy](/unified/about-isolation-policy).
- Privileged Remote Access policies (Policies > Access Control > Clientless > Privileged Policy): Privileged Remote Access (PRA) policies consist of privileged credentials policies and privileged capabilities policies. Privileged credentials policy rules allow you to assign privileged consoles to include designated credentials. To learn more, see [About Privileged Credentials Policy](/unified/about-privileged-credentials-policy). Privileged capabilities policy rules allow you to set permissions for File Transfer, Clipboard, and Session Recording features. To learn more, see[ About Privileged Capabilities Policy](/unified/about-privileged-capabilities-policy).
- Timeout Policy (Policies > Access Control > Private Applications > Timeout Policy): Timeout policy rules allow you to create granular rules that control authentication timeout and idle connection timeout settings. To learn more, see [About Timeout Policy](/unified/about-timeout-policy).
- Redirection Policy (Infrastructure > Private Access > Client Connector Policies > Redirection Policy): Redirection policy rules allow you to set criteria for preferring Private Service Edges over Public Service Edges. To learn more, see [About Redirection Policy](/unified/about-redirection-policy).
[]Policy Evaluation Order
Policy rules are evaluated using the most specific application segment and a top-down, first-match principle. For example, when a user requests a specific application, all of your configured policies starting with the first rule in a set of policy rules are evaluated. As soon as it finds a policy that matches the criteria that was specified in a rule, it enforces that policy rule and disregards all other rules that follow, including any potentially conflicting rules.
Policy rules are evaluated in the following order:
- When the application request is received, Private Applications first tries to identify the rule that matches the criteria. If application segments are part of the criteria, the rule corresponding to the most specific application segment for a given domain name or IP address is chosen.
- Your policy rules are evaluated then execute the specified action for the rule. Within a set of policy rules, if none of the policy rules apply then the following applies:
- For access policy, access to the application is implicitly set to Block Access. This is also the case if you do not define any policy rules at all within the Admin Portal. To learn more, see [About Access Policy](/unified/about-access-policy).
- For timeout policy, the default timeout policy rule is applied. To learn more, see [About Timeout Policy](/unified/about-timeout-policy).
- For client forwarding policy, access to the application is implicitly set to Forward to Private Apps. This is also the case if you do not define any policy rules at all within the Admin Portal. To learn more, see [About Client Forwarding Policy](/unified/about-client-forwarding-policy).
- For isolation policy, the default isolation policy rule is applied. To learn more, see [About Isolation Policy](/unified/about-isolation-policy).
These policy evaluation order guidelines apply in the following scenarios:
- [Conflicting Access Policy Rules](#conflictingglobalpolicies)
- [Conflicting Access Policy Rules with Segment Groups](#conflictingglobalandapp)
- []An organization configures an access policy rule that allows all applications for the "Marketing Dept."
[See image.](#image1)
- The organization also configures a policy that denies the "Operations Apps" segment group to the "Marketing Dept."
[See image.](#image2)
In this scenario, even if the organization configured the latter policy denying the "Operations App" segment group to the "Marketing Dept," users from "Marketing Dept" still have access to the "Operations Apps" segment group. When a user from the "Marketing Dept" requests an application from the "Operations App" segment group, the access policy rules are checked first and then the policy rule allowing Marketing users access to any application is found. It then applies that access policy rule and immediately stops checking any other policies, because a matching policy was found for the user.
[]![Add Access Policy with SAML Attributes defined](/downloads/zpa/documentation-knowledgebase/policies/about-policies/about-policies/zpa-accesspolicy-globalexample_1.png)
[]![Add Access Policy with SAML Attributes and Segment Groups defined](/downloads/zpa/documentation-knowledgebase/policies/about-policies/about-policies/zpa-accesspolicy-globalexample2_1.png)
- []An organization configures an access policy rule that allows access to any applications for any user.
- It temporarily wants to block the "Sales" group from accessing any applications, so it configures an additional access policy rule denying them access.
[See image.](#image3)
In this scenario, users in the "Sales" group are not blocked from accessing any applications because these users match the first policy rule, which allows any users access to any applications. The first access policy rule is applied and the second policy rule is disregarded. To resolve this issue, the order of the access policy rules must be modified so that the policy rule blocking the "Sales" group comes before the policy rule allowing any users access to any applications.
[]![Access Policy page with rules displayed in table](/downloads/zpa/documentation-knowledgebase/policies/about-policies/about-policies/zpa-ruleorderexample_1.png)
[]{
"nameid": "jane.doe@example.com"
"orgid": "86753098675309696"
"saml_attributes": {
"Group": "Private App-users",
"First Name": "Jane",
"Last Name": "Doe",
"Email Address": "jane.doe@example.com"
}
}