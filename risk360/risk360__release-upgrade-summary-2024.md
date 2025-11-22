# Release Upgrade Summary (2024)
Source: https://help.zscaler.com/risk360/release-upgrade-summary-2024

This article provides a summary of all new features and enhancements for Risk360.

**Clouds:** zscalerrisk.net
The following service updates were deployed to zscalerrisk.net on

## December 09, 2024
### Feature Available
#### New Factors Added for Compromise
The Compromise category is updated with 15 factors under the following new factor groups:
- Identity Protection: Active Directory
- Identity Protection: Entra ID
- Identity Protection: Credential Exposure
To learn more, see [About Factors](/risk360/about-factors).

## November 26, 2024
### Feature Available
#### Enhanced Alerts
The Alerts feature is enhanced with the following updates in the Risk360 Admin Portal:
-
The table in the Ongoing Alerts tab shows the alert ID and mute status of the alert rule.
[See image.](#alerts-page)
- The table in the Alerts History tab shows the alert ID of the alert rule.
-
The Ongoing Alert drawer shows the alert trigger cause history and the change at various levels (i.e., organization, category, factor group, and factor).
[See image.](#alerts-drawer)
-
5 predefined customizable rule templates are added to the Add Alert Rule wizard.
[See image.](#template)
To learn more, see [About Alerts](/risk360/about-alerts) and [Configuring an Alert Rule](/risk360/configuring-alert-rule).
[]![Alerts Page](/sites/default/files/downloads/zia/authentication-administration/administrator-role-management/administrators/about-administrators/Risk360-Alerts.png)
[]![Alerts Drawer](/sites/default/files/downloads/zia/authentication-administration/administrator-role-management/administrators/about-administrators/Risk360-Alerts-drawer.png)
[]![Alert Rule Template Wizard](/sites/default/files/downloads/zia/authentication-administration/administrator-role-management/administrators/about-administrators/Risk360-Alerts-Templates.png)

## November 15, 2024
### Feature Available
#### Enhancments to Asset Details
The Events Contributing to Risk Score for Last 7 Days** **section on the Asset Details page is enhanced with the following updates:
- For each risky event, you can view the:
- Threat Category
- Threat Name
- URL Category
- URL Name
- Export all events contributing to the risk score change to a CSV file.
- View all events contributing to the risk score change in a drawer by clicking View All Events.
[See image.](#events-img)
To learn more, see [Analyzing an Asset Risk](/risk360/analyzing-asset-risk).
[]![Events Contributing to RIsk Score for Last 7 Days EVents Contributing to Risk Score for Last 7 Days](/sites/default/files/downloads/tech-pubs-drafts/risk360-draft-articles/analyzing-asset-risk/Risk360-Asset-Details-Page-Events.png)

## November 13, 2024
### Feature Available
#### Ability to Include or Exclude Items For Risk Computation
You can include or exclude individual items (i.e., servers and vulnerabilities) from risk score computation from the Investigate page. The changes are captured in the [audit logs](/risk360/about-audit-logs) with the username and reason provided for the action.
[See image.](#include-option)
To learn more, see [Investigating Sections of a Problem](/risk360/investigating-sections-problem).
[]![Inculde Option Investigate Page](/sites/default/files/downloads/tech-pubs-drafts/risk360-draft-articles/investigating-sections-problem/Risk360-Investigate-page.png)

## October 31, 2024
### Feature Available
#### Support to Scan Multiple Domains for External Surface Attack
You can add multiple domains in the Risk360 Admin Portal to scan and identify publicly exposed assets for quantifying risk and mitigating potential cyberattacks. The risk assessed is visualized in the form of risk [factors](/risk360/about-factors) which can be further drilled down to the [investigate](/risk360/investigating-sections-problem) page.
[See image.](#seeds-management)
To learn more, see [About Seeds Management](/risk360/about-seeds-management), [Adding Domains Using a CSV](/risk360/adding-domains-using-csv), and [Adding a Domain for External Attack Surface Analysis](/risk360/adding-domain-external-attack-surface-analysis).
[]![Seeds Management Page](/sites/default/files/downloads/risk360/administration-authentication/about-seeds-management/Risk360-Seeds-Management-Page.png)

## September 10, 2024
### Feature Available
#### Investigate with Decoy Domains
You can filter and view data for Zscaler decoy domains within your network when [investigating problem cards](/risk360/investigating-sections-problem) under the External Surface Attack category.
[See image.](#zscaler-decoy)
[]![Zscaler Decoy? Field in the Investigate Page](/sites/default/files/downloads/business-insights/workplace-insights/analyzing-workplace-insights/Risk360-Zscaler-Decoy-Field.png)

## August 16, 2024
### Feature Available
#### Renamed Sub-factor under Advanced Threat Settings
The existing sub-factor, Kerberos Authentication Bypass for Certain URLs, under the Advanced Threat Settings factor is renamed to Custom Denylist Configuration for URLs.
[See image.](#denylist-factor)
To learn more, see [About Factors](/risk360/about-factors).
[]![Custom Denylist Configuration For URLs Factor](/sites/default/files/downloads/business-insights/reports/about-scheduled-reports/Risk360-denylist-factor.png)

## August 08, 2024
### Feature Available
#### New Factor for External Attack Surface
A new factor, SSL/TLS Certificate Expiration, is added to the External Attack Surface category that quantifies risk based on your organization's expired and soon-to-be expired SSL/TLS certificates.
[See image.](#ssl-expiration-factor-img)
[]![SSL/TLS Certification Expiration Factor](/sites/default/files/downloads/business-insights/workplace-insights/integrating-saas-application-workflow-automation/Risk360-SSL-Factor.png)

## July 19, 2024
### Feature Available
#### Support for NIST CSF 2.0
The Risk360 service supports NIST CSF 2.0 in the Risk360 Admin Portal.
[See image.](#nist-csf-2.0)
To learn more, see[ Analyzing Risk with NIST CSF](/risk360/analyzing-risk-nist-csf).
[]![Risk360-NIST-CSF-2.0.gif](/sites/default/files/downloads/business-insights/reports/about-scheduled-reports/Risk360-NIST-CSF-2.0.gif)

## July 05, 2024
### Feature Available
#### Alerting Support in Risk360
You can configure and receive alert notifications based on criteria defined in the alert rules as emails or webhooks.
[See image.](#alerts)
To learn more, see [About Alerts](/risk360/abouting-alerts), [Understanding Alert Email](/risk360/understanding-alert-email), and [ServiceNow Webhook Configuration Guide](/risk360/servicenow-webhook-configuration-guide).
[]![Alerts Page](/sites/default/files/downloads/risk360/servicenow-webhook-configuration-guide/Risk360-About-Alerts.png)

## July 01, 2024
### Feature Available
#### New Factors Added Under UEBA
The following new factors are added under the UEBA factor group, for the Data Loss category:
- Code Repository Made Public
- Code Repository Shared Externally
- Bulk Files Delete Operation
- Data Uploads to High-Risk Countries
[See image.](#ueba-factors)
[]![UEBA Factors](/sites/default/files/downloads/risk360/dashboard-analytics/about-factors/Risk360-UEBA-Factors.png)

## June 11, 2024
### Feature Available
#### Tenable Factors Support in Risk360
The Risk360 service supports integration with the Tenable Vulnerability Management solution to quantify the risk associated with the vulnerabilities in your organization. The Zscaler service calls the Tenable Vulnerability Management API to request various risk-related information, categorizes the risk under Risk360's External Attack Surface category, and quantifies risk by taking into account the common vulnerability scoring system (CVSS) score, vulnerability priority rating (VPR) score, exploit code maturity, and threat recency.
[See image.](#tenable-factors)
To learn more, see [Tenable Integration For Risk360 Factors](/risk360/tenable-integration-risk360-factors).
[]![Tenable Factors in Risk360 Admin Portal](/sites/default/files/downloads/risk360/dashboard-analytics/tenable-integration-risk360-factors/Risk360-Tenable-Factors_1.png)

## June 04, 2024
### Feature in Limited Availability
#### Support for Asset-Level Risk Scoring
You can view the risk score assigned to all your organization's assets and other important metrics in the Risk360 Admin Portal.
[See image.](#asset-risk)
To learn more, see [About Asset-Level Risk](/risk360/about-asset-level-risk) and [Analyzing an Asset Risk](/risk360/analyzing-asset-risk).
[]![Assets page](/sites/default/files/downloads/risk360/dashboard-analytics/about-asset-level-risk/Assets-Page.png)

## May 24, 2024
### Feature Available
#### Export Factors
You can export the factors contributing to your organization's risk score into a CSV file from the Factors page using the Export icon.
[See image.](#export-icon)
To learn more, see [About Factors](/risk360/about-factors).
[]![Export icon in Factors Page ](/sites/default/files/downloads/risk360/dashboard-analytics/about-factors/Risk360-Factors-Page-Export-Option.png)

## May 07, 2024
### Feature Available
#### Enhanced Posture Profile Card
The Posture Profile card (Insights > Posture Profile) in the Risk360 Admin Portal is enhanced with the following new widgets:
-
**Access Policies without Posture Profile**: This graph shows the trend for the number of access policies for the last 90 days.
[See image.](#profile-graph)
-
**5 Access Policies without Posture Profile**: This section shows the access policies without a posture profile for the last 7 days.
[See image.](#top-polices)
Click the Investigate link under these preceding widgets to view the data in a table for all access policies without a posture profile. You can filter the data using the filter options.
[See image.](#investigate-page)
[]![Access Policies without Posture Profile Graph](/sites/default/files/downloads/risk360/abouting-alerts/Risk360-access-policies-without-posture-profile-graph.png)
[]![5 Access Policies without Posture Profile](/sites/default/files/downloads/risk360/abouting-alerts/Risk360-5-access-policies-without-posture-profile_0.png)
[]![Investigate Access Policies without Posture Profile](/sites/default/files/downloads/risk360/abouting-alerts/Risk360-Investigate-acces-policies-without-posture-profile_0.png)

### Feature Available
#### Enhanced Segmentatation Card
The Segmentation card (Insights > Segmentation) in the Risk360 Admin Portal is enhanced with the following new widgets:
-
**Application Segments with Open Ports**: This graph shows the trend for open ports for the last 90 days.
[See image.](#app-graph)
-
**5 Sample Application Segments with Open Ports**: This table shows random application segments with open ports. The table consists of the following columns:
- Name
- Defined TCP Port Ranges
- Defined UDP Port Ranges
[See image.](#top-apps)
Click the Investigate link under these preceding widgets to view the data in a table for all application segments with open ports.
[See image.](#investigate)
[]![Application Segments with Open Ports](/sites/default/files/downloads/risk360/abouting-alerts/Risk360-application-segments-with-open-ports.png)
[]![5 Sample Application Segments with Open Ports](/sites/default/files/downloads/risk360/abouting-alerts/Risk360-5-application-segments-with-open-ports_0.png)
[]![Investigate Application Segments with Open Ports](/sites/default/files/downloads/risk360/abouting-alerts/Risk360-Investigate-application-segments-that-are-with-open-ports.png)

### Feature Available
#### Enhanced SSL Inspection Card
The SSL Inspection card (Insights > SSL Inspection) in the Risk360 Admin Portal is enhanced with the following new widget:
**Top 5 Uninspected User Traffic by URL Hosts**: This bar chart shows the top 5 uninspected URL hosts and their corresponding traffic volume for the last 30 days.
[See image.](#all)
Click the Investigate link under the preceding widget to view the data in a table for the top 100 uninspected URL hosts. You can filter the data using the filter option.
[See image.](#investigate-page-url)
[]![Top 5 Uninspected User Traffic by URL Hosts](/sites/default/files/downloads/risk360/abouting-alerts/Risk360-top-5-uninspected-user-traffic-by-url-host.png)
[]![Investigate Uninspected User Traffic by URL Hosts](/sites/default/files/downloads/risk360/abouting-alerts/Risk360-investigate-uninspected-user-traffic-by-url-host.png)

### Feature Available
#### Risk360 Integration with ZSLogin
Risk360 supports the ZIdentity service that allows you to single sign-on (SSO) to the different Zscaler admin portals using a single set of login credentials.
If you are subscribed to the ZIdentity service, admins are listed as read-only on the Administrators page and the Administrator Management page shows an SSO link to the ZSLogin Admin Portal where you can manage your admins.
To learn more, see [What Is ZSLogin?](/zslogin/what-zslogin), [About Administrators](/risk360/about-administrators-risk360), and [Understanding Administrator Management Settings](/risk360/understanding-administrator-management-settings-risk360).

## February 19, 2024
### Feature Available
#### Viewing Top 10 Key Events Affecting Risk
You can view the top 10 key events that contributed to your risk score (in the last 90 days) by clicking Key Events in the Risk Score Trend graph on the Dashboard page.
[See image.](#events)
To learn more, see [About Dashboard](/risk360/about-dashboard-risk360-draft#enlarged-view).
[]![Risk Score Trend and Top 10 Events in enlarged view](/sites/default/files/downloads/tech-pubs-drafts/risk360-draft-articles/about-dashboard-risk360-draft/Risk360-enlarged-risk-trend-graph_2.png)

## January 11, 2024
### Feature in Limited Availability
#### CrowdStrike Factors Support in Risk360
The Risk360 service supports integration with CrowdStrike to show you risk contributing factors. The Zscaler service calls the CrowdStrike Falcon API to request various risk related information, categorizes them under Risk360 categories (External Attack Surface, Compromise, Lateral Propagation, and Data Loss), and quantifies each factor according to its risk weight.
[See image.](#crowdstrike-factors)
To enable this feature, contact your Zscaler Account team.
To learn more, see [About Factors](/risk360/about-factors) and [CrowdStrike Integration For Risk360 Factors](/risk360/crowdstrike-integration-risk360-factors).
[]![CrowdStrike Factors](/sites/default/files/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Risk360-CrowdStrike-Factors.png)
