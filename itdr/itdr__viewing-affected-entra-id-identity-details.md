# Viewing Affected Entra ID Identity Details
Source: https://help.zscaler.com/itdr/viewing-affected-entra-id-identity-details
PDF: https://help.zscaler.com/pdf/com/en/1531758.pdf

The [Entra ID Posture](/itdr/about-entra-id-posture-dashboard) dashboard displays a list of the top 10 vulnerable identities that are at highest risk in the Entra ID tenant. Having visibility of these 10 identities that are at highest risk helps you to prioritize what issues to focus on first. On the Entra ID Posture dashboard or [Identities](/itdr/viewing-top-vulnerable-entra-id-identities) page, you can click an Entra ID identity to view additional details, such as failed posture checks, associated Okta user account details, recent suspicious changes made to the identity, detected potential identity attacks or threats, Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) snapshots, and assigned Entra and RBAC roles. You can further investigate the issues and swiftly remediate the compromised identity to disrupt the attacker's operations.
On the Entra ID details page, you can view the following information on each tab:
- [Summary](#itdr-entra-id-summary-tab)
- [Posture](#itdr-entra-id-identity-posture-tab)
- [Change Detection](#itdr-entra-id-identity-change-detection-tab)
- [Threats](#itdr-entra-id-identity-threats-tab)
- [Access Risk](#itdr-entra-id-identity-access-risk-tab)
- [Roles](#itdr-entra-id-identity-role-tab)
[]Provides a snapshot of Entra ID identity vulnerabilities. On the **Summary** page, you can do the following:
- View the name of the Entra ID identity (user or service principal name).
- View the following Entra ID identity details:
- **Name**: The Entra ID user or service principal name.
- **User Principal Name**: The [user principal name (UPN)](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/plan-connect-userprincipalname) attribute value for the identity.
- **Enabled**: The account activation status. A green check mark indicates enabled, and a red X indicates disabled.
- **Roles**: Click **View Roles** to view the details of the [Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) and [Azure RBAC built-in or custom roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles) that are assigned to the identity.
- **User Type**: The Entra ID user type (**Member** or **Guest**).
- **Department**: The administrative or organizational unit name for the identity.
- **MFA**: The multi-factor authentication (MFA) status for identity. You can view the following statuses:
- **Is Capable**: Indicates if the identity is capable of using MFA. A green check mark indicates enabled, and a red X indicates disabled.
- **Is Registered**: Indicates if the identity is registered for MFA. A green check mark indicates enabled, and a red X indicates disabled.
- **Methods Registered**: The authentication methods registered with the identity (e.g., Passkey (FIDO2), SMS, Voice, Password, etc.).
-
**Default Method**: The default MFA method configured by the admin for the identity.
If the MFA authentication methods are not configured, the **Methods Registered **and **Default Method **fields don't display any data.
- **App**: The name and ID of an application registered in the Entra ID tenant.
- **On-premises**: The details of an on-premises AD domain that is synced with the Azure Entra ID tenant. You can view the following details:
- **SAM Account Name**: The security accounts manager (SAM) name of the AD account.
- **Distinguished Name**: The distinguished name of the on-premises AD account.
- **Domain Name**: The domain name of the on-premises AD account.
- **Security Identifier**: The security identifier (SID) details of the on-premises AD account.
- **User Principle Name**: The user principal name (UPN) attribute value of the on-premises AD account.
- **Sync Enabled**: Indicates if the on-premises AD account is synced with Azure Entra ID. A green check mark indicates enabled, and a red X indicates disabled.
- View the unified posture risk score of the Entra ID tenant on a scale of 0 to 100. You can also view the total number of posture risks or misconfigurations the Entra ID identity is exposed to. For example, excessive global admins, insecure permissions on application, etc. Click **Review failed checks** to analyze the risk and quickly remediate the issue.
- View the total number of recent risky changes made to the Entra ID identity that have a bad impact on the posture. For example, changes such as a user is granted excessive privileges, users are able to sign in without MFA, a guest user has been assigned a privileged role, etc. Click **Review all changes** to investigate these recent risky changes and take appropriate steps to remediate issues.
-
View the following Okta user account details, if the identity exists in Okta.
To view the Okta user accounts details, ensure that [ITDR is integrated with Okta](/itdr/integrating-itdr-okta). If the identity doesn't exist in Okta, the Okta tile doesn't show any data.
- **Status**: The status of the identity.
- **Created On**: The date and time when the identity was created.
- **Activated On**: The date and time when the identity was activated.
- **Status Changed On**: The date and time when the status of the identity was changed.
- **Last Login**: The date and time when the identity last logged in.
- **Last Updated On**: The date and time when the identity was updated.
- **Password Changed On**: The date and time when the identity password was changed.
- **Name**: The name of the identity.
- **Login**: The login details of the identity.
- **Email**: The email ID of the identity.
- **City**: The city or locality of the identity.
- **Display Name**: The display name of the Okta user.
- **Title**: The title of the Okta user (e.g., **Vice President**, **Manager**, etc.).
- **Time Zone**: The time zone of the Okta user.
- **Division**: The division that the Okta user belongs to.
- **Country Code**: The country of the Okta user.
- **State**: The state or the region of the Okta user.
- **Department**: The department that the Okta user belongs to.
- **Manager**: The display name of the Okta user's manager.
- **Cost Center**: The name of the cost center assigned to the identity.
- **Groups**: The group that the Okta user belongs to.
- **Roles**: The roles that are assigned to the Okta user.
- **Factors**: The MFA that the user is enrolled in and the status of the authentication.
- Gain insight into threat incidents on ZIA, and policies blocked and application segment access violations on ZPA if your Entra ID identity is integrated with ZIA and ZPA services. The data is represented as a donut chart.
- Select any of these options from the **Actions** drop-down menu:
- [Contain with ZPA](#itdr-entra-id-zpa-containment)
- [Contain with ZIA](#itdr-entra-id-zia-containment)
- [Suspend](#itdr-entra-id-suspend)
- [Unsuspend](#itdr-entra-id-unsuspend)
- [Activate](#itdr-entra-id-activate)
- [Deactivate](#itdr-entra-id-deactivate)
- [Reset Password](#itdr-entra-id-reset)
- [Clear User Sessions](#itdr-entra-id-clear)
- [Reset Authenticators](#itdr-entra-id-authenticators)
[See image.](#itdr-aff-entra-id-identity-summary-image)
[]Take immediate action to contain an attack or threat via the ZIA service. You can forward the attack details to ZIA for automated containment. ZIA inspects the attack details and blocks them according to the defined policy.
[]Take immediate action to contain an attack or threat via the ZPA service. You can forward the attack details to ZPA for automated containment. ZPA inspects the attack details and blocks them according to the defined policy.
[]Suspend the Okta user account and disable user access.
[]Unsuspend the suspended Okta user account and enable user access.
[]Activate the deactivated Okta user account. An email is sent to your Okta email ID to activate the user account.
[]Deactivate the Okta user account and temporarily disable user access until activated again. This removes access to all the apps that were previously authenticated via Okta.
[]Reset the password of the Okta user account. An email is sent to your Okta email ID to reset the password.
[]Clear all active sessions of the user.
[]Reset the authenticators.
[]Provides visibility into the top vulnerability risks or issues in the Entra ID identity. This helps you to prioritize what issues to focus on. You can view the following additional details about each risk to further investigate and remediate it. You can click a risk type on the left-side pane to view the following information:
- Entra ID identity issue details:
- **Type of Risk**: The type of risk (e.g., **Best Practice Violations**,** Privilege Escalation**, **Hybrid Risk**, **Data Loss**, etc.).
- **Severity**: The severity level of the risk (**Critical**, **High**, **Medium**, or **Low**).
- **Remediation**: The remediation assessment (**Easy**, **Moderate**, or **Difficult**).
- **MITRE ATT&CK  Tactics**: The type of MITRE ATT&CK  tactic (e.g., **Privilege Escalation**, **Credential Access**, etc.).
- **What is the issue?**: The description of the vulnerability issue.
- **What is the impact?**: The consequences of the attack.
- **References**: Click the reference link to view Microsoft documentation or any other references to understand the issue context and remediation.
-
**Who is affected?**: A list of affected identities that are vulnerable to attack.
You can use the **Actions** menu to [export the affected identities as a CSV file](/itdr/using-tables#itdr-export-table-csv-section) and [copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table, and click **Remediation** to [automatically remediate Entra ID issues](/itdr/running-remediation-actions-microsoft-entra-id-issues).
[See image.](#itdr-aff-entra-id-identity-posture-issue-details-image)
- Remediation details:
-
If there is a single remediation for an issue, you can view:
- The remediation description and assessment (**Easy**, **Moderate**, or **Difficult**).
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation or any other reference document that provides remediation details.
[See image.](#itdr-entra-id-aff-identity-single-remediation)
-
If there are multiple remediations for an issue, Zscaler ITDR provides a flowchart that breaks down multiple steps into distinct workflows. The workflows in the flowchart are prioritized based on the most suitable remediation to the issue. The most appropriate remediation is listed first, followed by the less suitable ones. After you choose a workflow, you can click the link in an individual step or process to view:
- The remediation description and assessment (**Easy**, **Moderate**, or **Difficult**).
- **How to fix?**: Steps to manually remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: Links to view Microsoft documentation, Zscaler help articles, or any other references to understand the issue context and remediation steps.
Click **Export Remediation Chart** to export the flowchart as an SVG file.
Click the **Add object to safelist** link in a remediation step to [add Entra ID objects to the safelist](/itdr/adding-entra-id-object-safelist). When you click the link, you are redirected to the **Who is affected?** table. You can select the Entra ID users or service principals and click **Add Objects to Safelist**.
[See image.](#itdr-entra-id-aff-identity-remediation-flowchart)
[]Lists the recent changes in the Entra ID identity or recent activity logs in the Okta account.
- [Entra](#itdr-entra-id-change-detection-sub-tab)
- [Okta](#itdr-entra-id-change-detection-okta-sub-tab)
[]Lists the recent risky or bad changes detected in the Entra ID. It also provides additional issues and remediation details. For each change that is detected, you can view:
- Change details:
- **Change Date**: The date and time when a change is detected in the identity.
- **Issue**: The issues for which the change is detected (e.g., **Insecure permissions on application**, **Privileged guest accounts**, etc.).
- **Initiated By**: The details of identity who initiated this change.
- **Reason**: The reason for the change.
- **Impact**: Indicates the following change status. You can filter the column to view a specific change:
- **Good**: A good or safe change.
- **Bad**: A risky change. The system administrators can review the bad impacts, view the issue details, and remediate the issues.
- **Info**: A significant change to the Entra ID tenant that might have a good or bad impact based on the environment. The system administrators can review the impact and take necessary actions.
- **Type**: The type of identity (**User** or **Service Principal**). You can filter the changes by identity type.
- Issue and remediation details: Click the **View** icon to view the following details:
- **Change Date**: The date and time when a change is detected in the identity.
- **Issue Name**: The issue name.
- **Change**: The description of risky change.
- **Type of Risk**: The type of risk (e.g., **Delegation Abuse**, **Account Management**, **Credential Exposure**, etc.).
- **What is the issue?**: The description of the issue.
- **What is the impact?**: The consequences of the attack.
- **Change Data**: The details of the change that was detected in the identity, such as the operation name, the caller IP address, data source information, and role details.
- **Remediation**: The remediation description and assessment (**Easy**, **Moderate**, or **Difficult**). For every remediation step, you can view:
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation. You can click the link to view guidance and best practices for remediation.
- **Raw Event**: The raw event data received from the Entra ID tenant’s log provider. The data includes information such as who initiated the change, what the change is, what the old value was, and what the new value is. The raw event data is represented in the JSON format that is easy to understand. The code is well-indented and has a key-value pair. You can download the JSON file for further investigation.
[See image.](#itdr-entra-id-change-detection-tab-image)
[]Lists the chronological records of Entra ID identity activities and logs in the Okta account. For each activity, you can view:
- Event Details:
- **Date**: The date and time when the event was created.
- **Event**: The logs of the event.
- **Severity**: The severity (**Debug**, **Info**, **Error**, and **Warn**) of the event.
- **Result**: The result (**Allow**, **Challenge**, **Deny**, **Failure**, **Skipped**, **Success**, and **Unknown**) of an action in the event.
- **Message**: The description of the event.
- Actions: Click the **View** icon to view additional event details:
- **Date**: The date and time when the event was created.
- **Event**: The instances or type of the event.
- **Severity**: The severity (**Debug**, **Info**, **Error**, and **Warn**) of the event.
- **Result**: The result (**Allow**, **Challenge**, **Deny**, **Failure**, **Skipped**, **Success**, and **Unknown**) of an action in the event.
- **Message**: The description of the event.
- **User Agent**: The software details (**OS**, **Browser**) through which the identity is performing the action.
- **Device**: The type of the device the user is operating from (e.g., **Computer**).
- **IP Address**: The IP address of the device where the event was performed.
- **Geographical Context**: The geographical location where the event was performed.
[See image.](#itdr-entra-id-change-detection-okta-image)
[]Analyzes the details of attacks in natural language along with information linked to the MITRE ATT&CK  framework. ThreatParse is a technology built into ITDR that conducts natural language reconstruction of attacks by summarizing and translating log information into plain English. It also links this information to the MITRE ATT&CK  framework and includes the risk scores assigned to attackers. The Threats page provides information about identity system logs across the Okta customer base that are identified as potentially suspicious. You can click an issue on the left-side pane to view the following information:
- **Issue**: The name of the issue.
- **Severity**: The severity level (**Critical**, **High**, **Medium**, and **Low**) of the issue.
- **MITRE ATT&CK  ID**: The MITRE ATT&CK  technique ID (e.g., **T1558.003**, **T1078.002**, etc.). Click the ID to view more details about the attack technique.
- **MITRE ATT&CK  TACTICS**: The type of MITRE ATT&CK  tactic (e.g., **Initial Access**, **Privilege Escalation**, etc.).
- **What is the issue?**: The detailed description of the issue.
- **Okta Logs**: The Okta system logs in a tabular format that list the date, time, and location of the event creation, browser, OS, and so on.
[See image.](#itdr-entra-id-okta-threats-tab-image)
[]Provides insight into traffic violations or bad activities on ZIA and ZPA services for the Entra ID identity. Presents real-time visibility into threat incidents and access policy violations for configured application segments. This helps you to understand the security efficacy of layered defense across Malware Protection, Advanced Threat Protection (ATP), Sandbox, Firewall, and Isolation for your identities.
ITDR integration with ZIA and ZPA services works with SCIM user provisioning and authentication method only. Zscaler provides an easy and consistent mechanism for users to use SCIM to manage the life cycle of user and group accounts in the Zscaler cloud.
On the **Access Risk** page, you can view the following information on each tab:
- [ZIA Insights](#itdr-entra-id-identity-access-risk-zia-sub-tab)
- [ZPA Insights](#itdr-entra-id-identity-access-risk-zpa-sub-tab)
[]The ZIA Insights page enables you to view and analyze the [threat or security incidents](/zia/about-cybersecurity-insights) for the Entra ID identity if [ITDR is integrated with ZIA](/itdr/containment-configuration-guide-zscaler-internet-access-zia).
On the **ZIA Insights** page, you can view the following information:
- **SCIM Username**: The SCIM username of the Entra ID identity as identified by the IdP. This username is used for authentication.
- **SCIM Group**: The SCIM group attributes as configured in your IdP.
- **IdP Name**: The identity provider’s name.
- **Last Location**: The last location from where the identity accessed ZIA or any other website.
- **Malicious traffic trend**: A graph that represents malicious traffic activity or threat incidents recorded for the selected time frame.
- **Threat profile**: A donut chart grouped by threat incident categories (Malware, Spyware, Adware, Malicious Content, etc.) your Entra ID tenant is exposed to.
- **Diagnostics**: A list of log information for threat incidents represented in a tabular format. You can search for specific entries wherever you see a search icon on a column field name:
- **Connection**: The date and time when the threat incident occurred.
- **Policy Action**: Explanation of the policy action. To learn more, see [ZIA Policy Reasons](/zia/policy-reasons).
- **URL**: The URL or IP address of the website that is included in the URL category.
- **URL Category**: The URL category of the threat incident. ZIA organizes URLs into a hierarchy of categories for granular filtering and policy creation. To learn more, see [ZIA URL Categories](/zia/about-url-categories).
- **Threat Name**: The threat name.
- **User Location**: The internet gateway location. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location.
[See image.](#itdr-aff-entra-id-identity-access-risk-zia-image)
[]The ZPA Insights page enables you to view and analyze access policy violations for [configured application segments](/zpa/about-applications) for the Entra ID identity if [ITDR is integrated with ZPA](/itdr/containment-configuration-guide-zscaler-private-access-zpa).
On the **ZPA Insights** page, you can view the following information:
- **SCIM Username**: The name of the user as identified by the IdP and used for authentication.
- **SCIM Group**: The SCIM group attributes as configured in your IdP.
- **IdP Name**: The identity provider’s name.
- **Last Location**: The last location from which the user accessed ZPA or any other application segment.
- **Policy block trend**: The trend chart that displays the total number of transactions where the access policy blocked users from accessing the application segments over a selected time frame. To learn more, see [About ZPA Policies](/zpa/about-policies).
- **Top 10 app access violations**: The top 10 application segments access violations over a selected time frame. To learn more, see [About ZPA Applications](/zpa/about-applications).
- **Diagnostics**: Lists the log information about evaluated access policy rules for the configured application segments in a table. You can search for specific entries wherever you see a search icon on a column field name:
- **Connection**: The date and time when the application access violation occurred.
- **Policy**: The name of the access policy rule configured to block specific users from accessing application segments.
- **Application**: The name of the application segment that is accessed.
- **Port**: The port number of the application segment.
- **Protocol**: The protocol name used for application segment discovery.
- **User Location**: The location the Entra ID identity is connecting from.
[See image.](#itdr-entra-id-identity-access-risk-zpa-image)
[]Provides details of the [Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) that are assigned to the Entra ID identity and [Azure built-in or custom roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles) that are configured for the identity.
On the **Roles** page, you can view the following information on each tab:
- [Azure RBAC](#itdr-entra-id-identity-azure-rbac-sub-tab)
- [Entra](#itdr-entra-id-identity-role-entra-sub-tab)
[]On the** Entra** page, you can view the details of the roles assigned to the identity and the scope of the role, including the following information:
- **Name**: The Entra ID role name (**Global Administrator**, **Application Developer**[, etc.)]
- **Scope**: The role scope. The scope limits the identity to access a particular resource. For example, the role could be limited to access a particular application, an administrative unit, or the entire tenant.
- **Scope Type**: The scope type (**Tenant**, **Administrative unit, Microsoft Entra resource**, etc.).
- **Assignment Type**: The assignment type of the Entra ID role (**Active** or **Eligible**). The **Active** assignment type provides users with immediate and continuous access to a role’s permissions without requiring any further actions. The **Eligible** assignment type allows users to request temporary access to a role, which must be activated through a verification process.
[See image.](#itdr-entra-id-identity-roles-entra-image)
[]On the **Azure RBAC** page, you can view information about the roles assigned to the Entra ID identity and Azure resources the role, including the following information:
- **Name**: The name of the role (e.g., **Reader**, **Contributor**, **Storage Blob Data Reader**, etc.)
- **Resource**: The name of the resource to which the role is assigned to. The role could be assigned to access a virtual machine, storage accounts, etc.
- **Resource Type**: The resource type (e.g. **Virtual Machine**, **Database**, etc.)
[See image.](#itdr-entra-id-identity-azure-rbac-image)
[]![View the affected Entra ID identity Summary tab](/downloads/itdr/dashboard/entra-id-posture/entra-id-posture-details/viewing-affected-entra-id-identity-details/ITDR-Entra-Summary.png)
[]![View Entra ID identity posture details](/downloads/itdr/dashboard/entra-id/viewing-affected-entra-id-identity-details/itdr-entra-id-affected-identity-posture-issue-details-3.png)
[]![View Entra ID remediation details](/downloads/itdr/dashboard/entra-id/viewing-affected-entra-id-identity-details/itdr-entra-id-affected-identity-posture-single-remediation-details-1.png)
[]![View Entra ID issue remediation flowchart](/downloads/itdr/dashboard/entra-id/viewing-affected-entra-id-identity-details/itdr-entra-id-affected-identity-posture-remediation-flowchart-3.png)
[]![View the Entra ID identity change detection details](/downloads/itdr/dashboard/entra-id/viewing-affected-entra-id-identity-details/itdr-entra-id-affected-identity-change-detection-tab-1.png)
[]![View Okta change details for the Entra ID identity](/downloads/itdr/dashboard/entra-id/viewing-affected-entra-id-identity-details/itdr-entra-id-affected-okta-change-detection-tab.png)
[]![View Entra ID identity Okta tab](/downloads/itdr/dashboard/entra-id/viewing-affected-entra-id-identity-details/itdr-entra-id-affected-identity-okta-threats-tab.png)
[]![View Entra ID identity Access Risk ZIA tab](/downloads/itdr/dashboard/entra-id/viewing-affected-entra-id-identity-details/itdr-entra-id-affected-identity-access-risk-zpa-tab-3.png)
[]![View Entra ID identity Access Risk ZPA tab](/downloads/itdr/dashboard/entra-id/viewing-affected-entra-id-identity-details/itdr-entra-id-affected-identity-access-risk-zpa-tab-1.png)
[]![Image]()
![View Entra ID role details](/downloads/itdr/dashboard/entra-id/viewing-affected-entra-id-identity-details/itdr-entra-id-affected-identity-roles-entra-tab-3.png)
[]![View the Azure RBAC details for the affected Entra ID identity](/downloads/itdr/dashboard/entra-id/viewing-affected-entra-id-identity-details/itdr-entra-id-affected-identity-roles-azure-rbac-tab-1.png)