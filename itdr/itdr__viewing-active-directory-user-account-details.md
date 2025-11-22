# Viewing Active Directory User Account Details
Source: https://help.zscaler.com/itdr/viewing-active-directory-user-account-details
PDF: https://help.zscaler.com/pdf/com/en/1531628.pdf

You can click an Active Directory (AD) user account on the [Active Directory Posture](/itdr/about-active-directory-posture-dashboard) dashboard or [Endpoint Credential Identities](/itdr/viewing-identities-endpoint-exposures) page to view additional details about the vulnerable AD user account.
The AD user details page displays information, such as failed posture checks, associated Okta user account details, recent suspicious changes made to the user account, detected potential identity attacks or threats, and Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) access snapshots. You can further investigate the issues and swiftly remediate the compromised AD user account to disrupt the attacker's operations.
On the AD user details page, you can view the following information on each tab:
- [Summary](#itdr-affected-ad-user-summary-tab)
- [Posture](#itdr-affected-ad-user-posture-tab)
- [Credential Exposure](#itdr-affected-ad-user-credential-exposure-tab)
- [Change Detection](#itdr-aff-ad-user-change-detection-tab)
- [Threats](#itdr-aff-ad-user-threats-tab)
- [Access Risk](#itdr-aff-ad-user-access-risk-tab)
- [Session Tracking](#itdr-aff-ad-user-session-tracking)
[]Provides a snapshot of identity vulnerabilities in the AD user account. On the Summary page, you can do the following:
- View the name of the AD user account.
- View the following AD user account details:
- **Created On**: The date when the user account was created.
- **Identity Classification**: The AD user account type, such as privileged** **or service. A privileged AD user account has powerful permissions that allow the user to perform nearly any action in the AD. A service AD user account is created to run a particular service or application on the Microsoft Windows operating system and has the minimum permissions that are required to run the services. To learn more, refer to the Microsoft documentation for [Privileged](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-b--privileged-accounts-and-groups-in-active-directory) and [Service](https://learn.microsoft.com/en-us/entra/architecture/service-accounts-on-premises) accounts.
- **Last Password Change**: The date when the password was last changed.
- **Critical Group Memberships**: The group membership of the critical AD group. ADs are primarily categorized into security and distribution groups. These groups have four different scopes, including universal, global, domain local, and local. Scope helps determine the areas in the AD domain where a group’s permissions can be enforced successfully. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups).
- **Password Reuse Detected**: The total number of other AD user accounts that share the same password as the affected AD user. This count excludes the affected AD user.
- **Last Seen Logon Workstation**: The name of the workstation where the user last logged in.
- **Last Logon Time**: The last time the user logged in to the workstation.
-
View the following Okta user account details, if the user exists in Okta.
To view the Okta user accounts details, ensure that [ITDR is integrated with Okta](/itdr/integrating-itdr-okta). If the user doesn't exist in Okta, the Okta tile shows No Data.
- **Status**: The status of the account.
- **Created On**: The date and time when the account was created.
- **Activated On**: The date and time when the account was activated.
- **Status Changed On**: The date and time when the status of the account was changed.
- **Last Login**: The date and time when the account last logged in.
- **Last Updated On**: The date and time when the account was updated.
- **Password Changed On**: The date and time when the account password was changed.
- **Name**: The name of the account.
- **Login**: The login details of the account.
- **Email**: The email ID of the account.
- **Groups**: The group that the Okta user belongs to.
- **Roles**: The roles that are assigned to the Okta user.
- **Factors**: The multi-factor authentication (MFA) that the user is enrolled in and the status of the authentication.
- **City**: The city or locality of the account.
- **Display Name**: The display name of the Okta user.
- **Title**: The title of the Okta user (e.g., **Vice President**, **Manager**, etc.).
- **Time zone**: The time zone of the Okta user.
- **Employee Number**: A unique identifier of the account assigned by the organization.
- **Division**: The division that the Okta user belongs to.
- **Country Code**: The country of the Okta user.
- **State**: The state or the region of the Okta user.
- **Department**: The department that the Okta user belongs to.
- **Manager**: The display name of the Okta user's manager.
- **Cost Center**: The name of the cost center assigned to the account.
- **User Type**: The type of the user that determines the schema for the Okta user's profile.
- View the total number of recent threats or attacks detected on the AD user account. For example, DCSync, DCShadow, Zerologon, Session Enumeration, Kerberoast, LDAP Reconnaissance, etc. Click **Investigate attacks** to view easy-to-understand attack details. You can analyze the details along with information linked to the MITRE ATT&CK  framework.
- View the total number of posture risks or misconfigurations the AD user account is exposed to. For example, privilege account delegation, stale passwords, etc. Click **Review failed checks** to analyze the risk and quickly remediate the issue.
- View the total number of recent risky changes made to the AD user account that have a bad impact on the identity posture. For example, changes such as AD account permissions are suspiciously modified, an AD account is suddenly disabled, etc. Click **Review all changes** to investigate these recent risky changes and take appropriate steps to remediate issues.
- Gain insight into threat incidents on ZIA, and policies blocked and application segments access violations on ZPA if your AD user account is integrated with ZIA and ZPA services. The data is represented as a donut chart.
-
Select any of these options from the **Actions** drop-down menu:
- [Contain with ZPA](#zpa-containment)
- [Contain with ZIA](#zia-containment)
- [Suspend](#suspend)
- [Unsuspend](#unsuspend)
- [Activate](#activate)
- [Deactivate](#deactivate)
- [Reset Password](#reset)
- [Clear User Sessions](#clear)
- [Reset Authenticators](#authenticators)
You can remediate AD user account issues from the **Actions **menu.
[See image.](#itdr-aff-ad-user-summary-image)
[]Take immediate action to contain an attack or threat via ZIA services. You can forward the attack details to ZIA for automated containment. ZIA inspects the attack details and blocks them according to the defined policy.
[]Take immediate action to contain an attack or threat via ZPA services. You can forward the attack details to ZPA for automated containment. ZPA inspects the attack details and blocks them according to the defined policy.
[]Suspend the Okta user account and disable user access.
[]Unsuspend the suspended Okta user account and enable user access.
[]Activate the deactivated Okta user account. An email is sent to your Okta email ID to activate the user account.
[]Deactivate the Okta user account and temporarily disable user access until activated again. This removes access to all the apps that were previously authenticated via Okta.
[]Reset password of the Okta user account. An email is sent to your Okta email ID to reset your password.
[]Clear all active sessions of the user.
[]Reset the authenticators.
[]Provides visibility into the top vulnerbility risks or issues in the AD user account. This helps you to prioritize what issues to focus on. You can view the following additional details about each risk to further investigate and remediate it. You can click a risk on the left-side pane to view the following information:
- Issue details:
- **Type of Risk**: The type of vulnerability risk (e.g., **Kerberos Abuse**, **Credential Exposure**, **Weak Permissions**, etc.).
- **Severity**: The severity level of the vulnerability risk (e.g., **Critical**, **High**, **Moderate**, and **Low**).
- **Remediation**: The remediation assessment (e.g., **High**, **Moderate**, and **Easy**).
- **MITRE ATT&CK  ID**: The MITRE ATT&CK  technique ID (e.g., **T1558.003**, **T1078.002**, etc.). Click the ID to view more details about the attack tactic.
- **MITRE ATT&CK  Tactics**: The type of MITRE ATT&CK  tactic (e.g., **Privilege Escalation**, **Credential Access**, etc.).
- **What is the issue?**: The description of the vulnerability issue with videos that demonstrate how an adversary performs the attack.
- **What is the impact?**: The consequences of the attack.
- **References**: A link to National Cybersecurity Agency of France (ANSSI) checklist mapping. ANSSI is a French government organization that secures government information systems. For an issue, you can click the reference link to view ANSSI recommendations and best practices to understand the issue context and remediation.
-
**Who is affected?**: The details of the user accounts that are vulnerable to attack.
You can use the **Actions** menu to [export the affected user account and computer details as a CSV file](/itdr/using-tables#itdr-export-table-csv-section) and [copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table, click **Remediations** to [remediate AD issues](/itdr/running-remediation-actions-ad-identities), and click **Add Objects to Safelist** to [add the AD object to the safelist](/itdr/adding-active-directory-object-safelist).
[See image.](#itdr-aff-ad-user-posture-issue-details)
- Remediation details:
-
If there is a single remediation for an issue, you can view:
- Remediation description and assessment (**Easy**, **Moderate**, or **Difficult**).
- Instructions or videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Remediation Script**: A script that you can [download](/itdr/downloading-and-running-remediation-script) and run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation that provides the issue context and remediation details.
[See image.](#itdr-affected-user-posture-remediation-details)
-
If there are multiple remediations for an issue, Zscaler ITDR provides a flowchart that breaks down multiple steps into distinct workflows. The workflows in the flowchart are prioritized based on the most suitable remediation to the issue. The most appropriate remediation is listed first, followed by the less suitable ones. After you choose a workflow, you can click the link in an individual step or process to view:
- Remediation description and assessment (**Easy**, **Moderate**, or **Difficult**).
- Instructions or videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Remediation Script**: A script that you can [download](/itdr/downloading-and-running-remediation-script) and run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation that provides the issue context and remediation details.
Click **Export Remediation Chart** to export the flowchart as an SVG file.
Click the** Add object to safelist** link in a remediation step to [add AD objects to the safelist](/itdr/adding-active-directory-object-safelist). When you click the link, you are redirected to the **Who is affected?** table. You can select the AD objects and click **Add Objects to Safelist**.
[See image.](#itdr-affected-ad-user-remediation-flowchart)
[]Lists all the exposed endpoint credentials for the AD user account. You can click an issue on the left-side pane to view additional details about each exposed credential to further investigate and remediate it.
- **Issue**: The issue details.
- **Type of Risk**: The type of vulnerability risk (e.g., **Insecure UAC**, **Admin Auto Logon Credentials**, etc.).
- **Severity**: The severity level of the vulnerability risk (e.g., **Critical**, **High**, **Moderate**, and **Low**).
- **MITRE ATT&CK  ID**: The MITRE ATT&CK  technique ID (e.g., **T1558.003**, **T1078.002**, etc.). Click the ID to view more details about the attack tactic.
- **MITRE ATT&CK  Tactics**: The type of MITRE ATT&CK  tactic (e.g., **Persistence**, **Lateral Movement**, etc.).
- **What is the issue?**: The description of the issue on how an adversary performs the attack.
- **What is the impact?**: The consequences of the attack.
- **Remediation**: The remediation description.
- **References**: A link to the Microsoft documentation. You can click the link to view guidance and best practices for remediation.
-
**Who is affected?**: The details of the endpoints that have exposed credentials.
You can clean up credentials only if the feature is supported for this exposure. To learn more, see [Cleaning Up Exposed Endpoint Credentials](/itdr/cleaning-exposed-endpoint-credentials). You can use the **Actions** menu to [copy specific columns from the table](/itdr/using-tables#itdr-copy-columns-table-section) and download the [table as a CSV or JSON file](/itdr/using-tables#itdr-export-table-csv-section).
[See image.](#itdr-ad-user-acc-details-exposed-credentials-image)
[]Lists the recent changes in the AD account or recent activity logs in the Okta account.
- [Active Directory](#change-detection-ad)
- [Okta](#change-detection-okta)
[]Lists the recent risky or bad changes detected in the AD user account. It also provides additional issues and remediation details. For each change that is detected, you can view the following details:
- **Change Date**: The date and time when the change is detected in the user account.
- **Issue**: The issues for which the change is detected (e.g., **Privileged account delegation**, **Unconstrained Delegation**, etc.).
- **Change**: The description of the change.
- **Impact**: Indicates that the change has a bad impact. The system administrators can review the bad impacts, view the issue details, and remediate the issues.
-
**Classification**: The AD user account type, such as privileged** **or service. A privileged AD user account has powerful permissions that allow the user to perform nearly any action in the AD. A service AD user account is created to run a particular service or application on the Microsoft Windows operating system and has the minimum permissions that are required to run the services. To learn more, refer to the Microsoft documentation for [Privileged](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-b--privileged-accounts-and-groups-in-active-directory) and [Service](https://learn.microsoft.com/en-us/entra/architecture/service-accounts-on-premises) accounts.
[See image.](#itdr-aff-ad-user-cd-ad-details-image)
You can click the **View** icon under **Actions** to view the following details:
- **Change Date**: The date and time when a change is detected in the user account.
- **Issue Name**: The issue name.
- **Change**: The description of risky change.
- **Who is affected?**: The details of the user account in which the change was detected.
- **Type of Risk**: The type of risk (e.g., **Delegation Abuse**, **Account Management**, **Credential Exposure**, etc.).
- **What is the issue?**: The description of the issue with videos that demonstrate how an adversary performs the attack.
- **What is the impact?**: The consequences of the attack.
- **MITRE ATT&CK  ID**: The MITRE ATT&CK  technique ID (e.g., **T1558.003**, **T1078.002**, etc.). Click the ID to view more details about the attack tactic.
- **MITRE ATT&CK  Tactics**: The type of MITRE ATT&CK  tactic (e.g., **Privilege Escalation**, **Credential Access**, etc.).
- **Investigate**: Issue investigation details.
-
**Remediation**: The remediation description and assessment (**Easy**, **Moderate**, or **Difficult**). For every remediation step, you can view:
- Instructions or Videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation. You can click the link to view guidance and best practices for remediation.
[See image.](#itdr-aff-ad-user-cd-ad-view-icon-details-image)
[]Lists the chronological records of user activities and logs in the Okta user account. For each activity, you can view the following details:
- **Date**: The date and time when the event was created.
- **Event**: The logs of the event.
- **Severity**: The severity (**Debug**, **Info**, **Error**, and **Warn**) of the event.
- **Result**: The result (**Allow**, **Challenge**, **Deny**, **Failure**, **Skipped**, **Success**, and **Unknown**) of an action in the event.
-
**Message**: The description of the event.
Click **Export CSV** to export these Okta activity log details as a CSV file.
[See image.](#itdr-add-ad-user-cd-okta-image)
You can click the **View** icon under **Actions** to view the following details:
- **Date**: The date and time when the event was created.
- **Event**: The instance or type of the event.
- **Severity**: The severity (**Debug**, **Info**, **Error**, and **Warn**) of the event.
- **Result**: The result (**Allow**, **Challenge**, **Deny**, **Failure**, **Skipped**, **Success**, and **Unknown**) of an action in the event.
- **Message**: The description of the event.
- **User Agent**: The software details (**OS**, **Browser**) through which the user is performing the action.
- **Device**: The type of device the user is operating from (e.g., **Computer**, **Mobile**, etc.).
- **IP Address**: The IP address of the device where the event occurred.
-
**Geographical Context**: The geographical location where the event occurred.
[See image.](#itdr-aff-ad-user-cd-okta-view-icon-image)
[]Analyzes the details of attacks in natural language along with information linked to the MITRE ATT&CK  framework. ThreatParse is a technology built into ITDR that conducts natural language reconstruction of attacks by summarizing and translating log information into plain English. It also links this information to the MITRE ATT&CK  framework and includes the risk scores assigned to attackers.
- [ITDR](#threat-itdr)
- [Okta](#threat-okta)
[]The information on the ITDR tab helps you to prioritize and focus on high-risk events using risk scores to stop the lateral movement of attackers. You can click a threat with the threat score on the left-side pane to view the following information:
- The attack description with the risk score
- Attack examples
- Attack mitigations
- MITRE ATT&CK  ID
- MITRE ATT&CK  tactic
- Event occurrence summary
[See image.](#itdr-aff-ad-user-thretparse-image)
[]The Okta tab provides information about identity system logs across the Okta customer base that are identified as potentially suspicious. You can click on an issue on the left-side pane to view the following information:
- **Issue**: The name of the issue.
- **Severity**: The severity level (**Critical**, **High**, **Medium**, and **Low**) of the issue.
- **MITRE ATT&CK  ID**: The MITRE ATT&CK  technique ID (e.g., **T1558.003**, **T1078.002**, etc.). Click the ID to view more details about the attack technique.
- **MITRE ATT&CK  Tactics**: The type of MITRE ATT&CK  tactic (e.g., **Privilege Escalation**, **Credential Access**, etc.).
- **What is the issue?**: The detailed description of the issue.
- **Okta Logs**: The Okta system logs for threat detection in a tabular format that lists the date and time of the event creation, users, browser, OS, and so on. These logs are only retained for 14 days, after which they are permanently deleted. You cannot modify the retention period.
[See image.](#itdr-aff-user-threats-okta-tab-image)
[]Provides insight into traffic violations or bad activities on ZIA and ZPA services for the AD user account. Presents real-time visibility into threat incidents and access policy violations for configured application segments. This helps you to understand the security efficacy of layered defense across Malware Protection, Advanced Threat Protection (ATP), Sandbox, Firewall, and Isolation for your AD user account.
ITDR integration with ZIA and ZPA services works with SCIM user provisioning and authentication method only. Zscaler provides an easy and consistent mechanism for users to use SCIM to manage the life cycle of user and group accounts in the Zscaler cloud.
On the Access Risk page, you can view the following information on each tab:
- [ZIA Insights](#itdr-aff-ad-user-access-risk-zia-tab)
- [ZPA Insights](#itdr-aff-ad-user-access-risk-zpa-tab)
[]The ZIA Insights page enables you to view and analyze the [threat or security incidents](/zia/about-cybersecurity-insights) for the AD user account if [ITDR is integrated with ZIA](/itdr/containment-configuration-guide-zscaler-internet-access-zia).
On the ZIA Insights page, you can view the following information:
- **Username**: The SCIM username of the AD user as identified by the IdP. This username is used for authentication.
- **SCIM Group**: The SCIM group attributes as configured in your IdP.
- **IdP Name**: The identity provider’s name.
- **Last Location**: The last location from where the AD user accessed ZIA or any other website.
- **Malicious traffic trend**: A graph that represents malicious traffic activity or threat incidents recorded for the selected time frame.
- **Threat profile**: A donut chart that is grouped by threat incident categories (Malware, Spyware, Adware, Malicious Content, etc.) your AD is exposed to.
-
**Diagnostics**: A list of log information for threat incidents represented in a tabular format. You can filter specific information using the search icon on a column field name:
- **Connection**: The date and time when the threat incident occurred.
- **Policy Action**: Explanation of the policy action. To learn more, see [ZIA Policy Reasons](/zia/policy-reasons).
- **URL Category**: The URL category of the threat incident. ZIA organizes URLs into a hierarchy of categories for granular filtering and policy creation. To learn more, see [ZIA URL Categories](/zia/about-url-categories).
- **Threat Name**: The threat name.
- **User Location**: The internet gateway location. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location.
Click **Export CSV** to export the ZIA diagnostic data as a CSV file. If you have filtered the data in the table, the same information is downloaded as a CSV file.
[See image.](#itdr-aff-ad-user-access-risk-zia-image)
[]The ZPA Insights page enables you to view and analyze access policy violations for [configured application segments](/zpa/about-applications) for the AD user account if [ITDR is integrated with ZPA](/itdr/containment-configuration-guide-zscaler-private-access-zpa).
On the ZPA Insights page, you can view the following information:
- **SCIM Username**: The name of the user as identified by the IdP and used for authentication.
- **SCIM Group**: The SCIM group attributes as configured in your IdP.
- **IdP Name**: The identity provider’s name.
- **Last Location**: The last location from which the user accessed ZPA or any other application segment.
- **Policy block trend**: The trend chart that displays the total number of transactions where the access policy blocked users from accessing the application segments over a selected time frame. To learn more, see [About ZPA Policies](/zpa/about-policies).
- **Top 10 app access violations**: The top 10 application segments access violations over a selected time frame. To learn more, see [About ZPA Applications](/zpa/about-applications).
-
**Diagnostics**: Lists the log information about evaluated access policy rules for the configured application segments in a table. You can search for specific entries wherever you see a search icon on a column field name:
- **Connection**: The date and time when the application access violation occurred.
- **Policy**: The name of the access policy rule configured to block specific users from accessing application segments.
- **Application**: The name of the application segment that is accessed.
- **Port**: The port number of the application segment.
- **Protocol**: The protocol name used for application segment discovery.
- **User Location**: The location the AD user is connecting from.
Click **Export CSV** to export the ZPA diagnostic data as a CSV file. If you have filtered the data in the table, the same information is downloaded as a CSV file.
[See image.](#itdr-aff-ad-user-access-risk-zpa-image)
[]You can [enable session tracking in the server agent policy](/itdr/configuring-server-agent-policy) to monitor logon activities for all AD administrators and privileged accounts. This helps you to identify any anomalous user activity. For example, you can detect suspicious behavior, such as a privileged account user logging in to a less secure workstation outside normal working hours.
On the Session Tracking page, you can view the following information:
- **Login Success**: Indicates if the login was successful (**True** or **False**).
- **Client Workstation**: The name of the workstation where the user last logged in.
- **Client IP**: The IP address of the client workstation.
- **Event ID**: The unique ID for the event.
- **Failure Reason**: If the login status is **False**, you can see the reason for failure.
- **Timestamp**: The timestamp when the user logged into the workstation.
- **Actions**: Click the **View** icon to view additional session details, such as client workstation details, login timestamp, preauthentication type, etc.
[See image.](#itdr-affc-user-session-track-tab)
[]![View the posture summary of affected AD user](/downloads/itdr/dashboard/active-directory-posture/active-directory-posture-details/viewing-active-directory-user-account-details/ITDR-AD-Summary.png)
[]![View affecter AD user posture issue details](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-computer-details/itdr-affected-ad-user-posture-issue-details-6.png)
[]![View remediation details](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-user-account-details/itdr-affected-ad-user-posture-single-remediation-2.png)
[]![View AD remediation flowchart details](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-user-account-details/itdr-affected-ad-user-posture-remediation-flowchart-3.png)
[]![View exposed credentials for the affected AD object](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-user-account-details/itdr-ad-user-details-credential-exposure-tab-2.png)
[]![View change detection details for the AD user account](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-user-account-details/itdr-ad-user-details-credential-cd-ad-tab-3.png)
[]![View AD change detection issue and remediation details](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-user-account-details/itdr-ad-user-details-credential-cd-ad-view-icon.png)
[]![View Okta active change logs for the affected AD user](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-user-account-details/itdr-ad-user-details-credential-cd-okta-tab-4.png)
[]![View Okta event details](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-user-account-details/itdr-ad-user-details-credential-cd-okta-view-icon-2.png)
[]![View ThreatParse details for the affected AD user](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-user-account-details/itdr-affected-ad-user-threats-itdr-tab.png)
[]![View Okta threat detection details](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-user-account-details/itdr-affected-ad-user-threats-okta.png)
[]![View ZIA insights for the affected AD identity](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-user-account-details/zscaler-itdr-affected-ad-user-access-risk-zia-tab-2.png)
[]![View ZPA insights for the affected AD identity](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-user-account-details/zscaler-itdr-affected-ad-user-access-risk-zia-tab-3.png)
[]![View session details for the affected user](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-user-account-details/itdr-ad-posture-affected-user-session-tracking-image.png)