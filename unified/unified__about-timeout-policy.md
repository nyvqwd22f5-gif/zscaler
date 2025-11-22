# About Timeout Policy
Source: https://help.zscaler.com/unified/about-timeout-policy
PDF: https://help.zscaler.com/pdf/com/en/1492066.pdf

A timeout policy lets you configure granular rules that control authentication and idle connection timeouts.
Timeout policy configurations provide the following benefits and enable you to:
- Specify the period after which users are prompted to reauthenticate to maintain their access to private applications.
- Outline inactivity periods after which a user connection needs to be reinitiated.
- Configure authentication and timeout intervals on a per user group or application basis, if desired.
You can configure timeout policy rules for:
- Authentication Timeout: The time interval used to determine when a user must reauthenticate to access an application.
- It is only evaluated when a user attempts to access an application. After a user's session has expired for a specific application, the user is only prompted to reauthenticate at the next attempt to access that application.
- You can define authentication timeout policies for a single application segment or all application segments.
Zscaler Client Connector certificates have a validity of 365 days from the date of enrollment. If the authentication timeout is set to **Never**, users are only prompted to re-enroll to renew device certificates. To renew device certificates, click **Authenticate **in the** Private Access** screen. In some cases, the certificate renewal might fail because of connectivity issues to the identity provider (IdP). If this occurs, you might need to log out (request a logout password from your administrator if required) and log back in to renew the certificate.
- Idle Connection Timeout: A user's application session idle timeout. An idle connection timeout expiration does not force reauthentication.
For a complete list of ranges and limitations for timeout policy rules, see [Ranges & Limitations](/unified/ranges-limitations).
Using Granular Rules for Users and Segment Groups
For each timeout policy rule, you can specify the users and segment groups the rule applies to. This allows you to have different authentication and idle connection timeout settings for different users and segment groups. So, even if a user must reauthenticate to continue using an application in one segment group, the user might still be able to continue using an application in another segment group depending on the timeout policy.
In the example rules configured below, the first rule requires users from the Sales department to reauthenticate every two days to continue accessing applications from the Sales App Group. However, the second rule requires the same users to reauthenticate every three days to continue accessing applications from the HR App Group.
[See image.](#img_exreauth)
[]Using the Default Timeout Policy Rule
The default timeout policy rule specifies that all users have to authenticate every 7 days for any application, and that their sessions never end due to an idle connection timeout expiration. You can edit the default rule, and it will always apply to all users authenticating from any IdP if you do not configure your own timeout policy rules. So, if you've configured some rules that apply to specific users or segment groups, the default rule will still apply to all other remaining users or segment groups from any IdP.
The [Privileged Remote Access (PRA) portal](/unified/accessing-privileged-remote-access-portal) and [user portal](/unified/about-user-portals) for Browser Access are dependent on the Default Timeout Policy rule's set authentication timeout.
[See image.](#img_exdefault)
Viewing User and Application Session Status in Zscaler Client Connector
On the **Private Access **menu, users can find the status for both their user and application sessions.
- The **Service Status** displays the status of the user session. This status is not impacted by your timeout policy.
- The **Authentication Status** reflects whether the user needs to reauthenticate.
[See image.](#ZApp_UserAppSessions)
Understanding the Reauthentication Process
When reauthentication is required to use an application, users see a notification on their device:
- Users see a notification similar to the following, which is an example message from the default timeout policy rule.
![Warning message within the Zscaler Client Connector](/downloads/zpa/documentation-knowledgebase/policies/reauthentication-policy/about-reauthPolicy/7a556acb-50e0-4e32-a636-760710359930_display.png)
- If you create additional timeout policy rules, you can set a custom notification message for each, so that users know which application requires reauthentication. The following example is a custom notification message.
![Warning message within the Zscaler Client Connector](/downloads/zpa/documentation-knowledgebase/policies/reauthentication-policy/about-reauthPolicy/de7b04cc-8d84-4b79-85f8-f5b0f27f2972_display.png)
Additionally, users see an **Authentication Required** status on the **Private Access** menu. Users must click **Authenticate** and log in with their credentials to continue accessing the application.
[See image.](#ZApp_AuthRequired)
The following guidelines apply:
- When a user reauthenticates to continue with an application session, they get a new SAML assertion. This means that a single reauthentication resets the reauthentication timer for all applications. [See an example.](#payroll)
If your IdP is defined as an application within an application segment, the [Authentication Timeout](/unified/configuring-timeout-policies) for the IdP application must be set to **Never**. If an IdP domain overlaps with a domain configured for [application discovery](/unified/about-application-discovery), you must bypass the IdP domain to avoid user reauthentication failure.
- Because reauthentication settings are defined per segment group and not per individual applications, when a user is active in an application, the user is considered to have been active in all applications that belong to the same group as that application. [See an example.](#activetime)
- The Public Service Edge uses the `notBefore` timestamp in the SAML assertion response to calculate if reauthentication is necessary. This needs to be considered when setting up a timeout policy.
[See another timeout policy example.](#example)
If you need to support reauthentication for application access when single sign-on (SSO) is set up using Microsoft Integrated Windows Authentication (IWA) with Kerberos, you must configure the ADFS, LDAP, and KDC applications within an application segment using the proper ports. You also need to configure a timeout policy rule where the [Authentication Timeout](/unified/configuring-timeout-policies) for these applications are set to **Never**.
About the Timeout Policy Page
On the Timeout Policy page (Policies > Access Control > Private Applications > Timeout Policy), you can do the following:
- Expand all the displayed rows in the table to see more information about each policy rule.
- Show all the rules in the table. The rows remain collapsed. Depending on the number of rules, this can take a few minutes.
By default, the UI displays the first 100 rules. Alternatively, you can scroll to see more rules.
- [Add a new timeout policy rule.](/unified/configuring-timeout-policies)
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all timeout policy rules that were configured. For each rule, you can see:
- **Rule Order**: The policy evaluation order number for the rule. Policy rules are applied based on the order they are listed here. To change the rule order, click on the number and manually enter a new value.
- **Name**: The name of the rule. The description is also displayed here, if available.
- **Timeouts**: Indicates the specified authentication and idle connection timeout intervals. When the row is expanded, it provides a visual representation of the **Criteria** (e.g., [SAML attributes](/unified/about-saml-attributes) per IdP, segment groups, etc.) and Boolean logic used within the rule.
- Copy an existing timeout policy rule's criteria, and use it to create a new rule.
- [Edit an existing timeout policy rule.](/unified/editing-timeout-policies)
- Delete a timeout policy rule.
- Edit the **Default Rule**. To learn more, see [Default Timeout Policy Rule](#DefaultReauthRule) above.
![Example timeout policy rules for users and segment groups within ZPA](/downloads/unified/policies/private-applications/access-control/timeout-policy/about-timeout-policy/about-timeout-policies_0.png)
[]![Timeout Policy page with example rules within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/timeout-policy/about-reauthPolicy/zpa-examplereauthpolicies_0.png)
[]![Timeout Policy page with Default Rule within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/timeout-policy/about-reauthPolicy/zpa-defaultreauthpolicy_0.png)
[]![Zscaler Client Connector window with Private Access page displayed](/downloads/zpa/documentation-knowledgebase/policies/reauthentication-policy/about-reauthPolicy/1a0ceae2-7af2-45b0-9b5d-80de4a428206_display.png)
[]![Zscaler Client Connector window with Private Access page displayed](/downloads/zpa/documentation-knowledgebase/policies/reauthentication-policy/about-reauthPolicy/2b643606-3733-498b-b8ac-6821e477b221_display.png)
[]For example, an organization has a timeout policy that requires reauthentication every three days for the application Payroll, and reauthentication every day for the application Benefits (for both applications, users never have to reauthenticate due to idle time).
- At 9:00 AM on Monday, Lisa opens the application Payroll.
- After that application, Lisa does not access any other apps until Thursday at 9:00 AM when she attempts to use Payroll again.
- She reauthenticates upon being prompted and accesses Payroll.
- Then at noon on the same day, Lisa accesses the application Benefits. She has not used this application in over a week, but she is not required to reauthenticate now because she just reauthenticated three hours ago when attempting to access the application Payroll.
[]For example, the applications Sales1 and Sales2 belong to the same application group, SalesApps. A policy is set for the SalesApps group requiring reauthentication after an idle time of 1 hour.
- At 9:00 AM, Lanuk begins using Sales1.
- Then at 9:30 AM, he stops using Sales1 and begins using another app, Sales2.
- He works in Sales2 for two hours, until 11:30 AM.
- At that point he goes back to Sales1 and is able to use that app again without reauthenticating, even if he's been technically inactive in that app for over an hour. This is because Sales1 belongs to the same application group as Sales2, and Lanuk has been using Sales2 until now. Activity in one application counts as activity for all other applications in the same application group.
[]An organization has configured the following timeout policy rules:
- The first rule requires Sales group users to reauthenticate every day to continue accessing applications from the Sales App Group.
- The second rule requires Sales group users to reauthenticate every three days to continue accessing applications from the HR App Group.
![Timeout Policy page with example rules within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/timeout-policy/about-reauthPolicy/zpa-examplereauthpolicies2_0.png)
With these policy rules:
- At 9:00 AM: Jane, from the Sales group, begins using three applications:
- BudgetApp from the Sales App Group, where users must reauthenticate every day, or after an idle time of 1 hour.
- ComplianceApp from the HR App Group, where users must reauthenticate every three days, or after an idle time of 5 hours.
- PayrollApp from the Finance App Group, which falls under the default rule where users must reauthenticate every 7 days, but never because of idle time.
- At 11:00 AM:
- Jane stops using BudgetApp and PayrollApp.
- She continues using ComplianceApp.
- At 12:30 PM:
- While actively working in ComplianceApp, Jane opens the BudgetApp again to access some quick data. Upon attempting to use the application, she sees the following dialog, because the app falls under a rule that requires reauthentication after one hour of idle time:
![de7b04cc-8d84-4b79-85f8-f5b0f27f2972_display.png](/downloads/zpa/documentation-knowledgebase/policies/reauthentication-policy/about-reauthPolicy/de7b04cc-8d84-4b79-85f8-f5b0f27f2972_display.png)
Jane reauthenticates, and is able to access BudgetApp again. With this reauthentication, Jane has reset the reauthentication timer not just for BudgetApp, but also all other applications, including ComplianceApp and PayrollApp. She can access ComplianceApp for another 5 hours without reauthenticating. The PayrollApp is covered by the default rule, so she now has another 7 days before she has to reauthenticate to access that application.