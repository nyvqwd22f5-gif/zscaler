# Viewing Identity Details
Source: https://help.zscaler.com/itdr/viewing-identity-details
PDF: https://help.zscaler.com/pdf/com/en/1531883.pdf

You can click an identity on the [Identity Search](/itdr/about-identity-search) page to view unified issue details for the identity across identity platforms (Active Directory (AD), Entra ID, and Okta).
For the specific identity, the page displays information such as posture issues, recent suspicious changes made to the identity, exposed endpoint credentials (for AD identities), associated Okta user account details, detected potential identity attacks or threats, Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) access risk assessments, etc. You can further investigate and swiftly remediate these issues to disrupt attacks.
For any detected attacks associated with the identity, you can take immediate action to contain the threats. You can also view the metadata for the AD, Entra ID, and Okta platforms.
To view the identity details:
- Go to **ITDR** > **Dashboard** > **Identity Search**.
-
On the [Identity Search](/itdr/about-identity-search) page, search for and click the identity.
[See image.](#itdr-id-details-click-id-image)
The identity details page appears with the following tabs:
[See image.](#itdr-id-details-all-tabs)
- [Overview](#itdr-id-details-overview-tab-section)
- [Posture Issues](#itdr-id-details-posture-issues-tab-section)
- [Recent Changes](#itdr-id-details-recent-changes-tab-section)
- [Threats Detected](#itdr-id-details-threats-tab-section)
- [Credentials](#itdr-id-details-credex-tab-section)
- [Access Risks](#itdr-id-details-access-risk-tab-section)
[]Provides a summary of issue details for the specific identity across all available identity platforms. On the **Overview** page, you can view:
- **Posture Issues**: The total number of posture issues categorized by severity levels (**Critical**, **High**, **Medium**, or **Low**).
- **Recent Changes**: The total number of recent active changes detected in the last 7 days.
- **Threats Detected**: The total number of threats or attacks detected, categorized by severity levels (**Critical**, **High**, **Medium**, or **Low**).
- **Credential Findings**: The total number of exposed endpoint credential issues, categorized by severity levels (**Critical**, **High**, **Medium**, or **Low**).
- **Access Risk**: The total number of potentially risky traffic violations or bad activities on ZIA and ZPA services.
- **AD Security Groups**: The details of the AD privileged group if the identity is a member.
- **Entra ID Security Groups**: The details of the Entra ID privileged group if the identity is a member.
- **MFA Status**: The multi-factor authentication (MFA) status details of the identity.
[See image.](#itdr-id-details-overview-tab-image)
[]Provides visibility into posture issues for the identity categorized by identity platforms. You can view the following details for each identity platform to further investigate and remediate issues:
- The total number of issues categorized by identity platform.
- The last scan timestamp for the AD domain, Entra ID tenant, etc.
- **Issue Name**: The name of the issue (**Privileged account delegation**, **Admins without phishing-resistant MFA**, etc.).
- **Description**: The issue description.
- **Severity**: The severity level of the issue (**Critical**, **High**, **Medium**, or **Low**).
- **Remediation**: Click **View Steps** to view remediation details.
- [Single remediation](#itdr-id-details-posture-issues-tab-one-rem-section)
- [Multiple remediations](#itdr-id-details-posture-issues-tab-many-rem-section)
[See image.](#itdr-id-details-posture-issues-tab-image)
[]If there is a single remediation for an issue, you can view:
- The remediation description and assessment (**Easy**, **Moderate**, or **Difficult**).
- Instructions or videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation that provides the issue context and remediation details.
[See image.](#itdr-id-details-posture-rem-details)
[]If there are multiple remediations for an issue, you can view a flowchart that breaks down multiple steps into distinct workflows. The workflows in the flowchart are prioritized based on the most suitable remediation to the issue. The most appropriate remediation is listed first, followed by the less suitable ones. After you choose a workflow, you can click the link in an individual step or process to view:
- The remediation description and assessment (**Easy**, **Moderate**, or **Difficult**).
- Instructions or videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation that provides the issue context and remediation details.
[See image.](#itdr-id-details-posture-rem-fc)
Click** Export Remediation Chart** to export the flowchart as an SVG file.
[]Lists the recent active changes detected for the identity across identity platforms, and classifies these changes as a good, bad, or info impact. You can filter change detection results by the date, source (**AD** or** Entra ID**), impact (**Good**, **Bad**, or **Info**), and issue type (**Accounts with exposed attributes**, **Insecure guest access**, etc.).
For each source type, you can view:
- [AD](#itdr-id-details-recent-changes-ad-section)
- [Entra ID](#itdr-id-details-recent-changes-entra-section)
[]For each change, you can view:
- **Change Date**: The date and time when a change is detected in the AD domain.
- **Issue**: The issues for which the change is detected (e.g., **Excessive Access Group**, **DC inconsistent**, etc.).
- **Change**: The description of active changes.
- **Impact**: The change status:
- **Good**: A good or safe change.
- **Bad**: A risky change.
- **Info**: A significant change that might have a good or bad impact based on the environment.
- **Classification**: The AD user account type (**Privileged** or **Service**). You can filter the column to view a specific user account type.
- **Type**: The type of AD identity (**User** or **Computer**).
[See image.](#itdr-id-details-recent-changes-ad-image)
[]For each change, you can view:
- **Change Date**: The date and time when a change is detected in the Entra ID tenant.
- **Issue**: The issues for which the change is detected (e.g., **Insecure permissions on application**, **Privileged guest accounts**, etc.).
- **Initiated By**: The details of the identity who initiated this change.
- **Reason**: The reason for the change.
- **Impact**: The change status:
- **Good**: A good or safe change.
- **Bad**: A risky change.
- **Info**: A significant change that might have a good or bad impact based on the environment.
- **Type**: The type of Entra ID identity (**User** or **Service Principal**).
[See image.](#itdr-id-details-recent-changes-entra-id-image)
[]Lists the detected potential identity attacks or threats. Analyzes the details of attacks in natural language, along with the threat ID that is linked to the MITRE ATT&CK  framework. For each threat detected, you can view:
- **Title**: The title of the threat (**Endpoint - Possible DCShadow attack**, **Endpoint - Possible DCSync attack**, etc.).
- **Description**: The attack description. The threat is analyzed and the details of attacks are presented in natural English language.
- **Threat ID**: The threat ID that is linked to the MITRE ATT&CK  framework
- **Attacker IP**: The IP address of the attacker.
- **Attacker ID**: The email ID of the attacker.
- **Events**: The total number of times the event occurred and the time and date when the attack happened.
- **Severity**: The severity level of the attack or threat (**Critical**, **High**, **Medium**, or **Low**).
[See image.](#itdr-id-details-threats-tab-image)
Click **View in Investigate** to view the attack details on the [Investigate](/itdr/understanding-investigate-module) page.
[]Lists all the exposed endpoint credentials for the identity in the AD. For each credential, you can view:
- **Notable Credentials**: Lists the notable exposed credential issues that you must focus on and prioritize to remediate. For each issue, you can view:
- **Issue Name**: The name of the issue (**Unattend files expose Windows credentials**, **Confluence Credentials were found from browsers**, etc.).
- **Description**: The issue description.
- **Severity**: Severity level (**Critical** or **High**).
- **Credentials**: Lists all the credential issues for the identity categorized by [exposure type](/itdr/viewing-exposed-credentials-scan-type). You can expand each exposure type to view additional credential issue details.
[See image.](#itdr-id-details-credex-tab-image)
[]Provides insight into traffic violations or bad activities on ZIA and ZPA services for the identity in AD and Entra ID. Presents real-time visibility into threat incidents and access policy violations for configured application segments.
ITDR integration with ZIA and ZPA services works with SCIM user provisioning and authentication methods only. Zscaler provides an easy and consistent mechanism for users to use SCIM to manage the life cycle of user and group accounts in the Zscaler cloud. You can view the following information on each tab:
- [Internet Access Insights (ZIA Insights)](#itdr-id-details-access-risk-tab-zia-section)
- [Internal Access Insights (ZPA Insights)](#itdr-id-details-access-risk-tab-zpa-section)
[]You can view and analyze the [threat or security incidents](/zia/about-cybersecurity-insights) for the identity if [ITDR is integrated with ZIA](/itdr/containment-configuration-guide-zscaler-internet-access-zia). On the **Access Risk Assessment** page, you can view:
- **SCIM Username**: The name of the identity as identified by the IdP and used for authentication.
- **SCIM Group**: The SCIM group attributes as configured in your IdP.
- **IdP Name**: The identity provider’s name.
- **Last Location**: The last location from where the identity accessed ZIA or any other website.
- **Malicious traffic trend**: A graph that represents malicious traffic activity or threat incidents recorded for the selected time frame.
- **Threat profile**: A donut chart that is grouped by threat incident categories (malware, spyware, adware, malicious content, etc.) your AD is exposed to.
-
**Diagnostics**: A list of log information for threat incidents represented in a tabular format. You can filter specific information using the search field for a column:
- **Connection**: The date and time when the threat incident occurred.
- **Policy Action**: The explanation of the policy action. To learn more, see [Policy Reasons](/zia/policy-reasons).
- **URL Category**: The URL category of the threat incident. ZIA organizes URLs into a hierarchy of categories for granular filtering and policy creation. To learn more, see [About URL Categories](/zia/about-url-categories).
- **Threat Name**: The threat name.
- **User Location**: The internet gateway location. The list includes **Road Warrior**, the default location for transactions that did not originate from a predefined location.
Click **Export CSV** to export the ZIA diagnostic data as a CSV file. If you have filtered the data in the table, the same information is downloaded as a CSV file.
[See image.](#itdr-id-details-access-risk-zia-image)
[]You can view and analyze access policy violations for [configured application segments](/zpa/about-applications) for the identity if [ITDR is integrated with ZPA](/itdr/containment-configuration-guide-zscaler-private-access-zpa). On the **Access Risk Assessment** page, you can view:
- **SCIM Username**: The name of the identity as identified by the IdP and used for authentication.
- **SCIM Group**: The SCIM group attributes as configured in your IdP.
- **IdP Name**: The identity provider’s name.
- **Last Location**: The last location from where the identity accessed ZPA or any other application segment.
- **Policy block trend**: The trend chart that displays the total number of transactions where the access policy blocked users from accessing the application segments over a selected time frame. To learn more, see [About Policies](/zpa/about-policies).
- **Top 10 app access violations**: The top 10 application segments access violations over a selected time frame. To learn more, see [About Applications](/zpa/about-applications).
-
**Diagnostics**: Lists the log information about evaluated access policy rules for the configured application segments in a table. You can filter specific information using the search field for a column:
- **Connection**: The date and time when the application access violation occurred.
- **Policy**: The name of the access policy rule configured to block specific users from accessing application segments.
- **Application**: The name of the application segment that is accessed.
- **Port**: The port number of the application segment.
- **Protocol**: The protocol name used for application segment discovery.
- **User Location**: The location the AD user is connecting from.
Click **Export CSV** to export the ZPA diagnostic data as a CSV file. If you have filtered the data in the table, the same information is downloaded as a CSV file.
[See image.](#itdr-id-details-access-risk-zpa-image)
Viewing Metadata for an Identity
On the identity details page, you can view metadata for an identity across identity platforms (AD, Entra ID, and Okta). The metadata includes details such as Given Name, User Principal Name, Department, Is Privileged, etc. The metadata enables you to efficiently manage user accounts and enforce appropriate access controls.
Before viewing metadata for identities, run the [AD](/itdr/scanning-active-directory) and [Entra ID](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal) scans. Enable attribute collection for [AD](/itdr/enabling-active-directory-attribute-collection) and [Entra ID](/itdr/about-entra-id-posture-scan) when configuring these scans. Additionally, [integrate ITDR with Okta](/itdr/integrating-itdr-okta).
To view metadata for the identity:
-
On the identity details page, click one or more identity platforms (**AD**, **Entra ID**, and **Okta**).
The metadata appears.
[See image.](#itdr-id-search-view-metadata)
- Click **Expand All** to view metadata for all identity platforms at the same time, and click **Collapse All** to hide all the data.
Taking Action to Contain Threats
When issues or attacks are detected for an identity across identity platforms , you can take immediate action to contain threats or remediate issues.
You can take immediate action to contain threats that are detected for identities stored across identity platforms (AD, Entra ID, and Okta).
To take an action:
- On the identity details page, click **Take Action** and select an option from the drop-down menu:
- [Zscaler](#itdr-identity-search-take-action-zscaler)
- [Active Directory](#itdr-identity-search-take-action-ad)
- [Okta](#itdr-identity-search-take-action-okta)
- [Entra ID](#itdr-identity-search-take-action-entra-id)
- In the confirmation window, click **OK**.
[]Integrate ITDR with [ZIA](/itdr/containment-configuration-guide-zscaler-internet-access-zia) and [ZPA](/itdr/containment-configuration-guide-zscaler-private-access-zpa) before selecting an option:
- **Contain with ZPA**: Contains an attack or threat via the ZPA service. You can forward the attack details to ZPA for automated containment. ZPA inspects the attack details and blocks the identity according to the defined policy.
- **Contain with ZIA**: Contains an attack or threat via the ZIA service. You can forward the attack details to ZIA for automated containment. ZIA inspects the attack details and blocks the identity according to the defined policy.
[See image.](#itdr-id-search-take-action-zscaler-image)
[]Configure a [server agent](/itdr/installing-server-agent) before selecting an action:
- **Enable User**: Enables the AD user account.
- **Disable User**: Disables the AD user account.
- **Reset Password**: Enforces a password change on the next login for the user account on the next login.
- **Revoke Group Membership**: Removes the AD user account from a specific group. Only users from the [privilege group](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-b--privileged-accounts-and-groups-in-active-directory) that are static can be removed. If a user is not a member of the specified group or if the specified group does not exist, no action is taken.
[See image.](#itdr-id-search-ad-take-actions-image)
[]Integrate ITDR with [Okta](/itdr/integrating-itdr-okta) before selecting an action:
- **Suspend**: Suspends the Okta identity and disables access.
- **Unsuspend**: Unsuspends the suspended Okta identity and enables access.
- **Activate**: Activates the deactivated Okta identity. An email is sent to your Okta email ID to activate the account.
- **Deactivate**: Deactivates the Okta identity and temporarily disables access until activated again. This removes access to all the apps that were previously authenticated via Okta.
- **Reset Password**: Resets the password for the Okta identity. An email is sent to your Okta email ID to reset your password.
- **Clear User Sessions**: Clears all active sessions of the identity.
- **Reset Authenticators**: Resets the authenticators (Microsoft multi-factor authentication, SSO, etc.).
[See image.](#itdr-id-search-okta-take-actions-image)
[]Add remediation action permissions to the [Entra ID deployment script](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal) before selecting an action:
- **Revoke Session**: Revokes Entra ID active user sessions to end any potentially compromised sessions. This remediation action doesn’t revoke guest user sessions.
- **Disable User**: Disables the Entra ID user.
- **Enforce MFA**: Creates a conditional access policy in the Entra ID tenant that enforces users to use multi-factor authentication (MFA) for all applications. The conditional policy is created for the first user only. Subsequent users are appended to the existing policy.
- **Enforce phishing-resistant MFA**: Creates a conditional access policy in the Entra ID tenant that enforces users to use MFA for all applications. FIDO2 keys or similar authentication methods are used.
- **Remove Active Role Assignment**: Removes one or more role assignments from the active role.
- **Remove Group Membership**: Removes one or more group memberships.
[See image.](#itdr-id-search-entra-id-take-actions-image)
[]![View all tabs on Identity Details page](/downloads/itdr/dashboard/identity-search/viewing-identity-details/itdr-id-search-details-all-tabs.png)
[]![Take actions to contain attacks via Zscaler services](/downloads/itdr/dashboard/identity-search/taking-action-identity-details-page/itdr-take-action-zscaler-id-search-1.png)
[]![Take actions for AD identities](/downloads/itdr/dashboard/identity-search/taking-action-identity-details-page/itdr-take-action-ad-id-search-1.png)
[]![Take action for Okta identities](/downloads/itdr/dashboard/identity-search/taking-action-identity-details-page/itdr-take-action-okta-id-search_0.png)
[]![Take an action for Entra ID identities](/downloads/itdr/dashboard/identity-search/taking-action-identity-details-page/itdr-take-action-entra-id-search.png)
[]![View identity metadata](/downloads/itdr/dashboard/identity-search/viewing-metadata-identity/itdr-about-identity-details-metedata-2.png)
[]![Click an identity to view details](/downloads/deception/deceive/network-decoys/configuring-services-network-decoy/itdr-about-identity-search-click-id.png)
[]![View the identity issue overview ](/downloads/itdr/dashboard/identity-search/viewing-identity-details/itdr-about-identity-details-overview-tab-2.png)
[]![View the posture issues for the identity](/downloads/itdr/dashboard/identity-search/viewing-identity-details/itdr-about-identity-details-posture-tab.png)
[]![View remediation details](/downloads/itdr/dashboard/identity-search/viewing-identity-details/itdr-about-identity-details-posture-tab-rem-single.png)
[]![View remediation flowchart](/downloads/itdr/dashboard/identity-search/viewing-identity-details/itdr-about-identity-details-posture-tab-rem-flowchart-1.png)
[]![View recent changes for the identity in AD](/downloads/itdr/dashboard/identity-search/viewing-identity-details/itdr-about-identity-details-recent-changes-ad-1.png)
[]![View recent changes for the identity in Entra ID](/downloads/itdr/dashboard/identity-search/viewing-identity-details/itdr-about-identity-details-recent-changes-entra-id.png)
[]![View the threat details for the identity](/downloads/itdr/dashboard/identity-search/viewing-identity-details/itdr-about-identity-details-threats-tab.png)
[]![View exposed credential issues for the identity](/downloads/itdr/dashboard/identity-search/viewing-identity-details/itdr-about-identity-details-credex-tab.png)
[]![View access risk for ZIA](/downloads/itdr/dashboard/identity-search/viewing-identity-details/itdr-about-identity-details-access-risk-zia-1.png)
[]![View access risk for ZPA](/downloads/itdr/dashboard/identity-search/viewing-identity-details/itdr-about-identity-details-access-risk-zpa-1.png)