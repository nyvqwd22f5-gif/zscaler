# Release Upgrade Summary (2025)
Source: https://help.zscaler.com/zdx/release-upgrade-summary-2025

This article provides a summary of all new features and enhancements per Zscaler cloud for Zscaler Digital Experience (ZDX). Zscaler will email a notification to your organization's registered support contacts approximately one week before your cloud is upgraded. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** zdxcloud.net, zdxbeta.net
The following service updates were deployed to zdxcloud.net on

## October 24, 2025
### Feature Available
#### End-of-Support (EOS) and End-of-Life (EOL) Information on Software Inventory Page
View End-of-Support (EOS) and End-of-Life (EOL) information for your installed software directly on the Software Inventory page.
[See image.](#InventoryMenu)
[]![Viewing EOL and EOS information ](/sites/default/files/downloads/tech-pubs-drafts/zdx-draft-articles/viewing-software-inventory/zdx-sw-details-tables.jpg)
To learn more, see [Viewing Software Inventory](/zdx/viewing-software-inventory).

### Feature Available
#### Network Intelligence Dashboard Enhancements
The Network Intelligence Dashboard has been enhanced with updated alerts, featuring clearer criteria and richer incident insights. Additionally, new Network Health summary widgets have been added to surface issues faster and provide greater clarity:
- **Network Anomalies for Last 14 Days**: Shows total anomalies per day and severity.
- **Top 5 Cities Sorted by User Count**: Lists cities with the highest user counts and anomaly levels.
- **Top 5 High-Latency ASNs**: Compares measured latency to a baseline.
[See image.](#dashboard)
To learn more, see [Monitoring the Network Intelligence Dashboard](/zdx/monitoring-network-intelligence-dashboard) and [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[]
![View the Network Intelligence Dashboard](/sites/default/files/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/NI_Release_Note_%2001.png)

## October 10, 2025
### Feature Available
#### Admin Scope Support for ZIdentity Admins
You can assign an admin scope to a ZIdentity admin that is configured as a ZDX Admin.
[See image.](#scope)
To learn more, see [Managing ZDX Admins](/zdx/managing-zdx-admins).
[]
![Assign an admin scope to the admin](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/zdx-admin-scope.png)

## September 26, 2025
### Feature Available
#### Device Events Reports
The Device Events reports are available in the ZDX Admin Portal. View and monitor aggregated insights into common system and software crashes.
[See image.](#device)
User Device Events detects several new events and categorizes them into different severity levels for easier analysis and troubleshooting in the Event Details drawer.
[See image.](#details)
To learn more, see [Viewing Device Events Reports](/zdx/viewing-device-events-reports) and [Evaluating User Details](/zdx/evaluating-user-details).
[]
![View Device Events report to observe devices experiencing system crashes or software crashes](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/zdx-device-events-releasenote.png)
[]
![View granular details about software or system crashes on the Device Event Details](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/zdx-device-events-details.gif)

### Feature Available
#### Device Health Dashboard
The Device Health dashboard provides a comprehensive view of struggling devices across an entire organization, department, user group, or location.
[See image.](#img_device-dashboard)
The Device Health dashboard includes hardware analysis evaluating real-time device usage and hardware profiling to optimize resource allocation and reduce costs.
[See image.](#img_hardwareanalysis)
To learn more, see [Monitoring the Device Health Dashboard](/zdx/monitoring-device-health-dashboard).
[]
![View the Device Health dashboard](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/ZDX-Devices-Dashboard-Summary-ReleaseNote-1.png)
[]
![Hardware Analysis provides a comprehensive analysis of hardware profiles and usage profiles.](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/ZDX-Devices-Hardware-Analysis.png)

## September 15, 2025
### Feature in Limited Availability
#### Network Intelligence Dashboard
The Network Intelligence dashboard is a high-level visualization of your organization's network. ZDX runs Cloud Path probes to analyze and identify anomalies in the network's health that allow you to understand the underlying network issues across your organization. You can also configure an alert rule to automatically receive notifications for Network Intelligence.
[See image.](#dashboard)
To learn more, see [Monitoring the Network Intelligence Dashboard](/zdx/monitoring-network-intelligence-dashboard) and [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[]
![View the Network Intelligence Dashboard](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/zdx-network-intelligence-release-note-3_0.png)

## September 12, 2025
### Feature Available
#### Data Explorer End User Monitoring Enhancements with User Groups and Metric-Based Filters
End User Monitoring in Data Explorer supports User Groups and Metric-Based filters to refine data analysis and visualization.
[See image.](#endusermonitoring-newfilter)
To learn more, see [Configuring Data Explorer Views](/zdx/configuring-data-explorer-views).
[]![Screenshot of the Hosted Monitoring interface highlighting the Overlays section, which includes a dropdown for selecting percentile thresholds and a toggle for showing errors.](/sites/default/files/downloads/tech-pubs-drafts/zdx-draft-articles/doc-59831doc-59833doc-59444-data-explorer-v3-user-group-filtermetric-based-filter-supportpreview/usergroupsfilterandmetricbasedfilter.png)

### Feature Available
#### Enhanced Cloud Path Probe Configuration Options
Cloud Path probes include advanced configuration settings to improve network diagnostics and end-to-end performance measurements.
You can specify the following options to enhance monitoring flexibility:
- **End-to-End Metrics Probing Type**: Measure network performance metrics such as latency, jitter, and packet loss using options like Prefer Selective Acknowledgment (SACK), Force SACK, and Force Synchronization (SYN) packet probing.
- **Probing Type**: Choose between SYN and SACK for traceroute methods when TCP is used as the protocol.
- **Capture PMTU**: Enable or disable Path Maximum Transmission Unit (PMTU) discovery to detect packet size limitations and fragmentation issues along the network path.
- **DSCP Configuration**: Set Differentiated Services Code Point (DSCP) values to define packet priority during network probes and monitor Quality of Service (QoS) changes along the path.
[See image.](#cloudpath-options)
To learn more, see [Configuring Zscaler Hosted Probes](/zdx/configuring-zscaler-hosted-probes).
[]![Screenshot showing the Cloud Path Probe configuration options available in the user interface, such as Protocol, End-to-end Metrics Probing Type, and DSCP Configuration](/sites/default/files/downloads/tech-pubs-drafts/zdx-draft-articles/doc-58562-doc-additional-advanced-cloud-path-ui-work-configuring-zscaler-hosted-probes/zdx-zprobe-cloud-configuration-UI.png)

## August 29, 2025
### Feature Available
#### Data Explorer Hosted Monitoring Enhancements with Error Overlays and Companion Probes
Hosted monitoring in Data Explorer now supports error overlays and companion probe data visualization.
[See image.](#hosted-overlay-error)
To learn more, see [Configuring Data Explorer Views](/zdx/configuring-data-explorer-views).
[]![Screenshot of the Hosted Monitoring interface highlighting the Overlays section, which includes a dropdown for selecting percentile thresholds and a toggle for showing errors.](/sites/default/files/downloads/tech-pubs-drafts/zdx-draft-articles/doc-59501-data-explorer-phase-11-error-overlay-hosted-monitoring-configuring-data-explorer-views/hosted-overlays-ErrorOverlayWithInformationDisplay_0.png)

## August 01, 2025
### Feature Available
#### Data Explorer Hosted Monitoring Overlays
For Cloud Path probes in hosted monitoring, overlay support for percentile thresholds such as the 99th and 95th percentiles is available. These overlays provide insights into performance outliers and anomalies by highlighting worst-case and typical scenarios.
[See image.](#de-multipath-view)
To learn more, see [Configuring Data Explorer Views](/zdx/configuring-data-explorer-views).
[]![Screenshot of the Hosted Monitoring interface highlighting the Overlays section, which includes a dropdown for selecting percentile thresholds and a toggle for showing errors.](/sites/default/files/downloads/tech-pubs-drafts/doc-58561-data-explorer-phase-9-percentile-threshold-overlay-configuring-data-explorer-views/Data%20explorer.png)

## July 18, 2025
### Feature Available
#### Data Explorer Hosted Monitoring Multipath Visualization View
For Cloud Path probes in hosted monitoring, a multipath visualization view format is available. This format is in addition to the existing chart, scatter, tabular, and range formats.
[See image.](#de-multipath-view)
To learn more, see [Configuring Data Explorer Views](/zdx/configuring-data-explorer-views).
[]![Hosted Monitoring View Type Options ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/zdx-de-hosted-view-type.jpg)

## June 20, 2025
### Feature Available
#### Companion Probe
During a Zscaler Hosted probe configuration, you can pair a Cloud Path probe as a companion probe to the Web probe. When the Web probe resolves to an IP address, then the Cloud Path probe runs to the same IP address.
[See image.](#companion)
To learn more, see [Configuring Zscaler Hosted Probes](/zdx/configuring-zscaler-hosted-probes).
[]
![Configure a Companion probe](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/ZDX-zscaler-hosted-probe-configuration-companion-probe.png)

## June 06, 2025
### Feature Available
#### Alert Support for Any Incident Type
Configure an alert rule for any incident type in order to automatically be notified and securely monitor when impacted devices experience an incident.
[See image.](#incident)
To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[]
![Configure an alert rule for specific incident types](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/ZDX-ConfiguringAlertRule-SpecificIncidents-1.png)

### Feature Available
#### Alert Support for Call Quality Metrics
Configure alerts to capture Call Quality metrics by selecting a Unified Communications as a Service (UCaaS) application to automatically receive notifications when there is a poor digital experience. You can configure an alert by selecting Call Quality or Network as a rule type as long as you select a UCaaS application.
[See image.](#alertrule)
To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[]
![Select Call Quality as the alert rule type](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/ZDX-ConfiguringAlertRule-CallQuality.png)

### Feature Available
#### Software Patch Inventory
Software Patch Inventory allows you to identify the current distribution of software patches on user devices across your organization.
[See image.](#patch-inventory-portal-rn)
To learn more about the feature and its prerequisites, see [Viewing Software Patch Inventory](/zdx/viewing-software-patch-inventory).
[]![Software Patch Inventory in left navigation of the ZDX Admin Portal](/downloads/zdx/release-notes/release-upgrade-summary-2023/zdx-patch-inventory-portal-rn.png)

### Feature Available
#### UCaaS Application Support for ZDX Score Analysis
Analyzing ZDX scores on the User Details page using Analyze Score also supports Unified Communications as a Service (UCaaS) and Zscaler Private Access (ZPA)-enabled applications.
[See image.](#zdx-ucaas-ZPA-support)
To learn more, see [Evaluating User Details](/zdx/evaluating-user-details).
[]![UcaaS and ZPA application support in ZDX ](/sites/default/files/downloads/zdx/release-notes/zdx-rn-ucaas-zpa-app-support-analyze-score.png)

## May 16, 2025
### Feature Available
#### macOS Support for Hi-Fi Cloud Path Diagnostics Session
To start a Hi-Fi Cloud Path as a Diagnostics session in the ZDX Admin Portal, users with macOS devices require a minimum Zscaler Client Connector version 4.5.1 for macOS and ZDX Module version 4.4 for macOS.
[See image.](#hi-fi)
To learn more, see [Starting a New Diagnostics Session](/zdx/starting-new-diagnostics-session) and [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility).
[]
![macOS support for Hi-Fi Cloud Path as a Diagnostics session](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/ZDX-Start%20New%20Diagnostics%20Session-Hi-Fi-ReleaseNote.png)

### Feature Available
#### Wi-Fi Dashboard Enhancements
View a list of your impacted Wi-Fi access points on the Wi-Fi Dashboard page. Additionally, you can configure the Wi-Fi data collection to use signal strength and retransmission rate to identify low-performing Wi-Fi devices instead of the ZDX Score.
[See image.](#wi-fi-dashboard)
To learn more, see [Monitoring the Wi-Fi Dashboard](/zdx/monitoring-wi-fi-dashboard) and [Configuring Inventory Settings](/zdx/configuring-inventory-settings).
[]
![View impacted Wi-Fi access points in a List View](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/ZDX-Wi-Fi-Dashboard-ListView-Release-Note.png)

## May 07, 2025
### Feature Available
#### ZDX API Support in OneAPI
An update was released to support ZDX API in OneAPI. You can also sync ZDX API credentials for ZIdentity-enabled tenants with ZDX. If you are subscribed to ZIdentity and have it enabled for your tenant, API keys created in the ZIdentity Admin Portal appear on the API Keys page in the ZDX Admin Portal and are read only. API keys created in the ZDX Admin Portal are not visible in the ZIdentity Admin Portal.
To learn more, see [About API Key Management](/zdx/about-api-key-management), [Understanding OneAPI](/oneapi/understanding-oneapi), and [About API Clients](/zidentity/about-api-clients).

## April 25, 2025
### Feature Available
#### Location of Stored ZDX Data
ZDX logs and data are now stored in Singapore in addition to the United States, the European Union (Western Europe, Netherlands) or Australia East (New South Wales). Contact your Zscaler Account team for details.
To learn more about Zscaler's retention of logs and data, see [ZDX Logs](/customer-logs-fair-use/zdx-customer-logs-and-data).

## April 18, 2025
### Feature Available
#### Data Explorer Hosted Monitoring Range View
A range view format is available for customized Data Explorer hosted monitoring views, in addition to the chart, scatter, and tabular formats.
[See image.](#de-table-view)
To learn more, see [Configuring Data Explorer Views](/zdx/configuring-data-explorer-views).
[]![The View Type window showing the range view option](/sites/default/files/downloads/zdx/configuration/configuring-data-explorer-views/zdx-de-hosted-view-type_0.png)

## March 21, 2025
### Feature Available
#### Device Incident Type for Windows Devices
The Device incident type provides comprehensive key metrics on anomalous behavior by detecting and analyzing trends in device usage for Windows devices.
[See image.](#device)
To learn more, see [Monitoring the Incidents Dashboard](/zdx/monitoring-incidents-dashboard).
[]![Observe a Device incident to analyze system software hangs and crashes](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/zdx-incidents-devices-systemsoftwarecrashes.png)

### Feature Available
#### Probe Assignments Report
The system-generated report for Probe Assignments is available in the ZDX Admin Portal.
[See image.](#probe-assignments)
To learn more, see [Viewing System-Generated Reports](/zdx/viewing-system-generated-reports).
[]![View the Probe Assignments report for details on probe usage](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/ZDX-System-Generated-Reports-Probe-Assignments.png)

## March 14, 2025
### Feature Available
#### SCIM Auto Provisioning for Admin Groups
You can enable SCIM Auto Provisioning to provide a user's group information as an admin group on the Administrator Management page. You can then manage admin groups on the Admin Groups page to associate roles and scopes that provide limitations and access to the ZDX Admin Portal.
[See image.](#AdminGroups)
To learn more, see [Configuring Administrator Management Settings](/zdx/configuring-administrator-management-settings), [About Admin Groups](/zdx/about-admin-groups), and [Managing Admin Groups](/zdx/managing-admin-groups).
[]
![SCIM Auto Provisioning](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2024/ZDX-AdministratorManagement-SCIMAutoProvisioning-ReleaseNote_0.png)
![Admin Group Page](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2024/ZDX-Admin-Groups-Overview.png)

## March 07, 2025
### Feature Available
#### Data Explorer Hosted Monitoring Scattered View
A scattered view format is available for customized Data Explorer hosted monitoring views, in addition to the chart and tabular formats.
[See image.](#de-table-view)
To learn more, see [Configuring Data Explorer Views](/zdx/configuring-data-explorer-views).
[]![scatter view](/sites/default/files/downloads/zdx/release-notes/scatter-view.png)

### Feature Available
#### User Domain Settings for ServiceNow
Configure the User Domain Settings in ServiceNow to update user records for emails or usernames with different logins.
[See image.](#domain)
To learn more, see [ZDX Integration on ServiceNow](/zdx/zdx-integration-servicenow).
[]
![Configure Domain Settings for user identity](/sites/default/files/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/servicenow-configuration-guides/zdx-integration-servicenow/ZDX-SNOW-Domain-Settings.png)

## February 21, 2025
### Feature Available
#### Data Explorer Tabular View and Improved Filters for Hosted Monitoring
A tabular format is available for hosted monitoring Data Explorer views, in addition to the chart format.
[See image.](#zdx-de-hosted-tabular-view)
[]![Hosted Monitoring - Tabular Format](/sites/default/files/downloads/tech-pubs-drafts/zdx-draft-articles/configuring-data-explorer-views-doc-56395/zdx-de-hosted-monitoring-view-rn.jpg)
For the selected metrics in your view, you can use filter operator and value fields to improve filter accuracy.
[See image.](#zdx-de-improved-metrics-filters)
[]![Improved metrics and filters ](/sites/default/files/downloads/tech-pubs-drafts/zdx-draft-articles/configuring-data-explorer-views-doc-56395/zdx-de-filters-metrics-hosted-monitoring-updated-rn.jpg)
To learn more, see [Configuring Data Explorer Views](/zdx/configuring-data-explorer-views).

## February 07, 2025
### Feature Available
#### Alert Rule Support for Custom Applications with Network Application Type
Configure an alert rule for a custom application that is a network application type.
[See image.](#alert)
To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[]
![Select a custom application that is a network application type](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/ZDX-Alert-Custom-Network.png)

### Feature Available
#### Data Explorer Views for Hosted Monitoring
You can generate and analyze views for Zscaler hosted data in Data Explorer.
[See image.](#zdx-de-hosted-charts-view)
[]
![zdx-de-hosted-charts-view.png](/sites/default/files/downloads/zdx/release-notes/zdx-de-hosted-charts-view.png)
To learn more, see [Configuring Data Explorer Views](/zdx/configuring-data-explorer-views) and [Monitoring Data Explorer Views](/zdx/monitoring-data-explorer-views).

### Feature Available
#### ZPA Incidents
On the Incidents Dashboard, a new ZPA incident type provides comprehensive key metrics on Zscaler Private Access (ZPA) traffic at the Zscaler data center.
The ZPA incident type includes the following subtypes:
- ZPA Public Service Edge
- ZPA App Connector
[See image.](#zpaincident)
To learn more, see [Monitoring the Incidents Dashboard](/zdx/monitoring-incidents-dashboard).
[]![Observe a ZPA Incident](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2025/zdx-incidents-ZPA.png)

## January 24, 2025
### Feature Available
#### Data Explorer Tabular View
A tabular format is available for customized Data Explorer views, in addition to the chart format.
[See image.](#de-table-view)
To learn more, see [Configuring Data Explorer Views](/zdx/configuring-data-explorer-views).
[]![Data Explorer Tabular View](/downloads/zdx/release-notes/release-upgrade-summary-2025/zdx-de-tabular-view-rn.png)

### Feature Available
#### Packet Capture Enhancements
The frame size limit for Packet Capture probing has been updated to 65,536 bytes.
[See image.](#packet-capture)
[]
![Packet Capture - Frame Size Limit](/sites/default/files/downloads/zdx/diagnostics/starting-new-diagnostics-session/ZDX-Start-New-Diagnostics-Packet-Capture-Updated.jpg)
When starting Packet Capture as a diagnostics session, a new Disk Space Limit option is available for Windows device users with ZDX Module version 4.5 and later.
[See image.](#disk-limit)
[]
![Disk-Space-Limit](/sites/default/files/downloads/zdx/diagnostics/starting-new-diagnostics-session/ZDX-PCAP-Disk-Space-Limit.jpg)
To learn more, see [Starting a New Diagnostics Session](/zdx/starting-new-diagnostics-session).

## January 17, 2025
### Feature Available
#### Application Admin Scope
You can select Applications as an admin scope when configuring a ZDX Admin.
[See image.](#applications)
To learn more, see [Managing ZDX Admins](/zdx/managing-zdx-admins).
[]
![Applications Admin Scope](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2024/ZDX-Application-Admin-Scope.png)

### Feature Available
#### Dark Mode Selection
You can select Dark Mode as your Theme from the My Profile menu.
[See image.](#dark)
To learn more, see [Customizing Your Admin Account Settings](/zdx/customizing-your-admin-account-settings).
[]
![Dark Mode as Theme](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2024/ZDX-Dark-Theme.jpg)

### Feature Available
#### Download CSV File of ZDX Admins
The Export option allows you to download a CSV file of ZDX Admins from the Administrators page.
[See image.](#export)
To learn more, see [About Administrators](/zdx/about-administrators).
[]
![Export ZDX Admins](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2024/ReleaseNote_Download.png)

### Feature Available
#### Full Cloud Path for ZDX Standard Subscriptions
The full [Cloud Path](/zdx/evaluating-cloud-path) is accessible in the Hop View and Command Line View for all ZDX subscriptions, including Standard subscriptions.
[See image.](#full-cp-std)
To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
[]![Full Cloud Path access](/downloads/zdx/release-notes/release-upgrade-summary-2025/zdx-full-cp-std.png)
