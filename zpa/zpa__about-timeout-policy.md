# About Timeout Policy
Source: https://help.zscaler.com/zpa/about-timeout-policy
PDF: https://help.zscaler.com/pdf/com/en/1483796.pdf

A timeout policy lets you configure granular rules that control authentication and idle connection timeouts.
Timeout policy configurations provide the following benefits and enable you to:
- Specify the period after which users are prompted to reauthenticate to ZPA to maintain their access to private applications.
- Outline inactivity periods after which a user connection needs to be reinitiated.
- Configure authentication and timeout intervals on a per user group or application basis, if desired.
You can configure timeout policy rules for:
- Authentication Timeout: The time interval used to determine when a user must reauthenticate to access an application.
- It is only evaluated when a user attempts to access an application. After a user's session has expired for a specific application, the user is only prompted to reauthenticate at the next attempt to access that application.
- You can define authentication timeout policies for a single application segment or all application segments.
Zscaler Client Connector certificates have a validity of 365 days from the date of enrollment. If the authentication timeout is set to **Never**, users are only prompted to re-enroll to renew device certificates. To renew device certificates, click **Authenticate **in the** Private Access** screen of Zscaler Client Connector. In some cases, the certificate renewal might fail because of connectivity issues to the identity provider (IdP). If this occurs, you might need to log out of Zscaler Client Connector (request a logout password from your administrator if required) and log back in to renew the certificate.
- Idle Connection Timeout: A user's application session idle timeout. An idle connection timeout expiration does not force reauthentication.
For a complete list of ranges and limitations for timeout policy rules, see [Ranges & Limitations](/zpa/ranges-limitations#Policies).
Using Granular Rules for Users and Segment Groups
For each timeout policy rule, you can specify the users and segment groups the rule applies to. This allows you to have different authentication and idle connection timeout settings for different users and segment groups. So even if a user must reauthenticate to continue using an application in one segment group, the user might still be able to continue using an application in another segment group depending on the timeout policy.
In the following configured rules example, the first rule requires users from the Sales department to reauthenticate every two days to continue accessing applications from the Sales App Group. However, the second rule requires the same users to reauthenticate every three days to continue accessing applications from the HR App Group.
[See image.](#img_exreauth)
[]Using the Default Timeout Policy Rule
ZPA provides a default timeout policy rule. The default rule specifies that all users have to authenticate every 7 days for any application, and that their sessions never end due to an idle connection timeout expiration. You can edit the default rule, and it will always apply to all users authenticating from any IdP if you do not configure your own timeout policy rules. So if you've configured some rules that apply to specific users or segment groups, the default rule will still apply to all other remaining users or segment groups from any IdP.
To edit the default rule:
- Go to **Policies **> **Timeout Policy**.
- Click **Default Rule**. The **Default Rule** drawer appears.
- Click the **Edit **icon. The **Edit Timeout Policy **window appears.
- Edit the default rule, and then click **Save**.
[See image.](#img_exdefault)
The [Privileged Remote Access (PRA) Portal](/zpa/accessing-privileged-remote-access-portal) and [user portal](/zpa/about-user-portals) for Browser Access depend on the Default Timeout Policy rule's set authentication timeout.
Viewing User and Application Session Status in Zscaler Client Connector
On the **Private Access **menu of Zscaler Client Connector, users can find the status for both their user and application sessions.
- The **Service Status** displays the status of the user session between Zscaler Client Connector and the ZPA Public Service Edge or ZPA Private Service Edge. This status is not impacted by your ZPA timeout policy.
- The **Authentication Status** reflects whether the user needs to reauthenticate.
[See image.](#ZApp_UserAppSessions)
Understanding the Reauthentication Process
When reauthentication is required to use an application, users see a notification on their device:
- Users see a notification similar to the following, which is an example message from the default timeout policy rule.
![Warning message within the Zscaler Client Connector](/downloads/zpa/documentation-knowledgebase/policies/reauthentication-policy/about-reauthPolicy/7a556acb-50e0-4e32-a636-760710359930_display.png)
- If you create additional timeout policy rules, you can set a custom notification message for each, so that users know which application requires reauthentication. The following example is a custom notification message.
![Warning message within the Zscaler Client Connector](/downloads/zpa/documentation-knowledgebase/policies/reauthentication-policy/about-reauthPolicy/de7b04cc-8d84-4b79-85f8-f5b0f27f2972_display.png)
Additionally, users see an **Authentication Required** status on the **Private Access** menu of Zscaler Client Connector. Users must click **Authenticate** and log in with their credentials to continue accessing the application.
[See image.](#ZApp_AuthRequired)
The following guidelines apply:
- When a user reauthenticates to continue with an application session, ZPA gets a new SAML assertion. This means that a single reauthentication resets the reauthentication timer for all applications. [See an example.](#payroll)
If your IdP is defined as an application within an application segment, the [Authentication Timeout](/zpa/configuring-timeout-policies) for the IdP application must be set to **Never**. If an IdP domain overlaps with a domain configured for [application discovery](/zpa/about-application-discovery), you must bypass the IdP domain in ZPA to avoid user reauthentication failure.
- Because reauthentication settings are defined per segment group and not per individual applications, when a user is active in an application, ZPA considers the user to have been active in all applications that belong to the same group as that application. [See an example.](#activetime)
- The ZPA Public Service Edge uses the `notBefore` timestamp in the SAML assertion response to calculate if reauthentication is necessary. This needs to be considered when setting up a timeout policy.
[See another timeout policy example.](#example)
If you need to support reauthentication for application access into ZPA when single sign-on (SSO) is set up using Microsoft Integrated Windows Authentication (IWA) with Kerberos, you must configure the ADFS, LDAP, and KDC applications within an application segment using the proper ports. You also need to configure a timeout policy rule where the [Authentication Timeout](/zpa/configuring-timeout-policies) for these applications is set to **Never**. To learn more, see [Supporting Reauthentication into ZPA via Microsoft IWA with Kerberos](/zpa/supporting-reauthentication-zpa-microsoft-iwa-kerberos).
About the Timeout Policy Page
On the Timeout Policy page (Policy > Timeout Policy), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Timeout Policy page to reflect the most current information.
-
Click the **Settings **icon (![zpa-settings-icon.png](/downloads/zpa/policies/timeout-policy/about-timeout-policy/zpa-settings-icon.png)
) to open the **Terminate All Sessions** drawer. In the **Terminate All Sessions** drawer, you can enable or disable termination of all running application sessions upon timeout according to the timeout policy or access policy action.
The option to enable or disable termination of all running application sessions upon timeout is available only for existing tenants. This option is hidden and automatically enabled for tenants created after November 3, 2022.
- Filter the information that appears in the table. By default, no filters are applied.
- [Add a new timeout policy rule.](/zpa/configuring-timeout-policies)
- Edit the **Default Rule**. To learn more, see [Default Timeout Policy Rule](#DefaultReauthRule).
- Expand all the displayed rows in the table to see more information about each policy rule.
By default, the UI displays the first 100 rules. Alternatively, you can scroll to see more rules.
- View a list of all timeout policy rules that were configured. For each rule, you can see:
- **Rule Order**: The [policy evaluation order](/zpa/about-access-and-application-group-policies#PolicyEvalOrder) number for the rule. ZPA applies policy rules based on the order they are listed here. To change the rule order, click on the number and manually enter a new value.
- **Name**: The name of the rule. The description is also displayed, if available.
- **Status**: The status of the rule (**Enabled** or **Disabled**).
- **Timeouts**: Indicates the specified authentication and idle connection timeout intervals. When the row is expanded, it provides a visual representation of the **Criteria **(e.g., [SAML attributes](/zpa/about-samlattributes) per IdP, segment groups, etc.) and Boolean logic used within the rule.
- Copy an existing timeout policy rule's criteria, and use it to create a new rule.
- [Edit an existing timeout policy rule.](/zpa/editing-timeout-policies)
- Delete a timeout policy rule.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Depending on your ZPA Admin Portal subscriptions, you will see the following ZPA policy options:
- [Access Policy](/zpa/about-access-policy)
- [Client Forwarding Policy](/zpa/about-client-forwarding-policy)
- [Isolation Policy](/zpa/about-isolation-policy)
- [Privileged Policy](/zpa/about-privileged-policy)
- [Security Policy](/zpa/about-security-policy)
- [Redirection Policy](/zpa/about-redirection-policy)
![Viewing and Managing Timeout Policies on the Timeout Policy Page ](/downloads/zpa/policies/timeout-policy/about-timeout-policy/zpa-timeout-policy-page3.png)
[]![Using granular timeout policy rules for users and segment groups within ZPA](/downloads/zpa/policies/timeout-policy/about-timeout-policy/zpa-timeout-policy-page-granular-rules-example.png)
[]![Default timeout policy rule within ZPA](/downloads/zpa/policies/timeout-policy/about-timeout-policy/zpa-timeout-policy-default-rule-drawer.png)
[]![Zscaler Client Connector window with Private Access page displayed](/downloads/zpa/documentation-knowledgebase/policies/reauthentication-policy/about-reauthPolicy/1a0ceae2-7af2-45b0-9b5d-80de4a428206_display.png)
[]![Zscaler Client Connector window with Private Access page displayed](/downloads/zpa/documentation-knowledgebase/policies/reauthentication-policy/about-reauthPolicy/2b643606-3733-498b-b8ac-6821e477b221_display.png)
[]For example, an organization has a timeout policy that requires reauthentication every three days for the application Payroll, and reauthentication every day for the application Benefits (for both applications, users never have to reauthenticate due to idle time).
- At 9:00 AM on Monday, Lisa opens the application Payroll.
- After that application, Lisa does not access any other apps until Thursday at 9:00 AM when she attempts to use Payroll again.
- She reauthenticates upon being prompted and accesses Payroll.
- At noon on the same day, Lisa accesses the application Benefits. She has not used this application in over a week, but she is not required to reauthenticate because she reauthenticated three hours ago when attempting to access the application Payroll.
[]For example, the applications Sales1 and Sales2 belong to the same application group, SalesApps. A policy is set for the SalesApps group requiring reauthentication after an idle time of one hour.
- At 9:00 AM, Lanuk begins using Sales1.
- At 9:30 AM, he stops using Sales1 and begins using another app, Sales2.
- He works in Sales2 for two hours, until 11:30 AM.
- Lanuk goes back to Sales1 and can use that app again without reauthenticating, even if he's been technically inactive in that app for over an hour. This is because Sales1 belongs to the same application group as Sales2, and Lanuk has been using Sales2 until now. Activity in one application counts as activity for all other applications in the same application group.
[]An organization has configured the following timeout policy rules:
- The first rule requires Sales group users to reauthenticate every day to continue accessing applications from the Sales App Group.
- The second rule requires Sales group users to reauthenticate every three days to continue accessing applications from the HR App Group.
![Example timeout policy rules for users and segment groups within ZPA](/downloads/zpa/policies/timeout-policy/about-timeout-policy/zpa-timeout-policy-example-rules-for-segments2.png)
With these policy rules:
- At 9:00 AM: Jane, from the Sales group, begins using three applications:
- BudgetApp from the Sales App Group, where users must reauthenticate every day, or after an idle time of one hour.
- ComplianceApp from the HR App Group, where users must reauthenticate every three days, or after an idle time of 5 hours.
- PayrollApp from the Finance App Group, which falls under the default rule where users must reauthenticate every 7 days, but never because of idle time.
- At 11:00 AM:
- Jane stops using BudgetApp and PayrollApp.
- She continues using ComplianceApp.
- At 12:30 PM:
- While actively working in ComplianceApp, Jane opens the BudgetApp again to access some quick data. Upon attempting to use the application, she sees the following dialog, because the app falls under a rule that requires reauthentication after one hour of idle time:
![de7b04cc-8d84-4b79-85f8-f5b0f27f2972_display.png](/downloads/zpa/documentation-knowledgebase/policies/reauthentication-policy/about-reauthPolicy/de7b04cc-8d84-4b79-85f8-f5b0f27f2972_display.png)
Jane reauthenticates and can access BudgetApp again. With this reauthentication, Jane has reset the reauthentication timer not just for BudgetApp, but also all other applications, including ComplianceApp and PayrollApp. She can access ComplianceApp for another 5 hours without reauthenticating. The PayrollApp is covered by the default rule, so she now has another 7 days before she has to reauthenticate to access that application.