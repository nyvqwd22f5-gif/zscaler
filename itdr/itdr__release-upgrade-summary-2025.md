# Release Upgrade Summary (2025)
Source: https://help.zscaler.com/itdr/release-upgrade-summary-2025

This article provides a summary of all new features and enhancements for Zscaler ITDR. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).

**Clouds:** illusionblack.com
The following service updates were deployed to illusionblack.com on

## November 04, 2025
### Feature Available
#### Automatic Enablement of Active Directory Attribute Collection
Attribute Collection is enabled for all Active Directory scan configurations by default. This change applies to all customers, including customers who have been disabled in their environment.
[See image.](#Attribute_Collection)
To learn more, see [Managing Active Directory Attribute Collection Settings](/itdr/enabling-active-directory-attribute-collection) and [About Active Directory Posture](/itdr/about-active-directory-posture).
[]![Attribute Collection Enabled ](/sites/default/files/downloads/itdr/itdr/active-directory-posture-scan/enabling-active-directory-attribute-collection/Attribute%20collection.png)

### Feature Available
#### User Interface Changes and Enhancements
The following user interface changes and enhancements were made to the Zscaler ITDR Admin Portal:
- An icon to access error logs was added for server agents and endpoint agents.
[See image.](#Serveragent_errorlog_icon)
[]![Agents error logs](/sites/default/files/downloads/itdr/endpoint-settings/agents/about-endpoint-settings/endpoint_logs_0.png)
To learn more, see [About Server Agents](/itdr/about-server-agents) and [About Endpoint Agents.](/itdr/about-endpoint-settings)
- In the Tenant Details window, the Tenant Name field was renamed to Tenant ID.
[See image.](#Tenant_details)
[]![Tenant details](/sites/default/files/downloads/itdr/endpoint-settings/agents/about-endpoint-settings/Tenant%20Details.png)
To learn more, see [Connecting an Entra ID Tenant with the Zscaler ITDR Admin Portal](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal).

## August 18, 2025
### Feature Available
#### Active Directory Privileged Account Tracking
The Active Directory (AD) Privileged Account Tracking page monitors anomalous login activity of users using a machine learning system. In addition to default privileged users, you can add up to 200 user accounts per AD domain for explicit tracking. Suspicious login activities are displayed in the Active Directory Privileged Account Tracking report, and you can mark the incidents as safe to prevent future alerts for similar behavior.
[See image.](#Ad-privileged-account-tracking)
To learn more, see:
- [About Active Directory Privileged Account Tracking](/itdr/about-active-directory-privileged-account-tracking)
- [About the Active Directory Privileged Account Tracking Report](/itdr/about-the-active-directory-privileged-account-tracking-report)
- [Adding Users for Privileged Account Tracking](/itdr/adding-users-for-privileged-account-tracking)
[]![Active Directory (AD) Privileged Account Tracking](/sites/default/files/downloads/itdr/dashboard/active-directory-posture/active-directory-posture-reports/downloading-itdr-active-directory-executive-report/ITDR-AD-privileged-account-tracking-rn1.png)

### Feature Available
#### Enhanced PDF Reports
The following PDF reports are enhanced to improve clarity in analyzing the report data:
- Entra ID Executive Summary Report
- AD Executive Summary Report
- Entra ID Delta Report
- Active Directory Delta Report
- Endpoint Credential Exposure Report
Additionally, the Entra ID and Active Directory (AD) Executive Summary reports include change detection information to help you track modifications within Entra ID and AD domains.
To learn more, see:
- [Downloading the Zscaler ITDR Microsoft Entra ID Executive Summary Report](/itdr/downloading-zscaler-itdr-microsoft-entra-id-assessment-posture-report)
- [Downloading the Active Directory Executive Summary Report](/itdr/downloading-itdr-active-directory-executive-report)
- [Downloading the Entra ID Delta Report](/itdr/downloading-entra-id-delta-report)
- [Downloading the Active Directory Delta Report](/itdr/downloading-active-directory-delta-report)
- [Downloading the Endpoint Credential Exposure Executive Summary Report](/itdr/downloading-endpoint-credential-exposure-executive-report)

### Feature Available
#### Updates to Server Agent-Based Threat Detection
The threat detection feature was updated to detect the following new attacks on a domain controller (DC) via a server agent:
- [Account Reconnaissance](https://attack.mitre.org/techniques/T1087/002/): An attack technique used by adversaries to use known username dictionaries to exploit authentication errors and discover valid usernames.
- [Password Spray](https://attack.mitre.org/techniques/T1110/003/): An attack technique used by adversaries to attempt to gain access to multiple user accounts with commonly used passwords.
- External IP Authentication (DC): An attack technique used by adversaries to identify login attempts from public IP addresses for credential theft, brute-force attack, or reconnaissance targeting exposed DCs.
- Kerberos Service Ticket Anomaly: Checks anomalous Kerberos service ticket requests using machine learning.
[See image.](#threat-detectionwindow)
To learn more, see [Enabling Threat Detection on a Server Agent](/itdr/enabling-threat-detection-server-agent).
[]![The list of threats detected on a domain controller using a server agent.](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-rn-threat-detection_0.png)

### Feature Available
#### User Interface Changes and Enhancements
The following tabs were renamed in the Zscaler ITDR Admin Portal:
| **Old** | **New** |
| ------- | ------- |
| Settings > User & Roles > SSO | Settings > User & Roles > IdP Providers |
| Settings > Users & Roles > Support Users | Settings > Users & Roles > Zscaler Remote Assistance |
| Settings > Advanced Settings > Maintenance | Settings > Advanced Settings > Manage Events & Evidence |
[See image.](#itdr-rn-user-role-adv-sett-tabs)
To learn more, see:
- [About Users & Roles](/itdr/about-users-roles)
- [About Identity Providers](/itdr/about-identity-provider)
- [About Advanced Settings](/itdr/about-advanced-settings)
[]![View Users & Roles and Advanced Settings tabs](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-idp-maint-remote-support-ui-2.png)

## June 23, 2025
### Feature Available
#### Active Directory Remediations
The Active Directory (AD) Remediations feature allows you to run remediation actions for risky AD identities from the Zscaler ITDR Admin Portal, enhancing the AD domain security posture. You must [configure a server agent to run AD remediation actions](/itdr/enabling-remediation-server-agent). You can run remediation actions for specific or multiple identities (in bulk).
The following remediation actions are available:
- Enable User
- Disable User
- Reset Password
- Revoke Group Membership
[See image.](#itdr-rn-ad-remediation-actions)
To learn more, see [Running Remediation Actions for Active Directory Identities](/itdr/running-remediation-actions-ad-identities).
After remediation, you can view remediation logs that provide actionable insights with additional details such as remediation action details, impacted identity, timestamp, remediation status, etc.
[See image.](#itdr-rn-view-ad-remediation-history)
To learn more, see [Viewing Active Directory Remediation History](/itdr/viewing-ad-remediation-history).
[]![Run a remediation action](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-ad-remediation-1.png)
[]![View AD remediation history](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-view-ad-remediation-logs-1.png)

### Feature Available
#### Identity Search
The Identity Search feature allows you to search for specific identities across identity platforms—including Active Directory (AD), Entra ID, and Okta—all on a single page. You can search for identities by username, first name, last name, email address, and more.
These identities are correlated and enriched with information from Zscaler ITDR posture capabilities, including security issues, credentials these identities store on endpoints, and any risky changes recorded against those identities.
[See image.](#itdr-rn-identity-search-page)
To learn more, see [About Identity Search](/itdr/about-identity-search).
You can drill down to a specific identity to view unified issue details, including posture issues, recent changes, detected threats, access risk assessments for the Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) services, etc. You can further investigate and remediate issues to improve the identity's security posture.
Additionally, you can [view metadata](/itdr/viewing-metadata-identity) for the identity for all supported platforms and [take immediate actions](/itdr/taking-action-identity-details-page) to contain detected attacks.
[See image.](#itdr-rn-identity-details-page)
To learn more, see [Viewing Identity Details](/itdr/viewing-identity-details).
[]![Search for an identity](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-identity-search-page.png)
[]![View identity details](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-identity-details-page.png)

### Feature Available
#### ITDR Integration with ServiceNow
Zscaler ITDR supports integration with ServiceNow to track and assess issues across the Zscaler ITDR Admin Portal (AD domain, credential, Entra ID) along with bad changes detected in the AD domain and Entra ID. You can create a ServiceNow incident for an issue and track it in the ServiceNow portal. This provides real-time visibility into incidents, and you can assign the incident to the appropriate team or individual to analyze and take required action.
You can create an incident on the following pages:
- Active Directory Posture dashboard
- Active Directory Change Detection dashboard
- Endpoint Credential Exposure dashboard
- Entra ID Posture dashboard
- Entra ID Change Detection dashboard
[See image.](#entraID-serviceNowticket)
To learn more, see:
- [About Configurations](https://help.zscaler.com/itdr/about-configurations)
- [Configuring a ServiceNow Webhook](https://help.zscaler.com/itdr/configuring-servicenow-webhook)
- [Configuring ITDR with ServiceNow](https://help.zscaler.com/itdr/configuring-itdr-servicenow)
- [Creating a ServiceNow Ticket](https://help.zscaler.com/itdr/creating-servicenow-ticket)
- [Viewing Incident Details](https://help.zscaler.com/itdr/viewing-incident-details)
[]![The Entra ID Posture dashboard listing the detailed findings of the posture issues and annotations around Actions and Create ServiceNow ticket option.](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-rn-entraID-posture-dashboard.png)

### Feature Available
#### Retention Period for Okta Logs
Okta system logs for threat detection are only retained for 14 days. You cannot modify this retention period.
To learn more, see [Viewing Affected AD User Account Details](/itdr/viewing-affected-active-directory-user-account-details), [Integrating ITDR with Okta](/itdr/integrating-itdr-okta), and [About Advanced Settings](/itdr/about-advanced-settings).

### Feature Available
#### Threat Detection
The threat detection feature enables you to detect threats on a domain controller using a server agent. Zscaler ITDR identifies these threats and enriches the data with contextual information for easier investigation and further analysis. The following types of attacks are detected via a server agent:
- [DCSync](https://attack.mitre.org/techniques/T1003/006/): An attack that allows an adversary to simulate the behavior of a domain controller and retrieve password hashes from another domain controller in the AD environment.
- [DCShadow](https://attack.mitre.org/techniques/T1207/): An attack in which an adversary registers a fake AD domain controller and uses that to inject malicious AD objects (e.g., credentials) into other domain controllers that are part of the same AD infrastructure.
- [Kerberoasting](https://attack.mitre.org/techniques/T1558/003/): A pervasive attack technique targeting AD service account credentials.
- [AS-REP roasting](https://attack.mitre.org/techniques/T1558/004/): An attack in which an adversary targets accounts that have disabled Kerberos pre-authentication.
- [Suspicious DPAPI access](https://attack.mitre.org/techniques/T1555/): Suspicious attempts to retrieve domain backup keys from a domain controller.
- [Suspicious Group Additions](https://attack.mitre.org/tactics/TA0003/): Attempts to establish persistence by adding malicious users to privileged groups in an organization's domain.
- [Brute Force](https://attack.mitre.org/techniques/T1110/): An attack method used to gain unauthorized access to AD accounts.
[See image.](#threat-detectiontab)
To learn more, see [Enabling Threat Detection on a Server Agent](/itdr/enabling-threat-detection-server-agent).
[]
![The Threat Detection tab with the list of threats detection that can be enabled on a server agent.](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-rn-threat-detection.png)

### Feature Available
#### User Interface Changes and Enhancements
The following user interface changes and enhancements were made to the Zscaler ITDR Admin Portal:
-
On the Password Analysis Dashboard (ITDR > Dashboard > Password Analysis), the Password Reuse pie charts legends were renamed to Identities without password reuse and Identities with password reuse.
[See image.](#itdr-rn-password-reuse-pie-chart-legends)
To learn more, see [About Password Analysis](/itdr/about-password-analysis).
-
On the Password Analysis Details page (ITDR > Dashboard > Password Analysis > Details), the Password Reuse column was renamed to Password Reuse Count.
[See image.](#itdr-rn-password-analysis-details-count)
To learn more, see [Viewing Password Analysis Details](/itdr/viewing-password-analysis-details).
-
The following dashboards were renamed:
| Old | New |
| --- | --- |
| Identity Posture | Active Directory Posture |
| Change Detection | Active Directory Change Detection |
| Entra ID | Entra ID Posture |
| Identity Risk Summary | Risk Summary |
[See image.](#itdr-dashboards)
To learn more, see:
- [About Active Directory Posture](/itdr/about-identity-posture-dashboard)
- [About Active Directory Change Detection](/itdr/about-change-detection-dashboard)
- [About Entra ID Posture](/itdr/about-entra-id-dashboard)
- [About Risk Summary](/itdr/about-identity-risk-summary-dashboard)
-
On the Risk Summary dashboard, you can select an AD domain in the Active Directory widget or an Entra ID tenant in the Entra ID widget to view the top three or critical misconfigurations or vulnerabilities detected in that domain or tenant.
[See image.](#risk-summary-dashboard)
To learn more, see [About Risk Summary](/itdr/about-identity-risk-summary-dashboard).
[]![View Password Reuse charts](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-password-reuse-chart-legends-1.png)
[]![View password analysis details](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-password-analysis-details-reuse-count-1.png)
[]![View ITDR dashboards](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-dashboard-options.png)
[]![The Risk Summary dashboard displaying the top misconfigurations and vulnerabilities across identity managements.](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-risk-summary-dashboard.png)

## April 14, 2025
### Feature Available
#### Mark Events or Attackers as Unsafe
You can select an event or attacker and mark it as unsafe. When you mark an event or attacker as unsafe, the allowlist rules are removed, and the attacker is flagged for further investigation.
[See image.](#mark_as_unsafe_option)
To learn more, see [Taking Action from the Dashboard](/itdr/taking-action-dashboard).
[]
![View mark as unsafe option](/sites/default/files/downloads/itdr-release-notes-mark-as-unsafe.png)

### Feature Available
#### New Criteria in Endpoint Credential Exposure and Threat Detection Policies
The following new criteria for selecting endpoints were added to endpoint credential exposure and threat detection policies:
| Selection Criterion | Description |
| ------------------- | ----------- |
| DNS Hostname (Specific) | Select endpoints based on their FQDNs by specifying the complete FQDN value |
| DNS Hostname (RegEx) | Select endpoints based on their FQDNs by specifying a regular expression for the FQDN value |

### Feature Available
#### New Endpoint Credential Exposure Type
The Local Security Authority (LSA) Protections scan type was added to check the registry keys to confirm if LSA protection is enabled.
[See image.](#itdr-rn-lsa-check)
To learn more, see [Viewing Exposed Credentials by Scan Type](/itdr/viewing-exposed-credentials-scan-type).
You can enable or disable the LSA Protections scan type when configuring the endpoint credential exposure scan.
[See image.](#LSA_protections_scan_type)
To learn more, see [Enabling or Disabling Scan Types in Credential Exposure Scan](/itdr/enabling-or-disabling-scan-types-credential-exposure-scan).
[]![View LSA protection check details](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-lsa-check.png)
![View LSA protections scan type](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-note-scan-type-lsa-protections.png)
[]

### Feature Available
#### Password Reuse Analysis
On the Password Analysis dashboard (ITDR > Dashboard > Password Analysis), you can view the percentage of Active Directory (AD) users who have reused passwords. The data is represented in pie charts for both regular and privileged users.
[See image.](#itdr-rn-pwd-reuse-analysis-charts)
To learn more, see [About Password Analysis](/itdr/about-password-analysis).
On the Password Analysis details page (ITDR > Dashboard > Password Analysis > Details), you can view the total number of times a password was reused and if password rotation occurred for AD users.
[See image.](#itdr-rn-pwd-rotation-reuse)
To learn more, see [Viewing Password Analysis Details](/itdr/viewing-password-analysis-details).
On the Summary tab (ITDR > Identity Posture > Top 10 Users & Computers > User), you can view the total number of other AD user accounts that share the same password as the affected AD user. This count excludes the affected AD user.
[See image.](#itdr-rn-aff-ad-user-password-reuse)
To learn more, see [Viewing Affected AD User Account Details](/itdr/viewing-affected-active-directory-user-account-details).
[]![View password reuse data for the affected user](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-aff-user-summary-password-reuse.png)
[]![View password reuse analysis](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-password-reuse-analysis-3.png)
[]![View password rotation and reuse details](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-password-reuse-details.png)

### Feature Available
#### Standardized Role Assignments in Entra ID
Posture checks for Entra ID identities support both active and eligible role assignment types, providing an effective approach to role monitoring. For an affected Entra ID identity, you can view the role assignment type on the Roles > Entra tab.
[See image.](#itdr-rn-entra-id-role-assignment-type)
To learn more, see [Viewing Affected Entra ID Identity Details](/itdr/viewing-affected-entra-id-identity-details#itdr-entra-id-identity-role-entra-sub-tab).
[]![View Entra ID role assignment type](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-entra-role-assignment.png)

### Feature Available
#### User Interface Changes and Enhancements
The following user interface changes and enhancements were made to the Zscaler ITDR Admin Portal:
-
On the Entra tab (ITDR > Manage > Change Detection), a new column named Policy Enabled was added. This column shows you the status of policies, indicating whether a policy is enabled or disabled. A green checkmark icon indicates that a policy is enabled, and a red X icon indicates that the policy is disabled.
[See image.](#policy_enabled_column)
To learn more, see [About Entra ID Change Detection Policies](/itdr/about-entra-id-change-detection-policies).
-
On the Threat Detection tab (ITDR > Manage > Threat Detection), a Delete Selected button was added that allows you to select and delete multiple policies.
[See image.](#delete_selected_option)
To learn more, see [Managing Threat Detection Policy](/itdr/managing-threat-detection-policy).
-
On the Endpoint Credential Exposure tab (ITDR > Manage > Endpoint Credential Exposure), a new search field was added under the Name column that allows you to search for a scan by name.
[See image.](#search_field)
To learn more, see [About Endpoint Credential Exposure Scan](/itdr/about-endpoint-credential-exposure-scan).
[]
![View policy enabled column](/sites/default/files/downloads/itdr/threat-detection-policies/managing-threat-detection-policy/itdr-release-notes-entra-policy-enabled.png)
[]
![View delete selected button](/sites/default/files/downloads/itdr/threat-detection-policies/managing-threat-detection-policy/itdr-release-notes-threat-detection-delete-selected-.png)
[]
![View search field](/sites/default/files/downloads/itdr/threat-detection-policies/managing-threat-detection-policy/itdr-release-notes-search-field.png)

### Feature Available
#### View Allowlisted Rules
When an event or attacker is marked as safe due to an allowlist rule, you can view the specific rule that triggered the action on the Event Logs page.
[See image.](#whitelisted_rule)
To learn more, see [About Event Logs](/itdr/about-event-logs).
[]
![View whitelisted rule](/sites/default/files/downloads/itdr-release-notes-whitelist-rule.png)

## March 05, 2025
### Feature Available
#### Active Directory and Entra ID Scan Delta Reports
The Delta Report feature enables you to effectively monitor changes in Active Directory (AD) domains and Entra ID tenants. This feature streamlines the process of monitoring, tracking, and responding to security posture changes over time.
You can automatically compare two historical scans and download the delta report to identify newly introduced risks, resolved issues, and updates to the existing risks. You can download these delta reports in PDF or Excel formats for offline review, collaboration, and efficient remediation.
[See image.](#itdr-rn-delta-scan-report)
To learn more, see [Downloading the Active Directory Delta Report](/itdr/downloading-active-directory-delta-report) and [Downloading the Entra ID Delta Report](/itdr/downloading-entra-id-delta-report).
[]![View Delta scan report](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-delta-report-ad-entra-id.png)

### Feature Available
#### Copying Columns from Tables
You can copy specific columns from tables (up to 1,000 rows) and paste them into CSV, JSON, Notepad, or other compatible files across various modules (Identity Posture, Entra ID, Credential Exposure, Change Detection, etc.) in the ITDR Admin Portal.
[See image.](#itdr-rn-copy-column-table)
To learn more, see [Using Tables](/itdr/using-tables#itdr-copy-columns-table-section).
[]![Copy specific columns from the table](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-copy-columns-table-1.png)

### Feature Available
#### Endpoint Credential Exposure Enhancements
The following enhancements are made to the Endpoint Credential Exposure module:
-
The following sections were added to the Endpoint Credential Exposure dashboard (ITDR > Dashboard > Endpoint Credential Exposure):
- Domain risk category or severity level (Critical, High, Medium, Low, etc.).
- Details of the top 5 credential exposure issues that exist on your endpoints.
- Credential exposure issues categorized by severity in a bar chart.
- Credential exposure issues categorized by risk in a donut chart.
- Risk Reduction Roadmap.
[See image.](#itdr-rn-endpoint-credex-dashboard)
To learn more, see [About the Endpoint Credential Exposure Dashboard](/itdr/about-endpoint-credential-exposure-dashboard).
-
The Detailed Findings page (ITDR > Dashboard > Endpoint Credential Exposure > Detailed Findings) was added. This page shows all the exposed credential issues on your endpoints. You can view additional details about each issue and recommendations to further investigate and remediate the issue.
[See image.](#itdr-credex-detailed-findings)
To learn more, see Viewing the [Viewing Exposed Endpoint Credential Detailed Findings and Recommendations Details](/itdr/viewing-exposed-endpoint-credential-detailed-findings-and-recommendations-details).
- The following scan or exposure types were added:
- Windows OOBE Priv Esc
- Windows OOBE Files
- Unmanaged Local Admins
- The following scan or exposure types were removed:
- Browser cookies - Removed
- Saved Browser Credentials
- LSASS Application secrets
- LSASS Login Sessions
- Insecure UAC Settings
- Active Sessions
- Recent Run Commands
- Recent Powershell Commands
- Certificate Files
-
The Cached Domain Logon Credentials scan or exposure type supports the credential cleanup feature.
[See image.](#itdr-rn-new-deprecated-exposure-types)
To learn more, see [Viewing Exposed Endpoint Credential Details by Scan Type](/itdr/viewing-endpoint-credential-exposure-issues) and [Cleaning Up Exposed Endpoint Credentials](/itdr/cleaning-exposed-endpoint-credentials).
-
The Severity column was removed from the table on the Identities page (ITDR > Dashboard > Endpoint Credential Exposure > Identities).
[See image.](#itdr-rn-credex-identities)
To learn more, see [Viewing Identities with Exposed Endpoint Credentials](/itdr/viewing-identities-endpoint-exposures).
-
You can filter issues by severity level on the Detailed Findings, MITRE ATT&CK  Exposure, and Privilege Escalation Path pages.
[See image.](#itdr-rn-credex-filter-by-severity)
[]![View Credential Exposure Dashboard](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-credex-dashboard-enhancements-1.png)
[]![View Detailed Findings page](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-credex-detailed-findings-page.png)
[]![View endpoint credential exposure scan types](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-credex-checks.png)
[]![View the Identities page](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-credex-identities.png)
[]![Filter endpoint exposed credential issues by severity](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-credex-filter-issues-by-severity.png)

### Feature Available
#### Entra ID Remediations
The Entra ID Remediation Action feature allows you to automatically run remediation actions for risky Entra ID identities from the Zscaler ITDR Admin Portal, enhancing the Entra ID tenant security posture. You can run remediation actions for specific or multiple identities (in bulk).
The following remediation actions are available:
- Disable User
- Revoke Session
- Enforce MFA
- Enforce MFA or phishing-resistant MFA
- Remove Active Role Assignment
- Remove Group Membership
[See image.](#itdr-rn-entra-id-remediation-action)
To learn more, see [Running Remediation Actions for Microsoft Entra ID Issues](/itdr/running-remediation-actions-microsoft-entra-id-issues).
After remediation, you can view remediation logs that provide actionable insights with additional details such as remediation action details, impacted identity, timestamp, remediation status, etc.
[See image.](#itdr-rn-entra-id-remediation-history)
You can add or remove permissions for running remediation actions while deploying a script in the Azure portal.
[See image.](#view_azure_cloud_shell)
To learn more, see [Connecting an Entra ID Tenant with the Zscaler ITDR Admin Portal](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal).
[]![View Entra ID remediation actions](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-entra-id-remediations.png)
[]![View Entra ID remediation history details](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-entra-id-remediation-history.png)
![Azure cloud shell](/sites/default/files/downloads/itdr/dashboard/entra-id/about-entra-id-dashboard/itdr-cloud-shell-deploy-resources.png)
[]

### Feature Available
#### Export Event Fields in JSON
ITDR supports exporting event fields in JSON format. You can export all the event fields and use them for further analysis and investigation.
[See image.](#exporting_event_logs)
To learn more, see [Exporting Event Logs](/itdr/exporting-event-logs).
[]
![Export event fields as JSON ](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-exporting-event-logs.png)

### Feature Available
#### Integration with Amazon GuardDuty
Zscaler ITDR supports integration with Amazon GuardDuty to isolate and contain attackers who interact with decoys by blocking access to those users across AWS resources.
[See image.](#1519646-aws-guarduty)
[]![Configuring AWS GuardDuty Intgeration](/sites/default/files/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-zscaler-private-access-zpa/zscaler-awsguardduty.png)

### Feature Available
#### Risk Reduction Roadmap
The Risk Reduction Roadmap feature provides a proactive security approach to enhance the security posture of your identity infrastructure, including Active Directory (AD), Entra ID, and endpoints.
An interactive in the Risk Reduction Roadmap section on the dashboard enables you to assess the current domain risk severity (Critical, High, Medium, or Low), and set a target severity level to systematically lower the domain risk.
After the target severity level is set, ITDR provides an actionable and prioritized risk and remediation roadmap. This roadmap helps you identify, prioritize, and remediate issues, ensuring a structured approach to improving the security posture of your identity infrastructure.
[See image.](#itdr-rn-risk-reduction-roadmap)
To learn more, see [Viewing the Active Directory Risk Reduction Roadmap](/itdr/viewing-active-directory-risk-reduction-roadmap), [Viewing the Entra ID Risk Reduction Roadmap](/itdr/viewing-entra-id-risk-reduction-roadmap), and [Viewing the Exposed Endpoint Credential Risk Reduction Roadmap](/itdr/viewing-exposed-endpoint-credential-risk-reduction-roadmap).
[]![View risk reduction roadmap](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-risk-reduction-roadmap-1.png)

### Feature Available
#### ZPA Containment Support for ZIdentity-Enabled Tenants
Support for containment with Zscaler Private Access (ZPA) is extended to ZIdentity-enabled tenants. If a user is contained with ZPA, then real apps become inaccessible and only app decoys remain accessible.
To learn more, see [Containment Configuration Guide for Zscaler Private Access (ZPA)](/deception/containment-configuration-guide-zscaler-private-access-zpa).

### Feature in Limited Availability
#### Active Directory Monitoring with Server Agent
The ITDR server agent monitors Active Directory (AD) users and computer activities, providing insights to help you quickly address identity-based threats. You can download the server agent directly from the ITDR Admin Portal and run the installation command to complete the setup.
[See image.](#itdr_server_agent)
To learn more, see [About Server Agents](/itdr/about-server-agents).
Session Tracking
You can enable session tracking in the server agent policy to monitor logon activities for all AD administrators and privileged accounts. The server agent collects activity logs and displays the details on the Summary and Session Tracking pages (ITDR > Identity Posture > Top 10 Users & Computers). This feature helps you to identify any anomalous user activity.
[See image.](#itdr-rn-server-agent-session-track)
To learn more, see [Viewing Affected Active Directory User Account Details](/itdr/viewing-affected-active-directory-user-account-details).
Password Analysis
You can enable and configure password analysis in the server agent policy to identify compromised or weak passwords by checking hashes against leaked databases, common patterns, and custom dictionaries while also monitoring for password reuse or rotation. The analysis is done locally on the selected domain controller (DC) and does not leave the customer environment, ensuring security and compliance. The password analysis details are displayed on the Password Analysis Dashboard (ITDR > Dashboard > Password Analysis).
[See image.](#password_analysis_dashboard)
To learn more, see [About Password Analysis](/itdr/about-password-analysis-dashboard).
[]![View the session tracking details](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-server-agent-session-tracking.png)
[]
![View itdr server agent](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-server-agent.png)
[]![View Password Analysis dashboard](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2025/itdr-release-notes-ad-password-analysis-1.png)
