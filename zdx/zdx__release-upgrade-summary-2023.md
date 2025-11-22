# Release Upgrade Summary (2023)
Source: https://help.zscaler.com/zdx/release-upgrade-summary-2023

This article provides a summary of all new features and enhancements per Zscaler cloud for Zscaler Digital Experience (ZDX). Zscaler will email a notification to your organization's registered support contacts approximately one week before your cloud is upgraded. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** zdxcloud.net, zdxbeta.net
The following service updates were deployed to zdxcloud.net on

## December 15, 2023
### Feature Available
#### Reports for ZDX Score by Applications and Wi-Fi Distribution
System-generated reports for ZDX Score by Applications and Wi-Fi Distribution are available in the ZDX Admin Portal.
To view the reports, make sure your subscription level supports system-generated reports and your ZDX role has the proper permission level.
[See image.](#sgr56-rn)
To learn more, see [Viewing System-Generated Reports](/zdx/viewing-system-generated-reports), [Ranges & Limitations](/zdx/ranges-limitations), and [Adding ZDX Roles](/zdx/adding-zdx-roles).
[]![Additional System-Generated Reports for ZDX Score by Application and Wi-Fi Distribution](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-static-reports-dashboard6.1-rn.png)

## December 01, 2023
### Feature Available
#### Exclude Option for Alert Rule Configuration's Filters
You can exclude items from a filter while configuring an Alert Rule.
[See image.](#ExcludeOption)
To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule) and [Editing an Alert Rule](/zdx/editing-alert-rule).
[]
![Select an item to exclude.](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-ConfiguringAlertRule-ExcludeOption1.png)
![Filters Selection](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-ConfiguringAlertRule-ExcludeOption2.png)

### Feature Available
#### Report for Application Performance
The system-generated report for Application Performance is available in the ZDX Admin Portal.
To view the report, make sure your subscription level supports system-generated reports and your ZDX role has the proper permission level.
[See image.](#sgr45-rn)
To learn more, see [Viewing System-Generated Reports](/zdx/viewing-system-generated-reports), [Ranges & Limitations](/zdx/ranges-limitations), and [Adding ZDX Roles](/zdx/adding-zdx-roles).
![Dashboard for System-Generated Reports](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-static-reports-dashboard4-rn.png)
[]

## September 29, 2023
### Feature Available
#### Improved Filter Interaction
Filter interaction has been improved in the Performance Overview, Applications Overview, User Overview, Alerts, and Rules pages in the ZDX Admin Portal to include or exclude filter selections. The filter interaction has also been added to probing criteria when configuring a new probe.
[See image.](#filter-interaction-rn)
To learn more, see [Monitoring the ZDX Dashboard](/zdx/monitoring-zdx-dashboard) and [Monitoring the Users Dashboard](/zdx/monitoring-users-dashboard).
[]![Include and Exclude Filter Selection](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-include-exclude2-rn.png)

### Feature Available
#### Improved Search for Probes
Filters have been added to the Probes page to help identify specific probes when using Search.
[See image.](#filter-probes-rn)
To learn more, see [About Probes](/zdx/about-probes).
[]![Probes page filters](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-probes-page-filters-search-rn.png)

### Feature Available
#### ZDX Autosense for Microsoft Teams Call Quality
ZDX Autosense dynamically detects the destination IP address and port for data traffic, and provides an automated Cloud Path probe when you onboard a Microsoft Teams Call Quality tenant.
Before you onboard a Microsoft Teams Call Quality tenant, make sure your ZDX subscription level supports ZDX Autosense, and you’re running the required versions of Zscaler Client Connector and ZDX Module. You must also enable a driver installation setting for ZDX Autosense in the Zscaler Client Connector Portal.
[See image.](#autosense-teams-rn)
To learn more, see [Understanding Microsoft Teams Call Quality for ZDX](/zdx/understanding-microsoft-teams-call-quality-zdx), [Supported Versions & Feature Compatibility](/zdx/feature-version-compatibilities), [Ranges & Limitations](/zdx/ranges-limitations), and [Configuring Zscaler Client Connector Profiles](/client-connector/configuring-zscaler-client-connector-profiles).
[]![ZDX Autosense for Microsoft Teams Call Quality](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-autosense-teams-card-rn.png)

## September 15, 2023
### Feature Available
#### Detailed Metrics for Page Fetch Time
Granular metrics for Page Fetch Time are available for Advanced Plus users on the user details page. View additional graphs with details that show a breakdown of individual time metrics that comprise the overall Page Fetch Time.
[See image.](#pft-time-metrics)
To learn more, see [Evaluating User Details](/zdx/evaluating-user-details#webprobemetrics).
[]![Page Fetch Time metrics](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-pft-metrics-rn.png)

### Feature Available
#### ZDX Autosense for Webex Call Quality
ZDX Autosense dynamically detects the destination IP address and port for data traffic, and provides an automated Cloud Path probe when you onboard a Webex Call Quality tenant.
Before you onboard a Webex Call Quality tenant, make sure your ZDX subscription level supports ZDX Autosense, and you’re running the required versions of Zscaler Client Connector and ZDX Module. You must also enable a driver installation setting for ZDX Autosense in the Zscaler Client Connector Portal.
[See image.](#autosense-webex-rn)
To learn more, see [Configuring Webex Call Quality for ZDX](/zdx/configuring-webex-call-quality-zdx), [Supported Versions & Feature Compatibility](/zdx/feature-version-compatibilities), [Ranges & Limitations](/zdx/ranges-limitations), and [Configuring Zscaler Client Connector Profiles](/client-connector/configuring-zscaler-client-connector-profiles).
[]![ZDX Autosense for Webex Call Quality](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-autosense-webex-card-rn.png)

## September 08, 2023
### Feature in Limited Availability
#### Zoom Quality of Service Subscription
Zoom Call Quality for ZDX provides the option to onboard a Zoom Quality of Service Subscription (QSS) tenant instead of a Zoom API tenant.
Contact your Zscaler Account Manager to request access to this feature.
[See image.](#zoom-qss-rn)
To learn more, see [Configuring Zoom Call Quality for ZDX](/zdx/configuring-zoom-call-quality-zdx).
[]![Option to select Zoom QSS for onboarding](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-select-zoom-qss.png)

## August 31, 2023
### Feature Available
#### ZDX Integration on ServiceNow
ServiceNow integrates with ZDX’s Root Cause Analysis and Deep Tracing to provide insightful analytics on a user’s applications metrics when the ZDX Score drops.
[See image.](#ZDXIntegrationOnServiceNow)
To learn more, see [ZDX Integration on ServiceNow](/zdx/zdx-integration-servicenow).
[]![ZDX Summary](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ServiceNow-ZDXSummary%20(2).jpg)
![Start a New Deep Tracing Session on ServiceNow](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ServiceNow-StartNewDeepTracing-ReleaseNote.jpg)

## August 29, 2023
### Feature Available
#### Self Service
Self Service allows users to resolve potential issues related to CPU usage and Wi-Fi access without the need to contact customer support. When enabled, an admin can review insights on how notifications are distributed to users on the Self-Service IT Overview dashboard.
Make sure your subscription level supports Self Service. To access the Self-Service IT Overview dashboard or to configure which users receive notifications, your ZDX role must have the proper permission level for Self-Service IT in the Add ZDX Role window.
[See image.](#self-service-IT-release-note)
To learn more, see [Configuring Self Service Settings](/zdx/configuring-self-service-it-settings), [Monitoring the Self Service Dashboard](/zdx/monitoring-self-service-dashboard), [Adding ZDX Roles](/zdx/adding-zdx-roles), and [Ranges and Limitations](/zdx/ranges-limitations).
[![Self-Service IT Overview](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-SSIT-Dashboard-ReleaseNote.png)
]

## August 25, 2023
### Feature Available
#### Filter for Location Groups
A filter has been added to the Performance Overview, Applications Overview, and User Overview pages in the ZDX Admin Portal to specify location groups in your organization. The filter has also been added to probing criteria when configuring a new probe and rule filters when configuring an alert rule.
[See image.](#loc-groups-rn)
To learn more, see [Monitoring the ZDX Dashboard](/zdx/monitoring-zdx-dashboard), [Monitoring the Applications Dashboard](/zdx/monitoring-applications-dashboard), [Configuring a Probe](/zdx/configuring-probe), and [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[]![Location Groups filter on ZDX Dashboard](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-location-groups-rn.png)

### Feature Available
#### Incidents Dashboard
The Incidents Dashboard displays incidents, which are issues that affect the device performance of multiple users that ZDX detects in the areas of Wi-Fi, Last Mile ISP, Zscaler Data Centers, and Application.
Make sure your subscription level supports the Incidents Dashboard. Your ZDX admin role must have the proper permission level for Incidents in the Add ZDX Role window to access the Incidents Dashboard.
[See image.](#zdx-incidents)
To learn more, see [Monitoring the Incidents Dashboard](/zdx/monitoring-incidents-dashboard), [Ranges & Limitations](/zdx/ranges-limitations), and [Adding ZDX Roles](/zdx/adding-zdx-roles).
[]![Incident Overview on the Incident Dashboard](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/Incidents%20Overview%20Summary%20-%20Release%20Note.png)

### Feature Available
#### ZDX Snapshot
The ZDX Snapshot feature provides a URL that you can share with ZDX users for view-only access of the user details page. ZDX Snapshot enables users without ZDX Admin Portal login access to view ZDX user details with limited user interaction.
Make sure your subscription level supports ZDX Snapshot and your ZDX role has the proper permission level to share ZDX Snapshots.
[See image.](#snap1-rn)
To learn more, see [Sharing ZDX Snapshots](/zdx/sharing-zdx-snapshots), [Ranges & Limitations](/zdx/ranges-limitations), and [Adding ZDX Roles](/zdx/adding-zdx-roles).
[]![Link to share ZDX Snapshot on user details page](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-snapshot-user-details2.png)

## August 18, 2023
### Feature Available
#### Additional System-Generated Reports
System-generated reports for Last Mile ISP Performance and DNS Performance are available in the ZDX Admin Portal.
To view the reports, make sure your subscription level supports system-generated reports and your ZDX role has the proper permission level.
[See image.](#sgr2-rn)
To learn more, see [Viewing System-Generated Reports](/zdx/viewing-system-generated-reports), [Ranges & Limitations](/zdx/ranges-limitations), and [Adding ZDX Roles](/zdx/adding-zdx-roles).
[]![Additional System-Generated Reports](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-static-reports-latency-phase2.png)

### Feature Available
#### Bandwidth Test for Deep Tracing Session
You can select a bandwidth test when you start a Deep Tracing Session on a user’s device.
[See image.](#zdx-bandwidthtest-releasenote)
To learn more, see [Starting a New Deep Tracing Session](/zdx/starting-new-deep-tracing-session).
[]![Bandwidth Test](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-StartDeepTracing-BandwidthTesting.png)

### Feature Available
#### Labels
You can manage labels and review label details on the Labels page.
[See image.](#ZDX-Labels)
To learn more, see [About Labels](/zdx/about-labels) and [Managing Labels](/zdx/managing-labels).
[]![Labels Overview Page](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/Labels%20Overview-ReleaseNote.png)

### Feature Available
#### ZDX Autosense for Zoom Call Quality
ZDX Autosense dynamically detects the destination IP address and port for data traffic, and provides an automated Cloud Path probe when you onboard a Zoom Call Quality tenant.
Before you onboard a Zoom Call Quality tenant, make sure your ZDX subscription level supports ZDX Autosense, and you’re running the required versions of Zscaler Client Connector and ZDX Module. You must also enable a driver installation setting for ZDX Autosense in the Zscaler Client Connector Portal.
[See image.](#autosense-rn)
To learn more, see [Configuring Zoom Call Quality for ZDX](/zdx/configuring-zoom-call-quality-zdx), [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility), [Ranges & Limitations](/zdx/ranges-limitations), and [Configuring Zscaler Client Connector Profiles](/client-connector/configuring-zscaler-client-connector-profiles).
[]![ZDX Autosense card for Cloud Path probe](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-autosense-probes-cards2-rn.png)

## July 28, 2023
### Feature Available
#### External Proxy in Cloud Path
Zscaler Digital Experience (ZDX) supports traceroute scenarios in the Cloud Path when an External Proxy is detected.
[See image.](#cp-eproxy-rn)
To learn more, see [Evaluating the Cloud Path](/zdx/evaluating-cloud-path).
[]![External proxy shown in Hop View](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-eproxy-1-a-rn.png)

### Feature Available
#### Process Inventory
Process Inventory allows you to monitor processes that might be impacting the behavior of your users' devices. Process calculations are updated in one-minute rolling intervals, and the top processes are displayed every five minutes.
To monitor the processes, you first need to set a CPU usage threshold for devices in your organization. Minimum versions of Zscaler Client Connector and ZDX Module are also required.
[See image.](#process-inventory-rn)
To learn more, see [Viewing Process Inventory](/zdx/viewing-process-inventory), [Configuring Inventory Settings](/zdx/configuring-inventory-settings), and [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility).
[]![Accessing Process Inventory from left-side navigation of ZDX Admin Portal](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-portal-access-rn.png)

## July 21, 2023
### Feature Available
#### Dynamic Alerting
You can create a dynamic alert by configuring the alert rule type to network or application and selecting the ZDX Score or ZDX Score Drops parameter.
[See image.](#dynamicalert)
To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule), [Evaluating Individual Alert Details](/zdx/evaluating-individual-alert-details), and [Triggering an Alert](/zdx/triggering-alert).
[]![Create a dynamic alert with the ZDX Score or ZDX Score drop parameter.](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-DynamicAlerting.png)

## July 07, 2023
### Feature Available
#### Filter for User Groups
A filter has been added to the Performance Overview, Applications Overview, and User Overview pages in the ZDX Admin Portal to specify user groups in your organization.
[See image.](#user-groups-rn)
To learn more, see [Monitoring the ZDX Dashboard](/zdx/monitoring-zdx-dashboard) and [Monitoring the Users Dashboard](/zdx/monitoring-users-dashboard).
[]![Filter for User Groups](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-user-group-rn.png)

## June 23, 2023
### Feature Available
#### Quarterly Business Review Reports
Download Quarterly Business Review (QBR) reports from the ZDX Admin Portal for insights into how Zscaler is helping protect your network. The reports can help you understand emerging traffic trends and the types of threats that Zscaler is blocking.
To access the reports, your ZDX role must have the proper permission level for Analytics in the Add ZDX Role window.
[See image.](#qbr-download-rn)
To learn more, see [Downloading Quarterly Business Review Reports](/zdx/downloading-quarterly-business-review-reports) and [Adding ZDX Roles](/zdx/adding-zdx-roles).
[]![Download Quarterly Business Review Reports](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-qbr-report-download3.png)

## June 16, 2023
### Feature Available
#### System-Generated Reports
View system-generated reports in the Zscaler Digital Experience (ZDX) Admin Portal that detail aggregated user data across your organization.
To view the reports, your ZDX role for Analytics must have the Full or View Only permission level in the Add ZDX Role window.
[See image.](#sgr-rn)
To learn more, see [Viewing System-Generated Reports](/zdx/viewing-system-generated-reports) and [Adding ZDX Roles](/zdx/adding-zdx-roles).
[]![Example table of System-Generated Reports](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-static-reports-latency-rn2.png)

## June 09, 2023
### Feature Available
#### Managing Top Private Applications
You can manage your Zscaler Private Access (ZPA) applications in ZDX in the Configuration Portal (Configuration > Applications > Top Private Apps).
[See image.](#zdx-topprivateapp-releasenote)
To learn more, see [Managing Top Private Applications](/zdx/managing-top-private-applications).
[]![Top Private Apps page](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-topprivateapps-searchresults-2.png)

### Feature Available
#### SIPA in Web Probe Metrics
Web probe traffic forwarded through Source IP Anchoring (SIPA) is highlighted in the graphs for Web Probe Metrics.
[See image.](#sipa-web-rn)
To learn more, see [Evaluating User Details](/zdx/evaluating-user-details).
[]![SIPA rendered in Web Probe Metrics](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-sipa-web-rendered5-rn.png)

## May 26, 2023
### Feature Available
#### Inventory Management for Admin Access
You can configure the permission settings for Inventory Management from the Add ZDX Role dialog window in Role Management.
[See image.](#InventoryManagement)
To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
[]![Inventory Management Granular Permission for Admin Access](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-Add-ZDX-Role-InventoryManagement-ReleaseNote.png)

### Feature Available
#### ISP Filtering
A filter has been added to the Performance Overview, Applications Overview, and User Overview pages in the ZDX Admin Portal to select the Internet Service Provider (ISP) for users in your organization.
[See image.](#isp-filter-rn)
To learn more, see [Monitoring the ZDX Dashboard](/zdx/monitoring-zdx-dashboard) and [Monitoring the Users Dashboard](/zdx/monitoring-users-dashboard).
[]![Filter for Last Mile ISPs](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-isp-filter-rn.png)

### Feature Available
#### Time Duration for Admin Access
You can select a time duration or Full Access for your Help Desk roles with other granular permissions levels in the Add ZDX Role window.
[See image.](#TimeDuration)
To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
[]![Select Time Duration for admin access.](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-Add-ZDX-Role-TimeDuration-ReleaseNote.jpg)

## May 19, 2023
### Feature Available
#### Webex Call Quality for ZDX
Zscaler Digital Experience (ZDX) supports Webex Call Quality to monitor calls or meetings among two or more participants in a configured Webex tenant. Call Quality works in parallel with cloud path probes, device metrics, and device events to help you identify issues that are unique to a device, application, or network.
[See image.](#webex-cqm-card)
To learn more, see [Configuring Webex Call Quality for ZDX](/zdx/configuring-webex-call-quality-zdx) and [Understanding Webex Call Quality for ZDX](/zdx/understanding-webex-call-quality-zdx).
[]![Webex Call Quality application card](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-webex-app-card2.png)

## May 12, 2023
### Feature Available
#### Additional Predefined Applications
Microsoft Login, Okta, and Webex (web app) are available as predefined applications in the Zscaler Digital Experience (ZDX) Admin Portal.
[See image.](#add-pre-apps-rn)
To learn more, see [Predefined Applications for ZDX](/zdx/predefined-applications-zdx).
[]![Predefined applications](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-additional-predefined-applications-rn.png)

### Feature Available
#### Redirects for Predefined Applications
To ensure accurate performance measurements, the setting for Follow Redirect is disabled by default when configuring a web probe for the following predefined applications:
- Box
- Microsoft Teams Web App
- OneDrive for Business
- Outlook Online
- ServiceNow
- SharePoint Online
[See image.](#pre-apps-redirects-rn)
To learn more, see [Configuring a Probe](/zdx/configuring-probe).
[]![Follow Redirect setting for configuring a web probe](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-disable-follow-redirect-rn.png)

## March 17, 2023
### Feature Available
#### Department Selection for an Admin’s Scope
The scope criteria in the Add ZDX Admin or Edit ZDX Admin window has been updated to allow the selection of Department.
[See image.](#DepartmentSelectionAdminScope)
[]![Select Department for the Admin's Scope criteria.](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-AddZDXAdmin-Department.jpg)

### Feature Available
#### Remote Assistance Device Information Obfuscation
In the Remote Assistance window, an admin can set their Device Information to Visible or Obfuscated.
[See image.](#DeviceInfoObfuscation)
[]![Set device information to Visible or Obfuscated.](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-RemoteAssistance-ReleaseNote-DeviceInfo-0.jpg)

## February 24, 2023
### Feature Available
#### Reference Line in Impacted User Devices Chart
A dotted reference line was added to the Impacted User Devices chart on an individual Alert Details page. This reference line is based on the criteria set from configuring an alert rule.
[See image.](#reference-line)
To learn more, see [Evaluating Individual Alert Details](/zdx/evaluating-individual-alert-details).
[![Reference Line on Individual Alert Details](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-ReleaseNote-IndividualAlertDetails-ReferenceLine-1.jpg)
]

## January 27, 2023
### Feature Available
#### Alert Details Enhancements
You can view the total and list of impacted devices per department, geolocation, or locations more readily.
[See image.](#AlertDetailsEnhancement)
To learn more, see [Evaluating Individual Alert Details](/zdx/evaluating-individual-alert-details).
[]![View the total or list and the list of impacted devices.](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-Alerts-IndividualAlertDetails-ReleaseNote.png)

### Feature Available
#### Alert Rule Copy Capability
You can copy the details of an existing rule in the Rules overview on the Alerts page.
[See image.](#ZDXCopyCapability)
To learn more, see [About Rules](/zdx/about-rules).
[]![Copy the selected rule's configuration.](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-ReleaseNote-CopyIcon.png)
![Displayed copy configuration of the selected rule.](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/ZDX-ReleaseNote-CopyRuleConfiguration.png)

### Feature Available
#### Citrix Support in Cloud Path
When Citrix is the network interface for TCP or UDP probes, Zscaler Digital Experience (ZDX) displays the path to the VPN Concentrator.
[See image.](#vpn-concentrator-route)
To learn more, see [Evaluating the Cloud Path](/zdx/evaluating-cloud-path).
[]![VPN Concentrator in Hop View](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-state-street-cp-pc2.png)

### Feature Available
#### Network Interface Types in Cloud Path
Network interface detection for cellular, Bluetooth, and USB types is represented in the hop view, as applicable.
[See image.](#network-types)
To learn more, see [Evaluating User Details](/zdx/evaluating-user-details#cloudpath).
[]![Example of network interface type in cloud path](/downloads/zdx/release-notes/release-upgrade-summary-2023/bluetooth_example.png)

### Feature Available
#### Packet Capture in Deep Tracing
You can enable Packet Capture (PCAP) for network trafficking in Deep Tracing Sessions.
[See image.](#PCAP)
To learn more, see [About Deep Tracing,](/zdx/about-deep-tracing) [Evaluating Deep Tracing Session Information](/zdx/Evaluating-Deep-Tracing-Session-Information), and [Starting a New Deep Tracing Session](/zdx/starting-new-deep-tracing-session).
[![PCAP configuration window](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2023/DeepTracing-PacketCaptureProbing-Example-1.png)
]

### Feature Available
#### Salesforce Applications
Zscaler Digital Experience (ZDX) supports both Salesforce Classic and the Salesforce Lightning interface as predefined applications.
[See image.](#salesforce-apps)
To learn more, see [Predefined Applications for ZDX](/zdx/predefined-applications-zdx).
[]![Salesforce Classic and Salesforce Lightning](/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-sfdc-classic-and-lightning-highlighted.png)

### Feature Available
#### ZDX Score Map Enhancements
The user interaction for the Regions by ZDX Score maps has been enhanced in the Performance Overview and Applications details pages, including the addition of a tooltip icon that links to the User Overview page.
[See image.](#zdx-score-map)
To learn more, see [About the ZDX Dashboard](/zdx/about-zdx-dashboard) and [About the Applications Dashboard](/zdx/about-applications-dashboard).
[]![Regions by ZDX Score map location](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-map-location-tooltip-highlighted.png)

### Feature in Limited Availability
#### Microsoft Endpoint Analytics for ZDX
Microsoft Endpoint Analytics helps identify issues with user software or devices that might be impacting performance and reliability. Metrics are garnered from the Microsoft Intune API and mapped to individual ZDX users and devices to provide Endpoint Analytics scores and data.
Contact your Zscaler Account Manager to request access to this feature.
[See image.](#ms-ept)
To learn more, see [Configuring Microsoft Intune for ZDX](/zdx/configuring-microsoft-intune-zdx) and [Understanding Microsoft Endpoint Analytics for ZDX](/zdx/understanding-microsoft-endpoint-analytics-zdx).
[]![Accessing Endpoint Analytics from user details page](/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-endpoint-analytics-user-details4.png)
