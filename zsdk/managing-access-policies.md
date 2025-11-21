# Managing Access Policies
Source: https://help.zscaler.com/zsdk/managing-access-policies
PDF: https://help.zscaler.com/pdf/com/en/1507456.pdf

When you create access policy rules, you implement security-based access control for specific application segments.
On the Access Policy page (Policy > Access Policy), you can:
- [Add an access policy.](#addAccessPolicy)
- [Copy an access policy.](#copyAccessPolicy)
- [Edit an access policy.](#editAccessPolicy)
- [Delete an access policy.](#deleteAccessPolicy)
[]
-
Click **Add Rule**.
The **Add Access Policy** window appears.
-
In the** Add Access Policy **window:
- **Name**: Enter an access policy name that does not contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
- **Description**:** **(Optional) Enter a description.
- For **Action**:
- **Rule Action**: Select **Allow Access** or **Block Access**.
- **Message to User**: (Optional) Enter the message that you want to display to users with blocked access. Zscaler recommends that you include helpful information so that users understand why they are being denied access.
- For **Traffic Steering**, select an **App Connector Selection Method** to determine which App Connector groups or server groups are allowed access.
- **All App Connector groups for the application**
-
**Specific App Connector groups or Server groups for the application**
If selected, then you can:
- **App Connector Groups**: Select at least one App Connector group.
- **Server Groups**: Select at least one server group.
- For **Criteria**, click **Add Criteria** to add any of the available criteria types. The drop-down menu only displays criteria that are not already in use by the rule.
[See image.](#addaccesspolicy)
- Click **Save**.
[]
-
Click the **Copy** icon for an access policy.
The **Copy Access Policy** window appears.
-
In the** Copy Access Policy **window, modify the copied information as needed.
[See image.](#copyaccesspolicy)
- Click **Save**.
[]
-
Click the **Edit** icon for an access policy.
The **Edit Access Policy** window appears.
-
In the** Edit Access Policy **window, modify the fields as needed.
[See image.](#editaccesspolicy)
- Click **Save**.
[]
-
Click the **Delete** icon for an access policy.
The **Confirm: Delete Action** window appears.
-
Click **Delete** to confirm.
[See image.](#deleteaccesspolicy)
Understanding Access Policy
Access policy consists of the following parts:
- [Details](#details)
- [Action](#action)
- [Traffic Steering](#traffic)
- [Criteria](#criteria)
Limitations of Access Policies
There are limits to the number of application segments applied to a rule. For a complete list of ranges and limitations for access policy rules, see [Ranges & Limitations](/zsdk/ranges-limitations#Policies).
[]The access policy details identify your access policy by name and description. Access policy details contain:
- **Name**: The access policy name.
- **Description**: The description of the access policy.
[]The access policy creates an action to grant access or block access to the user, based on their user group. You can create a message that appears if the user is blocked access. You can configure the following for **Action**:
-
**Rule Action**: To create an action for the access policy to grant access to a mobile app for a user group.
By default, ZSDK blocks access to [applications](/zsdk/about-applications) and [segment groups](/zsdk/about-segment-groups) for users until you configure policy rules that explicitly allow access. So, you only need to configure policy rules to block access for specific circumstances or to require approval. For example, if you want to allow access to all applications in your organization for most users but block access for some users, you can configure one policy rule that blocks access for those specific users while another rule allows access to all other users. ZSDK uses a first-match principle when evaluating policies, so for this scenario, you must list the block rule before the allow rule. To learn more, see [Policy Evaluation Order](/zpa/about-access-and-application-group-policies#policy-evaluation-order). To learn more about use cases that call for policy rules that block access, see [Access Policy Configuration Examples](/zpa/policy-configuration-examples).
- **Pop-Up Message to User**: (Optional) Enter the message you want to display to users with blocked access. Zscaler recommends that you include helpful information for users to understand why they are being denied access.
[]The access policy allows you to configure specific App Connector groups or server groups for access to your mobile applications. You can configure the **App Connector Selection Method** for **Traffic Steering **to select which clients gain access to the mobile app.
- If **All App Connector groups for the application** is selected and there are more than 48 configured for your organization, then only 48 App Connector groups are used.
- If **Specific App Connector groups or server groups for the application** is selected, then you can select which App Connector groups or server groups are used.
The maximum limit of selected App Connector groups is 48.
[]
Select the criteria for the access policy to provide or block access to mobile apps. The available criteria are:
- [Applications](#apps)
- [Client Types](#client)
- [Country Code](#country)
- [Device Profile](#deviceprofile)
The Boolean logic used between **Criteria** is always displayed. For example, when a user requests access to an application, the policy rule is evaluated to check whether an application segment OR its segment group are present AND whether any of the Security Assertion Markup Language attributes are applicable to the user making the request before it grants or denies access. You can always view the **Rule Action** and **Criteria** as well as the applied Boolean logic on the [Access Policy page](/zsdk/about-access-policy).
[See image.](#addcriteria)
[]Choose the application segments and segment groups to which this rule applies:
-
**Application Segments**: Choose the [application segments](/zsdk/about-applications), and click **Done**. You can search for a specific application segment, click **Select All** to apply all applications segments, or click **Clear Selection** to remove all selections. The [application segments you've configured](/zsdk/defining-and-managing-application-segments) appear in the menu. There is no limit to the number you can select.
If you add multiple application segments to the policy rule, the access policy uses an OR Boolean operator between them.
-
**Segment Groups**: Choose the [segment groups](/zsdk/about-segment-groups), and click **Done**. You can search for a specific segment group, click **Select All** to apply all segment groups, or click **Clear Selection** to remove all selections. The [segment groups you've configured](/zsdk/managing-segment-groups) appear in the menu. There is no limit to the number you can select.
If you add multiple segment groups to the policy rule, the access policy uses an OR Boolean operator between them.
[]Choose the client types to which the rule applies, and click **Done**. You can search for a specific client type, click **Select All** to apply all client types, or click **Clear Selection** to remove all selections. The valid client types are:
- **Prelogin Tunnel**: Applications that require access before the user is authenticated. Zscaler issues a client certificate that is valid for 7 days.
- **Zero Trust Tunnel**: Applications that require access after the user is authenticated. Zscaler issues a client certificate that is valid for 6 months.
If you add multiple client types to the policy rule, the access policy uses an OR Boolean operator between them.
[]Choose the country code to which the rule applies, and click **Done**. You can search for a specific country code, click **Select All** to apply all country codes, or click **Clear Selection** to remove all selections.
If you add multiple country codes to the policy rule, the access policy uses an OR Boolean operator between them.
[]Choose the device profile to which the rule applies, and click **Done**. You can search for a specific device profile, click **Select All** to apply all device profiles, or click **Clear Selection** to remove all selections.
If you add multiple device profiles to the policy rule, the access policy uses an OR Boolean operator between them.
[]
![Add Criteria to an Access Policy](/downloads/zsdk/policies/managing-access-policies/AccessPolicies-Configuring-Criteria-2.png)
[]
![Add Access Policy Window](/downloads/zsdk/policies/managing-access-policies/AccessPolicies-Add-Access-Policy-2.png)
[]
![Copy Access Policy Window](/downloads/zsdk/policies/managing-access-policies/AccessPolicies-CopyAccess-Policy-2.png)
[]
![Edit Access Policy Window](/downloads/zsdk/policies/managing-access-policies/AccessPolicies-Edit-Access-Policy-2.png)
[]
![Confirm Deletion](/downloads/zsdk/managing-access-policies/AccessPolicies-Delete-Access-Policy.png)