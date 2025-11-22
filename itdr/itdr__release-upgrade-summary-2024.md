# Release Upgrade Summary (2024)
Source: https://help.zscaler.com/itdr/release-upgrade-summary-2024

This article provides a summary of all new features and enhancements for Zscaler ITDR. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).

**Clouds:** illusionblack.com
The following service updates were deployed to illusionblack.com on

## December 04, 2024
### Feature Available
#### ITDR Attribute Collection
Zscaler ITDR collects Active Directory (AD) objects, Entra ID identities, and Okta attributes. ITDR leverages these attributes to provide context for the misconfigurations detected.
Active Directory Attribute Collection
ITDR collects AD object (user and computer) attributes, such as objectSid, description, pwdLastSet, department, etc. After you configure an AD domain for [scanning](/itdr/scanning-active-directory), you can [enable attribute collection](/itdr/enabling-active-directory-attribute-collection). The Windows endpoint agent assigned for scanning the AD domain collects the attributes. ITDR leverages these attributes to provide context for the misconfigurations detected in the AD.
[See image.](#itdr-rn-ad-attribute-coll)
To learn more, see [About Active Directory Posture](/itdr/about-active-directory-posture) and [Enabling Active Directory Attribute Collection](/itdr/enabling-active-directory-attribute-collection).
Entra ID Attribute Collection
ITDR collects Entra ID attributes, such as giveName, displayName, department, etc. After you connect an Entra ID tenant with ITDR for scanning, the attribute collection is enabled by default. When scanning the Entra ID tenants, ITDR collects these attributes. ITDR leverages these attributes to provide context for the misconfigurations detected in Entra ID tenants.
To learn more, see [About Entra ID Posture Scan](/itdr/about-entra-id-posture-scan) and [Connecting an Entra ID Tenant with the Zscaler ITDR Admin Portal](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal).
[]![Enable AD attribute collection](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-ad-attribute-collection.png)

### Feature Available
#### Remediation Flowchart
If there are multiple remediations for an issue, Zscaler ITDR provides a flowchart that breaks down multiple steps into distinct workflows. The workflows in the flowchart are prioritized based on the most suitable remediation to the issue. The most appropriate remediation is listed first, followed by the less suitable ones.
Active Directory Remediation Flowchart
You can view remediation flowcharts for Active Directory (AD) misconfigurations on the Detailed Findings and Recommendations Details page (ITDR > Identity Posture > Detailed Findings and Recommendations) and the Posture tab for the affected identity. In the flowchart, you can choose a suitable workflow to remediate the issue by clicking the reference link on an individual step or process to view more information, such as the issue context and remediation details. You can export the remediation chart as an SVG file and [add AD objects to the safelist](/itdr/adding-active-directory-object-safelist).
[See image.](#itdr-rn-ad-remediation-flowchart)
To learn more, see [Viewing the Active Directory Detailed Findings and Recommendations Details](/itdr/viewing-issue-finding-recommendation-details) and [Viewing Affected Active Directory User Account Details](/itdr/viewing-affected-active-directory-user-account-details).
Entra ID Remediation Flowchart
You can view remediation flowcharts for Entra ID misconfigurations on the Detailed Findings and Recommendations Details page (ITDR > Entra ID > Detailed Findings and Recommendations) and the Posture tab for the affected identity. In the flowchart, you can choose a suitable workflow to remediate the issue by clicking the reference link on an individual step or process to view more information, such as the issue context and remediation details. You can export the remediation chart as an SVG file and [add Entra ID objects to the safelist](/itdr/adding-entra-id-object-safelist).
[See image.](#itdr-rn-entra-id-remediation-flowchart)
To learn more, see [Viewing the Entra ID Detailed Findings and Recommendations Details](/itdr/viewing-entra-id-findings-recommendations) and [Viewing Affected Entra ID Identity Details](/itdr/viewing-affected-entra-id-identity-details).
[]![View AD remediation flowchart](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-ad-remediation-flowchart-2.png)
[]![View Entra ID remediation chart](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-entra-id-remediation-flowchart-1.png)

### Feature Available
#### User Interface Changes and Enhancements
The Add Objects to Safelist option was added to the Detailed Findings and Recommendations page on the Active Directory dashboard (ITDR > Dashboard > Identity Posture) and Entra ID dashboard (ITDR > Dashboard > Entra ID).
[See image.](#bulk-add-object-safelist)
To learn more, see [Adding an Active Directory Object to the Safelist](/itdr/adding-active-directory-object-safelist) and [Adding an Entra ID Object to the Safelist](/itdr/adding-entra-id-object-safelist).
[]![A screenshot highlighting the options to add objects to safelist in bulk](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-bulk-add-option.png)

## October 15, 2024
### Feature Available
#### New Entra ID Posture Checks
New Entra ID posture checks were added to detect misconfigurations. The posture checks are related to best practice violations for applications, multi-factor authentication (MFA), insecure privilege management, data loss, etc. After an Entra ID tenant is scanned, issues detected for these posture checks are listed under the Detailed Findings and Recommendations Details widget on the Entra ID dashboard.
To learn more, see [About the Entra ID Dashboard](/itdr/about-entra-id-dashboard).

## August 14, 2024
### Feature Available
#### Change Detection Object Safelists
Object Safelist is introduced for Active Directory and Entra ID Change Detections.
You can add an Active Directory Change Detection to the AD Change Detection Object Safelist from the Change Detection Page (ITDR > Dashboard > Change Detection).
[See image.](#itdr-rn-ad-cd-object-option)
You can view and manage the AD Change Detection Object Safelist under ITDR > Settings > AD Change Detection Object Safelist.
[See image.](#itdr-rn-ad-cd-object-manage)
To learn more, see [About Active Directory Change Detection Object Safelist](/itdr/about-active-directory-change-detection-policies).
You can add an Entra ID Change Detection to the Entra ID Change Detection Object Safelist from the Entra ID Change Detection Page (ITDR > Dashboard > Entra ID Change Detection).
[See image.](#itdr-rn-entra-id-cd-object-option)
You can view and manage the Entra ID Change Detection Object Safelist under ITDR > Settings > Entra ID Change Detection Object Safelist.
[See image.](#itdr-rn-entra-id-cd-object-manage)
To learn more, see [About Entra ID Change Detection Object Safelist](/itdr/about-entra-id-change-detection-object-safelist).
[]![AD Change Detecton Page](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-cd-object-safelistoption.png)
[]![AD Change Detection Object Safelist](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-manage-cd-ad-object-safelist.png)
[]![Entra ID Change Detection Page](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-change-detection-entra-id-option.png)
[]![Entra ID Change Detection Object Safelist](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-manage-cd-entra-idobject-safelist.png)

### Feature Available
#### Clean Up Exposed Endpoint Credentials
Exposed credentials on the endpoint enable adversaries to escalate privileges and access sensitive data and applications. Zscaler ITDR scans the endpoints and provides visibility into exposed endpoint credentials. You can investigate these credentials and, as a remediation action, clear or clean them up from the endpoints, thereby reducing the compromise phase attack surface available to an adversary.
Currently, ITDR supports credential cleanup for the following exposure or scan types only:
- Saved Windows Credentials
- AWS Credentials
- Azure Credentials
- Google Cloud Credentials
- Database Connections
- Saved VNC Passwords
- Admin AutoLogon Settings
[See image.](#itdr-rn-clean-up-exposed-credentials)
To learn more, see [About the Endpoint Credential Exposure Dashboard](/itdr/about-endpoint-credential-exposure-dashboard), [Viewing Exposed Endpoint Credential Details by Scan Type](/itdr/viewing-endpoint-credential-exposure-issues), and [Cleaning Up Exposed Endpoint Credentials](/itdr/cleaning-exposed-endpoint-credentials).
[]![Clean up exposed endpoint credentials](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-cleanup-exposed-endpoint-credentials-1.png)

### Feature Available
#### Custom Change Detection
You can configure change detection policies to detect when changes to critical properties in Active Directory (AD) and Entra ID identities are made. You can specify users, groups, computers, service principals, and roles. After the changes are detected, users are notified about these changes. The detected changes are displayed on dashboards for further analysis and remediation.
Active Directory Change Detection Policy
You can create policies based on various properties across users, groups, and computers to detect AD changes. In addition, you can notify specific users when the changes pertaining to a policy are detected.
[See image.](#itdr-rn-ad-change-pdetection-policy-window)
To learn more, see [Creating an Active Directory Custom Change Detection Policy](/itdr/creating-active-directory-custom-change-detection-policy).
Entra ID Change Detection Policy
You can create policies based on various properties across users, service principals, and roles to detect Entra ID changes. In addition, you can notify specific users when the changes pertaining to a policy are detected.
[See image.](#itdr-rn-entra-id-change-detection-policy-window)
To learn more, see [Creating an Entra ID Custom Change Detection Policy](/itdr/creating-entra-id-custom-change-detection-policy).
Active Directory Custom Change Detection Dashboard
After you configure and deploy an AD change detection policy, the detected AD identity properties changes are displayed on the AD Custom Change Detection dashboard. You can monitor and analyze these changes to improve the security posture of your AD domain.
[See image.](#itdr-rn-ad-custom-cd-dashboard)
To learn more, see [About the AD Custom Change Detection Dashboard](/itdr/about-active-directory-custom-change-detection-dashboard).
Entra ID Custom Change Detection Dashboard
After the Entra ID change detection policy is created and deployed, the detected Entra ID identity properties changes are displayed on the Custom Change Detection dashboard. You can monitor and analyze these changes to improve the security posture of your Entra ID tenant.
[See image.](#itdr-rn-entra-id-custom-cd-dashboard)
To learn more, see [About the Entra ID Custom Change Detection Dashboard](/itdr/about-entra-id-custom-change-detection-dashboard).
[]![AD Change Detection Policy Window](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-ad-change-detection-policy.png)
[]![Entra ID Change Detection Policy Window](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-entra-id-policy-changes.png)
[]![View custom AD change detection dashboard](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-ad-custom-change-detection.png)
[]![View Entra ID custom change detection dashboard ](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-entra-id-custom-change-detection.png)

### Feature Available
#### Expiration for Safelists
You can configure an expiration date while adding an item to the safelist. The item is retained in the respective safelists until the configured expiration date. This ensures that safelisted objects are automatically added back for consideration in scan results after the expiration date. Objects in the safelist are not counted towards risk scoring.
[See image.](#rn-safelist-window)
You can configure the expiration date while adding items to the following safelists:
- [Active Directory Issue Safelist](/itdr/adding-issue-active-directory-issue-safelist)
- [Active Directory Object Safelist](/itdr/adding-active-directory-object-safelist)
- [AD Change Detection Issue Safelist](/itdr/adding-change-detection-issue-safelist)
- [AD Change Detection Object Safelist](/itdr/adding-change-detection-ad-change-detection-object-safelist)
- [Entra ID Issue Safelist](/itdr/adding-issue-entra-id-issue-safelist)
- [Entra ID Object Safelist](/itdr/adding-entra-id-object-safelist)
- [Entra ID Change Detection Issue Safelist](/itdr/adding-change-detection-issue-entra-id-change-detection-safelist)
- [Entra ID Change Detection Object Safelist](/itdr/adding-change-detection-entra-id-change-detection-object-safelist)
An option to filter safelist items based on whether they are active or expired was also added to the respective safelist pages.
[See image.](#rn-safelist-table)
[]
![Add to Safelist Window](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-option-safelist-window.png)
[]
![AD Change Detection Issue Safelist](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-saflist-expiration-column.png)

### Feature Available
#### Export Okta, ZIA, and ZPA Logs to CSV for the Active Directory User
For an Active Directory (AD) user account that is affected by issues, you can export the Okta activity change logs and Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) threat or security incident logs individually into CSV files.
[See image.](#itdr-rn-okta-zia-zpa-export-csv)
To learn more, see [Viewing Affected Active Directory User Account Details](/itdr/viewing-affected-active-directory-user-account-details).
[]![Export Okta, ZIA, and ZPA logs to CSV](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-export-csv-okta-zia-zpa-1.png)

### Feature Available
#### User Interface Changes and Enhancements
The following user interface changes and enhancements were made to the Zscaler ITDR Admin Portal:
-
The Active Directory Vulnerability report (ITDR > Identity Posture > View Report) was renamed to Active Directory Posture Scan Report.
[See image.](#itdr-rn-ad-posture-scan-report)
To learn more, see [Viewing the Active Directory Posture Scan Report](/itdr/viewing-vulnerability-report).
-
The MITRE ATT&CK tactics were recorded on ITDR dashboards (Active Directory, Entra ID, Risk Summary, etc.) to match the [MITRE ATT&CK matrix layout for enterprises](https://attack.mitre.org/#).
[See image.](#itdr-rn-reorder-mitre-attack-tactic)
To learn more, see [About the Identity Posture Dashboard](/itdr/about-identity-posture-dashboard), [About the Entra ID Dashboard](/itdr/about-entra-id-dashboard), and [About the Identity Risk Summary Dashboard](/itdr/about-identity-risk-summary-dashboard).
-
Focus Area was renamed to Detailed Findings and Recommendations on the Active Directory (ITDR > Dashboard > Identity Posture) and Entra ID (ITDR > Dashboard > Entra ID) dashboards.
[See image.](#itdr-rn-detailed-findings-recomm)
To learn more, see [About the Identity Posture Dashboard](/itdr/about-identity-posture-dashboard) and [Viewing the AD Detailed Findings and Recommendations Details](/itdr/viewing-issue-finding-recommendation-details).
[See image.](#itdr-rn-entra-detailed-findings-recomm)
To learn more, see [About the Entra ID Dashboard](/itdr/about-entra-id-dashboard) and [Viewing the Entra ID Detailed Findings and Recommendations Details](/itdr/viewing-entra-id-findings-recommendations).
-
Add to Safelist was renamed to Add Issue to Safelist on the Detailed Findings and Recommendations (formerly Focus Area) page on the Active Directory (ITDR > Dashboard > Identity Posture) and Entra ID (ITDR > Dashboard > Entra ID) dashboards.
[See image.](#itdr-rn-add-safelist-button)
To learn more, see [Adding an Issue to the Active Directory Issue Safelist](/itdr/adding-issue-active-directory-issue-safelist) and [Adding an Issue to the Entra ID Issue Safelist](/itdr/adding-issue-entra-id-issue-safelist).
-
The page description of the Identity Posture and Entra ID dashboards were updated to show the statistics of the total number of identities assessed and identities affected by issues.
[See image.](#itdr-rn-ad-page-desc)
To learn more, see [About the Identity Posture Dashboard](/itdr/about-identity-posture-dashboard).
[See image.](#itdr-entra-id-page-desc)
To learn more, see [About the Entra ID Dashboard](/itdr/about-entra-id-dashboard).
-
The LDAP Activity module in Active Directory Threat Detection Policies was renamed to Suspicious LDAP Activity.
[See image.](#itdr-rn-ladp-activity-renamed)
To learn more, see [About Threat Detection Policies](/itdr/about-threat-detection-policies) and [Creating a Threat Detection Policy](/itdr/creating-threat-detection-policy).
-
The AD Threat Detection option was added under ITDR > Dashboard that redirects to the Investigate dashboard with the ITDR-specific filter applied to the alerts.
[See image.](#itdr-rn-ad-treat-detection-filter)
![View AD posture scan report](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-ad-posture-scan-report.png)
[]
[]![View MITRE ATT&CK Kill Chain](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-mitre-attack-tactic-reorder-1.png)
[]![View AD issue details and recommendations](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-detailed-findings-recommendations-ad.png)
[]![View Entra ID issue details and recommendations](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-entra-id-detailed-findings-recommendations-1.png)
[]![Details and Recommendations Page](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-add-issue-tosafelist-button.png)
[]![View AD Identity Posture dashboard page description](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-ad-posture-page-description-1.png)
[]![View Entra ID dashboard page description](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-entra-id-dashboard-page-description-1.png)
[]![AD Threat Detection Policy Modules](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-ladp-activity-renamed.png)
[]![AD Threat Detection Filter Option](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-ad-threat-detection.png)

### Feature Available
#### View Exposed Endpoint Credentials for an Affected Active Directory User
You can view exposed endpoint credential details for an affected Active Directory (AD) user account. For each exposed credential, you can view details such as type of risk, severity level, MITRE ATT&CK ID and tactics, issue impact, remediation, etc. You can analyze the risk to further investigate and remediate it.
[See image.](#itdr-rn-ad-user-credential-exposure-tab)
To learn more, see [Viewing Affected Active Directory User Account Details](/itdr/viewing-affected-active-directory-user-account-details) and [About the Endpoint Credential Exposure Dashboard](/itdr/about-endpoint-credential-exposure-dashboard).
[]![View exposed credential details for the AD user account](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-ad-user-credential-exposure.png)

## July 08, 2024
### Feature Available
#### ITDR Notifications
The ITDR Notifications feature enables you to configure email notifications to keep you informed about the vulnerabilities present in your identity infrastructure (Active Directory (AD), Entra ID, etc.) and endpoints. After AD domains, Entra ID tenants, and endpoints are scanned for vulnerabilities, the configured recipients receive emails with executive summary reports or bad changes details. Receiving emails helps you to stay updated on the critical risks present in your identity platforms. You can analyze the reports to prioritize and remediate issues.
[See image.](#itdr-rn-notifications)
To learn more, see [About Notifications](/itdr/about-notifications).
[]![itdr-release-notes-notifications.png](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-notifications.png)

### Feature Available
#### Safelists Relocation and UI Changes
All safelists were moved from the Settings module to ITDR > Settings along with some UI label changes:
- Active Directory Posture Safelist was renamed to Active Directory Issue Safelist.
- Change Detection Safelist was renamed to AD Change Detection Issue Safelist.
- Entra ID Posture Safelist was renamed to Entra ID Issue Safelist.
The following table compares the UI location changes before and after this update:
| Old Location | New Location |
| ------------ | ------------ |
| Settings > ITDR Safelist > Active Directory Posture Safelist | ITDR > Settings > Active Directory Issue Safelist |
| Settings > ITDR Safelist > Active Directory Object Safelist | ITDR > Settings > Active Directory Object Safelist |
| Settings > ITDR Safelist > Change Detection Safelist | ITDR > Settings > AD Change Detection Issue Safelist |
| Settings > Entra ID > Entra ID Posture Safelist | ITDR > Settings > Entra ID Issue Safelist |
| Settings > Entra ID > Entra ID Object Safelist | ITDR > Settings > Entra ID Object Safelist |
| Settings > Entra ID > Entra ID Change Detection Safelist | ITDR > Settings > Entra ID Change Detection Issue Safelist |
[See image.](#itdr-settings)
[]
![A screenshot highlighting the location of safelists in the ITDR menu](/sites/default/files/downloads/itdr/safelist/active-directory-posture-safelist/adding-issue-active-directory-posture-safelist/itdr-rn-settings-safelists.png)

## June 05, 2024
### Feature Available
#### Enable or Disable Scan Types in Credential Exposure Scan
You can scan the endpoints for credential exposure to identify exposed credential vulnerabilities and potential privilege escalation attack paths. After you configure an [endpoint credential exposure scan](/itdr/configuring-endpoint-credential-exposure-scan), you can enable or disable scan types that run on the endpoints to identify exposed credentials.
[See image.](#itdr-rn-enable-disable-scan-type)
To learn more, see [About Endpoint Credential Exposure Scan](/itdr/about-endpoint-credential-exposure-scan) and [Enabling or Disabling Scan Types in Credential Exposure Scan](/itdr/enabling-or-disabling-scan-types-credential-exposure-scan).
[]![Enable or disable scan types](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-endpoint-credential-scan-types-enable-disable.png)

### Feature Available
#### Enhancements to Endpoint Credential Exposure
The Endpoint Credential Exposure feature is enhanced to provide the following capabilities to investigate issues and swiftly remediate the compromised endpoints:
-
View exposed credential details grouped by MITRE ATT&CK techniques.
[See image.](#itdr-rn-cred-expo-mitre-attack)
To learn more, see [Viewing Exposed Endpoint Credential Issues Grouped by MITRE ATT&CK Techniques](/itdr/viewing-exposed-credential-grouped-mitre-attack-techniques).
-
View the privilege escalation attack paths for all exposed endpoint credentials.
[See image.](#itdr-rn-expo-cred-privilege-attack-path)
To learn more, see [Viewing Privilege Escalation Attack Paths for Exposed Endpoint Credentials](/itdr/viewing-privilege-escalation-attack-paths-exposed-endpoint-credentials).
-
View the details of all the identities storing exposed credentials.
[See image.](#itdr-rn-expo-cred-identities)
To learn more, see [Viewing Identities with Exposed Endpoint Credentials](/itdr/viewing-identities-endpoint-exposures).
[]![View endpoint exposure credential details grouped by MITRE ATT&CK techniques ](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-endpoint-credentials-by-mitre-attack.png)
[]![View privileged escalation paths for exposed endpoint credentials](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-endpoint-credentials-privilege-escalation.png)
[]![View identities with exposed credentials](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-itdr-endpoint-credentials-identities.png)

### Feature Available
#### Identity Risk Summary
The Identity Risk Summary dashboard collates top or critical misconfigurations and vulnerabilities from various identity management solutions, such as Active Directory (AD), Microsoft Entra ID, etc. It also identifies the top endpoint credential exposures contributing to identity risk posture. The dashboard aggregates the risk factors and offers an identity risk snapshot of the environment. You can also view mappings to security risk frameworks like MITRE ATT&CK. The interactive widgets help you to view your entire identities' risk profile, drill down to top critical risks, and remediate the issues instantly to improve the risk score.
[See image.](#itdr-rn-risk-summary-page)
To learn more, see [About the Identity Risk Summary Dashboard](/itdr/about-identity-risk-summary-dashboard).
[]![The Identity Risk Summary page](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-risk-summary-dashboard-3.png)

### Feature Available
#### ITDR – Microsoft Entra ID
Zscaler ITDR enables you to run posture checks on your Microsoft Entra ID tenant at a set frequency. These checks identify misconfigurations and possible risks in the Entra ID tenant. After the tenant is assessed for vulnerabilities, the results are displayed on a dashboard for further investigation and remediation.
Entra ID Tenant Configuration
You can connect an Entra ID tenant and run a scan from the Entra ID configuration page (ITDR > Manage > Entra ID).
[See image.](#itdr-entra-id-tenant-details)
To learn more, see [Connecting an Entra ID Tenant with the Zscaler ITDR Admin Portal](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal).
After connecting an Entra ID tenant, ITDR runs scan for posture checks and change dectections in an Entra ID. You can manually trigger a new scan and enable or disable a scan for an Entra ID tenant from the Entra ID configuration page (ITDR > Manage > Entra ID).
[See image.](#itdr-entra-id-actions-scan)
To learn more, see [Triggering an On-Demand Scan](/itdr/triggering-demand-scan-entra-id)[.]
Entra ID Dashboard
After your Entra ID tenants are scanned for misconfigurations, the results are available on the Entra ID dashboard (ITDR > Dashboard > Entra ID). The dashboard displays the unified risk score for the tenant, top vulnerability issues by severity, top vulnerability issues by risk type, affected identities, issues mapped on the MITRE ATT&CK kill chain, etc. You can also view and download executive summary and vulnerability reports. On the dashboard, you can view active changes detected in your Entra ID tenant that provide near real-time visibility of new misconfigurations and security risks introduced. You can interactively drill down to a specific issue and analyze it.
[See image.](#itdr-rn-entra-id-dashboard)
To learn more, see [About the Entra ID Dashboard](/itdr/about-entra-id-dashboard).
Entra ID Change Detection
The Entra ID Change Detection page (ITDR > Dashboard > Entra ID Change Detection) provides near real-time visibility into new misconfigurations and security risks introduced to your Entra ID tenant. The impact of the changes are classified as good, bad, or info. You can view additional issues and remediation details.
[See image.](#itdr-rn-entra-id-change-detection-dashboard)
To learn more, see [About the Entra ID Change Detection Dashboard](/itdr/about-entra-id-change-detection-dashboard).
Entra ID Safelist
You can add, view, and manage Entra ID posture issues, objects, and change detection issues as safe if they do not pose or contribute to the risk posture of the Entra ID tenant. The safelists are managed separately for posture issues, objects, and change detection issues respectively.
Entra ID Posture Safelist
You can view and manage the Entra ID Posture Safelist from the Entra ID Posture Safelist page (Settings > Entra ID Safelist > Entra ID Posture Safelist).
[See image.](#entra-id-posture-safelist-ui)
To learn more, see [About the Entra ID Posture Safelist](/itdr/about-entra-id-posture-safelist), [Adding an Issue to the Entra ID Posture Safelist](/itdr/adding-issue-entra-id-posture-safelist), and [Deleting an Issue from the Entra ID Posture Safelist](/itdr/deleting-issue-entra-id-posture-safelist).
Entra ID Object Safelist
You can view and manage the Entra ID Object Safelist from the Entra ID Object Safelist page (Settings > Entra ID Safelist > Entra ID Object Safelist).
[See image.](#entra-id-object-safelist-ui)
To learn more, see [About the Entra ID Object Safelist](/itdr/about-entra-id-object-safelist), [Adding an Issue to the Entra ID Object Safelist](/itdr/adding-entra-id-object-safelist), and [Deleting an Issue from the Entra ID Object Safelist](/itdr/deleting-object-entra-id-object-safelist).
Entra ID Change Detection Safelist
You can view and manage the Entra ID Change Detection Safelist from the Entra ID Change Detection page (Settings > Entra ID Safelist > Entra ID Change Detection Safelist).
[See image.](#entra-id-change-detection-safelist-ui)
To learn more, see [About the Entra ID Change Detection Safelist](/itdr/about-entra-id-change-detection-safelist), [Adding an Issue to the Entra ID Change Detection Safelist](/itdr/adding-change-detection-issue-entra-id-change-detection-safelist), and [Deleting an Issue from the Entra ID Change Detection Safelist](/itdr/deleting-issue-entra-id-change-detection-safelist).
[]![View the Entra ID Dashboard](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-entra-id-dashboard-3.png)
[]![View the Entra ID Change Detection dashboard](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-entra-id-change-detection-1.png)
[]![A screenhost capturing the Entra ID Posture Safelist](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/rn-itdr-entra-id-posture-safelist.png)
[]![A screenshot capturing the Entra ID Object Safelist](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/rn-itdr-entra-id-object-safelist.png)
[]![A screenshot of Entra ID Change Detection Safelit Page](/sites/default/files/downloads/itdr/scan-configuration/entra-id-posture-scan/connecting-entra-id-tenant-zscaler-itdr-admin-portal/rn-itdr-entra-id-changedetection-safelist.png)
[]![A screenshot capturing the Tenant Details window](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-tenant-details.png)
[]
![rn-itdr-options-scan-entra-id_0.png](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/rn-itdr-options-scan-entra-id_0.png)

### Feature Available
#### View Exposed Endpoint Credential Details by Exposure Type
You can view the total number of exposed endpoint credential risks for each exposure or scan type on the All Exposures page (ITDR > Dashboard > Endpoint Credential Exposure > All Exposures) for a particular scan date. For each exposure or scan type, you can drill down to a particular risk and view its details, such as system name, username, identities, privilege escalation paths, etc.
[See image.](#itdr-release-notes-all-exposure)
To learn more, see [About the Endpoint Credential Exposure Dashboard](/itdr/about-endpoint-credential-exposure-dashboard) and [Viewing Credential Exposure Risk Details by Scan Type](/itdr/viewing-endpoint-credential-exposure-issues).
[]![View exposed credentials for all exposure types](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-release-notes-endpoint-credentials-all-exposures-1.png)

## April 17, 2024
### Feature Available
#### Containment Integration for Identity Threat Protection with Okta AI
You can integrate Zscaler ITDR with Okta to push user risk scores by leveraging the Shared Signals Framework (SSF). With this integration, ITDR pushes user risk scores to Okta for users based on threat detection events. Based on the risk score and Okta policies, Okta can end the user’s sessions, prompt a Multi-Factor Authentication (MFA) challenge, or invoke a workflow to restore your organization's security posture.
[See image.](#zd-rn-okta-ssf)
To learn more, see [Containment Configuration Guide for Identity Threat Protection with Okta AI](/itdr/containment-configuration-guide-identity-threat-protection-okta-ai)[.]
[]
![A screenshot capturing the Okta (SSF) window](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zscaler-deception-okta-base-url.png)

### Feature Available
#### Download Endpoint Credential Exposure Scan Data
You can download endpoint credential exposure scan data to your local system as a .zip file containing CSV files for each credential exposure issue. Each CSV file contains details corresponding to the exposure type.
[See image.](#ece-report)
To learn more, see [Downloading Endpoint Credential Exposure Scan Data](/itdr/downloading-endpoint-credential-exposure-scan-report).
[]![Download Credential Exposure Scan Data](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-itde-ece-download-ece-csv-data.png)

### Feature Available
#### Download the Credential Exposure Executive Report
You can download the Credential Exposure Executive report in PDF format from the [Endpoint Credential Exposure Dashboard](/itdr/about-endpoint-credential-exposure-dashboard). This report provides an abstract of credential exposure and vulnerabilities that exist on your endpoints. The report displays the summary of all the endpoints assessed, the average number of credentials exposed per user, and the hosts that are are vulnerable to privilege escalation. The report highlights the misconfigurations that have the highest impact. You can leverage this report to identify credential exposure risks, prioritize what issue to focus on first, and mitigate issues before the credentials are compromised.
[See image.](#itdr-rn-download-credential-exp-report)
To learn more, see [About the Endpoint Credential Exposure Dashboard](/itdr/about-endpoint-credential-exposure-dashboard), [Downloading the Endpoint Credential Exposure Executive Report](/itdr/downloading-endpoint-credential-exposure-executive-report), and [Understanding the Credential Exposure Summary Report](/itdr/understanding-credential-exposure-summary).
[]![Credential Exposure Summary report](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-zscaler-itdr-credential-exposure-summary.png)

### Feature Available
#### Endpoint Credential Exposure Error Logs
You can view error logs of a failed or partially completed endpoint credential exposure policy scan of an endpoint agent on the Agents page.
[See image.](#error-logs)
To learn more, see [About Endpoint Agents](/itdr/about-endpoint-agents).
[]![View Credential Exposure error logs](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-itdr-v4.22-ece-error-logs.png)

### Feature Available
#### Okta Threat Detection
You can view the Okta identity system logs across Okta that are identified as potentially suspicious under the Okta tab on the Threats page.
[See image.](#threat-okta)
To learn more, see [Viewing Affected Active Directory User Account Details](/itdr/viewing-affected-active-directory-user-account-details).
[]![View Okta identity system logs in ITDR](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-itdr-threat-detection-okta.png)

### Feature Available
#### Removal of Phone and Text Message Notifications
Zscaler ITDR no longer supports phone and text message notifications. As a result, the following changes were made across the Zscaler ITDR Admin Portal:
-
Under Orchestrate > Rules, the Phone and SMS notification options were removed from the Rule Details window.
[See image.](#rules-notify)
-
Under Orchestrate > Event Templates, the phone and text message notification template options were removed.
[See image.](#itdr-rel-notes-event-templates)
-
Under Settings > Users, the phone field was removed from the User Details window.
[See image.](#itdr-rel-notes-add-user-details)
To learn more, see [Adding a User](/itdr/adding-user).
-
Under Account Settings > Profile, the phone field was removed from the Edit Profile section.
[See image.](#itdr-rel-notes-edit-your-profile)
To learn more, see [Editing the User Profile](/itdr/editing-user-profile).
[]![Customize the email notification template](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-itdr-customize-event-template.png)
[]![Configure a new user account](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/release-notes-zscaler-deception-user-details-2.png)
[]![Edit your user profile](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/release-notes-zscaler-deception-edit-user-profile-1.png)
[]![Orchestrate Rule Details window](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-itdr-orchestrate-rules-notification.png)

### Feature Available
#### User Interface Changes and Enhancements
The following user interface changes and enhancements were made to the Zscaler ITDR Admin Portal:
-
On the Agent Update Groups page (Settings > Endpoint Settings > Agent Update Groups), the Agent Group window was renamed to Agent Update Group Details.
[See image.](#itdr-rn-ui-lable-agent-group)
To learn more, see [About Agent Update Groups](/itdr/about-agent-update-groups).
-
On the Affected Active Directory (AD) Computer Details page (Identity Posture dashboard > Top 10 Users and Computers > Computer), the Okta, ZPA, and ZIA tiles were removed as they are not applicable to AD computer objects.
[See image.](#ad-computer)
To learn more, see [Viewing Affected Active Directory Computer Details](/itdr/viewing-affected-active-directory-computer-details).
[]
![A screenshot highlighting the UI label Change in Agent Update Group Page](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/itdr-rn-agent-update-groups.png)
[]![Viewing the affected AD computers](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-identity-dashboard-AD-computers.png)

## February 14, 2024
### Feature Available
#### Affected Active Directory User and Computer Details
The affected Active Directory (AD) user and computer details page provides correlated identity vulnerability details of user accounts and computer objects in an AD. You can view information such as failed posture checks, associated Okta user account details, recent suspicious changes made to the user account, detected potential identity attacks or threats, and ZIA and ZPA access snapshots. You can further investigate the issues and swiftly remediate the compromised AD user or computer to disrupt the attacker's operations.
[See image.](#itdr-release-notes-view-ad-affected-user)
To learn more, see [Viewing Affected Active Directory User Details](/itdr/viewing-affected-active-directory-user-details).
[See image.](#itdr-release-notes-affected-ad-comp-details)
To learn more, see [Viewing Affected Active Directory Computer Details](/itdr/viewing-affect-active-directory-computer-details).
[]![View the affected AD user details](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-viewing-ad-user-details_0.png)
[]![View affected AD computer details](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-viewing-ad-computer-details.png)

### Feature Available
#### Configure Safe Processes Using Regular Expressions
You can add safe processes to Zscaler ITDR using regular expressions. This allows you to configure a single safe process that accommodates multiple different processes by matching a specific pattern of strings in the process names.
[See image.](#safe-process-regex)
To learn more, see [Configuring a Safe Process](/itdr/configuring-safe-process).
[]![Configuring safe process using regular expressions](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-itdr-selection-type-regex.png)

### Feature Available
#### Endpoint Credential Exposure
The Endpoint Credential Exposure feature enables you to identify exposed credentials, API tokens, and identity-related data and potential privilege escalation points on your endpoints to prevent exploitation and disrupt lateral movements.
Endpoint Credential Exposure Scan
You can scan the endpoints for credential exposure to identify exposed credentials and vulnerabilities from various sources such as browser, credential managers, registries, plain text files, memory, etc.
[See image.](#credential-scan)
To learn more, see [About Endpoint Credential Exposure Scan](/itdr/about-endpoint-credential-exposure-scan)[.]
Endpoint Credential Exposure Dashboard
After your endpoints are scanned for credential exposure, you can view the results on the Endpoint Credential Exposure dashboard. The dashboard displays the overview of the exposure to include the total number of endpoints scanned, average credentials per user, and total number of identities with exposed credentials. It also displays the top 3 vulnerabilities that should take priority. You can analyze the issues in detail and remediate them.
[See image.](#dashboard)
To learn more, see [About the Endpoint Credential Exposure Dashboard](/itdr/about-endpoint-credential-exposure-dashboard).
[]![Viewing the Endpoint Credential Exposure scan page](/sites/default/files/downloads/itdr/about-endpoint-credential-exposure-scan/itdr-endpoint-credential-exposure-scan.png)
[]![Viewing the Endpoint Credential Exposure dashboard](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-endpoint-credential-exposure-dashboard.png)

### Feature Available
#### Enhancement to Endpoint Agents
On the Agents page (Settings > Endpoint Settings > Agents), a Show all agents toggle was added under the Actions drop-down menu. This allows you to view a list of active and inactive endpoint agents in the Agents table.
[See image.](#show-all-agents)
To learn more, see [About Endpoint Agents](/itdr/about-endpoint-agents).
[]![Show all the endpoint agents](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-itdr-show-all-agents.png)

### Feature Available
#### Investigate
The Investigate module provides information on all [threat detection](/itdr/about-threat-detection) events generated in Zscaler ITDR, along with corresponding endpoints in an interactive graphical view. The graphical representation also shows how all components are connected with the Zscaler ITDR Admin Portal. You can use filters to show events based on timelines, or you can use queries.
[See image.](#zd-rn-itdr-dashboard)
For each event shown in the ITDR dashboard, you can perform the following actions:
- Contain with Zscaler Internet Access (ZIA)
- Contain with Zscaler Private Access (ZPA)
- Mark as safe
- Add to blocklist
- Delete an event
[See image.](#zd-rn-itdr-actions-dashboard)
In addition, you can also view extended details for each component that include:
- ThreatParse: Provides information on all attacks based on MITRE framework reconstructed in natural English.
- Chronology: Provides a temporal overview of events and a heatmap of the activities.
- Event Logs: Provides log information for all events associated with the selected component.
[See image.](#zd-rn-itdr-dashboard-extended-details)
[]
![A screenshot capturing the ITDR dashboard](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zd-rn-investigate.png)
[]
![A GIF capturing the various actions in ITDR Dashboard](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zd-rn-investigate-actions.gif)
[]
![A screenshot capturing Extended Details in ITDR Dashboard](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2024/zd-rn-investigate-extended-details.png)

### Feature Available
#### ITDR Integrations
Zscaler ITDR integrates seamlessly with third-party security solutions to view identity metadata, identify real-time changes, forward attackers' identities, and isolate attackers.
Okta
You can integrate ITDR with Okta to view Okta identity metadata, identify real-time changes, and perform actions on an Okta identity in the Zscaler ITDR Admin Portal.
[See image.](#itdr-okta-integration)
To learn more, see [Integrating Okta with ITDR](/itdr/integrating-itdr-okta) and [Viewing Affected Active Directory User Account Details](/itdr/viewing-affected-active-directory-user-details).
Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA)
You can integrate ITDR with ZIA and ZPA to gain insights into traffic violations or bad activities on ZIA or ZPA services for the Active Directory user account. You can also contain an attack or threat and forward the attack details to ZIA or ZPA to take further actions according to the defined policy.
[See image.](#zia-zpa-accessrisk)
To learn more, see [Containment Configuration Guide for Zscaler Internet Access (ZIA)](/itdr/containment-configuration-guide-zscaler-internet-access-zia), [Containment Configuration Guide for Zscaler Private Access (ZPA)](/itdr/containment-configuration-guide-zscaler-private-access-zpa), and [Viewing Affected Active Directory User Account Details](/itdr/viewing-affected-active-directory-user-details)[.]
[]![Integrating ITDR with Okta](/sites/default/files/downloads/itdr/integrating-itdr-okta/itdr-integration-with-okta.png)
![Viewing Okta account details](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-itdr-okta-integration.png)
[]![ZIA insights in ITDR](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/zscaler-itdr-affected-ad-user-access-risk-zia-tab.png)
![ZPA insights in ITDR](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/zscaler-itdr-affected-ad-user-access-risk-zpa-tab.png)

### Feature Available
#### Orchestrate
The Orchestrate feature enables Zscaler ITDR integration with leading security solutions to:
- Create and manage rules that automate workflows, notifications, and containment in response to threat detection.
- Create and manage API tokens and event notification templates.
- Integrate ITDR with leading security solutions to:
- Transmit event logs in real time.
- Contain threats to isolate active attackers.
- Enrich security events with relevant contextual information to manage security threats efficiently.
[See image.](#itdr-release-notes-orchestrate-menu)
[]![ITDR Orchestrate Menu](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-zscaler-itdr-orchestrate.png)

### Feature Available
#### User Interface Changes and Enhancements
The following user interface changes and enhancements were made across the ITDR Admin Portal:
| **Old** | **New** |
| ------- | ------- |
| ITDR > Dashboard > ITDR Posture - Active Directory Dashboard | ITDR > Dashboard > Identity Posture |
| ITDR > Scan Agents | ITDR > Manage > Active Directory Posture |
| Deceive > Landmine Agents > Agents | Settings > Endpoint Settings > Agents |
| Deceive > Landmine Agents > Settings | Settings > Endpoint Settings > Agent Configuration |
| Deceive > Landmine Agents > Update Phase Groups | Settings > Endpoint Settings > Agent Update Groups |
| Deceive > Landmine Agents > Safe Processes | Settings > Endpoint Settings > Safe Processes |
| ITDR > ITDR - Active Directory > Issue Safelist | Settings > ITDR Safelist > Active Directory Posture Safelist |
| ITDR > ITDR - Active Directory > Object Safelist | Settings > ITDR Safelist > Active Directory Posture Safelist |
| ITDR > ITDR - Active Directory > Change Detection Safelist | Settings > ITDR Safelist > Change Detection Safelist |
[See image.](#dashboard-settings-changes)
To learn more, see [About the Identity Posture Dashboard](/itdr/about-itdr-posture-active-directory-dashboard), [About Active Directory Posture](/itdr/about-scan-agents), and [About Settings](/itdr/about-settings).
[]![Viewing the ITDR Settings](/sites/default/files/downloads/itdr/release-notes/release-upgrade-summary-2024/release-notes-itdr-about-settings.png)
