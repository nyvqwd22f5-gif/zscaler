# Release Upgrade Summary (2023)
Source: https://help.zscaler.com/itdr/release-upgrade-summary-2023

This article provides a summary of all new features and enhancements for Zscaler ITDR. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).

**Clouds:** illusionblack.com
The following service updates were deployed to illusionblack.com on

## November 02, 2023
### Feature Available
#### Change Detection Safelist
The ITDR - Change Detection feature monitors and detects active changes in an Active Directory (AD) domain, and classifies these changes as a good or bad impact. The Change Detection (ITDR > Change Detection) page displays the detected issues. You can review these change detection issues to confirm that they are not a risk and mark them as safe.
[See image.](#deception-release-notes-change-detection-safelist)
To learn more, see [About ITDR - Change Detection](/deception/adding-change-detection-issue-safelist), [Adding a Change Detection Issue to the Safelist](/deception/adding-change-detection-issue-safelist), and [Viewing Change Detection Issue and Remediation Details](/deception/viewing-change-detection-issue-and-remediation-details).
[]![Add a change detection issue to safelist](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-itdr-change-detection-safelist.png)

### Feature Available
#### ITDR Active Directory Assessment Posture Report
The ITDR Active Directory (AD) Assessment Posture report is a summary of potential misconfigurations and vulnerabilities in your scanned AD domain. The report displays a unified domain risk score on a scale of 0 to 100, the type of risks most prevalent in the AD, an issue priority matrix, and remediation guidance to fix the issues. You can download the ITDR AD Assessment Posture report as a PDF file.
[See image.](#deception-release-notes-itdr-ad-assessment-report)
To learn more, see [Viewing the ITDR AD Assessment Report](/deception/viewing-itdr-active-directory-assessment-report) and [Downloading the ITDR AD Assessment Report](/deception/downloading-itdr-active-directory-assessment-report).
[]![View the ITDR AD Assessment Report](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-itdr-ad-assessment-report.png)

### Feature Available
#### ITDR UI Enhancements
-
The Identity label on the left-side navigation menu was renamed to ITDR.
[See image.](#deception-release-notes-itdr-navigation)
-
The Identity Posture - Active Directory Dashboard page (Identity > Dashboard) was renamed to ITDR Posture - Active Directory Dashboard (ITDR > Dashboard).
[See image.](#deception-release-notes-itdr-dashboard)
To learn more, see [About the ITDR Posture - Active Directory Dashboard](/deception/about-itdr-posture-active-directory-dashboard).
[]![ITDR navigation menu](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-itdr-navigation-menu.png)
[]![ITDR - Posture Active Directory Dashboard](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-itdr-posture-ad-dashboard.png)

### Feature Available
#### Viewing Active Directory Failed Scan Check Details
After an Active Directory (AD) domain is scanned and the scan status is completed, you can view the details of the failed scan checks, if any.
[See image.](#deception-release-notes-view-failed-scan-checks)
To learn more, see [About Scan Agents](/deception/about-scan-agents).
[See image.](#deception-release-notes-view-failed-scan-checks-details)
To learn more, see [Viewing Failed Scan Check Details](/deception/viewing-failed-scan-check-details).
[]![View failed scan checks details](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-view-failed-scan-checks.png)
[]![View failed scan checks details](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-view-failed-scan-checks-details-1.png)

## August 31, 2023
### Feature Available
#### Active Directory Attack Detection
You can create a Windows landmine policy and configure the ITDR - Active Directory (AD) attack detection module to detect credential misuse, entitlement exposures, and privilege escalation activities against AD via the Landmine Agent.
[See image.](#deception-release-notes-itdr-ad-module)
To learn more, see [Creating a Landmine Policy](/deception/creating-landmine-policy) and [Configuring ITDR - Active Directory](/deception/configuring-identity-threat-detection-response-active-directory).
[]![Configure the ITDR - Active Directory Attack Detection Deception module](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-itdr-attack-detection-1.png)

### Feature Available
#### Identity Posture - Active Directory
The Identity Posture - Active Directory feature enables organizations to protect privileged identities, such as Active Directory (AD) domains that are at a high risk of exploitation and regulatory noncompliance. It helps you to detect attacks, such as DYSync, DCShadow, Kerberoast, etc., and disrupt privilege escalation and lateral movement threats with decoy users and computers.
Scan Active Directory Domains
You can scan AD domains via a Microsoft Windows landmine agent to discover identity vulnerabilities, such as AS-REP roasting and kerberoasting attacks.
[See image.](#deception-release-notes-add-scan)
To learn more, see [About Scan Agents](/deception/about-scan-agents-page) and [Scanning an Active Directory](/deception/scanning-active-directory).
Identity Posture - Active Directory Dashboard
After your AD domains are [scanned](/deception/scanning-active-directory), the results are available on the Identity Posture - Active Directory dashboard. The dashboard displays the top vulnerability issues by severity, affected users and computers, risk analysis with issues categorized by percentage, issues mapped on the MITRE ATT&CK kill chain, etc. You can interactively drill down to a specific issue and analyze it.
On the dashboard, you can view active changes detected in your AD that provide near real-time visibility of new misconfigurations and security risks introduced.
The dashboard displays remediation steps that you can take to maintain the security posture of your AD infrastructure. You can also view and download the vulnerability reports.
[See image.](#deception-release-notes-identity-posture-dashboard)
To learn more, see [About the Identity Posture - Active Directory Dashboard](/deception/about-identity-posture-active-directory-dashboard).
Issue and Object Safelist
After your AD domain is [scanned](/deception/scanning-active-directory), the vulnerability issues and objects (AD user accounts and computers) are listed on the [Focus Area](/deception/viewing-focus-area-details) page. You can review these issues and objects to confirm that the vulnerability is not a risk and mark them as safe. The issues and objects marked as safe are listed on the Issue Safelist and Object Safelist pages.
[See image.](#deception-release-notes-itdr-issue-safelist)
To learn more, see [Adding a Vulnerability Issue to the Safelist](/deception/adding-vulnerability-issue-safelist) and [Viewing and Managing Issue Safelist](/deception/viewing-managing-issue-safelist).
[See image.](#deception-release-notes-itdr-object-safelist)
To learn more, see [Adding an Active Directory Object to the Safelist](/deception/adding-object-safelist) and [Viewing and Managing Active Directory Object Safelist](/deception/viewing-managing-active-directory-object-safelist).
ITDR - Change Detection
The ITDR - Change Detection feature improves the security posture of an Active Directory (AD) environment. It provides near real-time visibility into new misconfigurations and security risks introduced to your AD.
[See image.](#deception-release-notes-itdr-change-detection)
To learn more, see [About ITDR - Change Detection](/deception/about-identity-threat-detection-and-response-change-detection).
[]![The Scan Agents page](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-about-scan-agents-1.png)
[]![Identity Posture - Active Directory dashboard](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-about-scan-itdr-dashboard-2.png)
[]![View vulnerability issue safelist](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-itdr-issue-safelist.png)
[]![View AD object safelist](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-itdr-object-safelist.png)
[]![ITDR - Change Detection](/sites/default/files/downloads/deception/release-notes/release-upgrade-summary-2023/release-notes-zscaler-deception-itdr-change-detection.png)
