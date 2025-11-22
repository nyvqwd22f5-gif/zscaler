# Release Upgrade Summary (2022)
Source: https://help.zscaler.com/zdx/release-upgrade-summary-2022

This article provides a summary of all new features and enhancements per Zscaler cloud for Zscaler Digital Experience (ZDX). Zscaler will email a notification to your organization's registered support contacts approximately one week before your cloud is upgraded. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** zdxcloud.net, zdxbeta.net
The following service updates were deployed to zdxcloud.net on

## October 21, 2022
### Feature Available
#### Compare ZDX Scores
Compare two time points in the ZDX Score Over Time graph on the user details page to view differences in ZDX Score data. The feature utilizes web, device, and cloud path metrics to help determine differences in scoring.
[See image.](#compare)
To learn more, see [Evaluating User Details](/zdx/evaluating-user-details).
[]![Compare ZDX Scores between two time points](/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-yengine-compare-options2.png)

### Feature Available
#### Depiction of Disabled and Deleted Applications and Probes
The distinction between disabled and deleted applications and probes in the ZDX Admin Portal UI has been updated. Disabled application and probe names are indicated in grey, and deleted application names are indicated via strikethrough.
[See image.](#disable-delete)
To learn more, see [About the ZDX Dashboard](/zdx/about-zdx-dashboard) and [About the Applications Dashboard](/zdx/about-applications-dashboard).
[]![Applications Overview page showing disabled and deleted applications](/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-app-overview.png)

### Feature Available
#### Device Time Zone in Hop View
Upon hover, the device profile in the Cloud Path Hop View includes the Device Time Zone.
[See image.](#device-time-zone)
To learn more, see [Evaluating User Details](/zdx/evaluating-user-details#cloudpath).
[]![Device Time Zone in device profile of hop view](/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-device-profile-tooltip-time-zone.png)

## September 23, 2022
### Feature Available
#### Software and Device Inventory
View current and historical information about software versions and updates on user devices, as well as current information about the devices and associated users. You can access Software Inventory and Device Inventory in the Inventory menu.
[See image.](#InventoryMenu)
In order to view Inventory data, you must enable Inventory Data Collection under the Inventory Settings in the Administration menu and run Zscaler Client Connector version 3.3 or later for Windows.
[See image.](#InventorySettings)
[]![View Inventory Menu](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-inventory-menu.png)
[]![View Inventory Settings from Administration menu.](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-inventory-settings.png)
To learn more, see [About Software Inventory](/zdx/about-software-inventory), [About Device Inventory](/zdx/about-device-inventory), and [Configuring Inventory Settings](/zdx/configuring-inventory-settings). Contact your Zscaler Account Manager to request access to this feature.

## August 19, 2022
### Feature Available
#### Granular Permissions and Obfuscation
You can assign granular permissions for your Help Desk roles with the updated permissions levels on the Add ZDX Role window.
If an admin has obfuscation assigned and is unable to see the required information, review the obfuscation settings in the permissions levels.
[See image.](#UserSearch)
To learn more, see[ Adding ZDX Roles](/zdx/adding-zdx-roles), [About ZDX Service Desk Role](/zdx/about-zdx-service-desk-role), and [About ZDX Role-based Administration](/zdx/about-zdx-role-based-administration).
[![Available Granular Permissions for role-based access control.](/sites/default/files/downloads/zdx/administration/adding-zdx-roles/zdx-add-role_0.png)
]

## August 17, 2022
### Feature in Limited Availability
#### ZDX API Key Management
You can create or manage an API key on the API Key Management page.
[See image.](#api-key-management-page)
Contact your Zscaler Account team to request access to this feature.
To learn more, see [About API Key Management](/zdx/about-api-key-management).
[![Displays API Key Management page.](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-api-key%20management-page.png)
]

## August 15, 2022
### Feature Available
#### ServiceNow Incident Management Integration with ZDX
Zscaler Digital Experience (ZDX) supports the integration of ServiceNow Incident Management in a ServiceNow instance to automatically create incidents when alerts are triggered.
[See image.](#snow-store)
To learn more about ServiceNow Incident Management, see the [ServiceNow Store](https://store.servicenow.com/sn_appstore_store.do#!/store/application/faa68b0987510510d52bca2e0ebb358d/2.0.0?referer=%2Fstore%2Fsearch%3Flistingtype%3Dallintegrations%25253Bancillary_app%25253Bcertified_apps%25253Bcontent%25253Bindustry_solution%25253Boem%25253Butility%25253Btemplate%26q%3Dzscaler&sl=sh).
To learn more about webhook configuration for ServiceNow Incident Management, see [Configuring Webhooks for ServiceNow](/zdx/configuring-webhooks-servicenow).
[]![ServiceNow Store page for ZDX](/downloads/zdx/release-notes/release-upgrade-summary-2022/app-store.png)

## August 12, 2022
### Feature Available
#### Alert Statuses
You can view alert statuses on the Alerts page.
[See image.](#alert-status-column)
To learn more, see [Understanding the Alert Status](/zdx/understanding-alert-status).
[![Alert Statuses column is now displayed to provide information on the Alert's Status.](/sites/default/files/downloads/zdx/alerts/understanding-alert-status/zdx-ongoing%20alerts-statuses.png)
]

### Feature Available
#### Default Packet Count for Cloud Path Probes
The default packet count for new cloud path probes has been updated from 11 to 5 for predefined and custom applications for all subscription levels.
[See image.](#packet-count)
To learn more, see [Configuring a Probe](/zdx/configuring-probe) and [Editing a Probe](/zdx/editing-probe).
[]![Default packet count setting](/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-packet-count-add-probe.png)

### Feature Available
#### Time Range Analysis for Poor ZDX Scores
Zscaler Digital Experience (ZDX) helps identify potential reasons for Poor ZDX Scores within a specified time range. Click Analyze Range within the ZDX Score Over Time graph on the user details page to view contributing factors and explanations.
[See image.](#analyze-range)
To learn more, see [Evaluating User Details](/zdx/evaluating-user-details#analyze-range).
[]![Analyze time range for poor ZDX scores](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-analyze-range-button-and-table_0.png)

## June 03, 2022
### Feature Available
#### Monitoring Criteria for ZDX Call Quality Applications
When adding a new tenant in Zscaler Digital Experience (ZDX) Call Quality applications for Microsoft Teams and Zoom, Monitoring Criteria filters are now provided to help identify users who are meeting hosts. Only meetings hosted by these users are monitored.
[See image.](#monitoring-criteria)
To learn more, see [Configuring Microsoft Teams Call Quality for ZDX](/zdx/configuring-microsoft-teams-call-quality-zdx) and [Configuring Zoom Call Quality for ZDX](/zdx/configuring-zoom-call-quality-zdx).
[]![Monitoring Criteria filters when adding a new tenant](/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-msteams-cqm-add-tenant-monitoring-criteria.png)

## May 23, 2022
### Feature Available
#### Analysis for Poor ZDX Scores
Zscaler Digital Experience (ZDX) can now help identify potential reasons for a Poor ZDX Score at a specific date and time. Click Analyze Score within the ZDX Score Over Time graph on the user details page to view factors and explanations for the low score.
[See image.](#analyze-single-pt)
To learn more, see [Evaluating User Details](/zdx/evaluating-user-details#analyze-single).
[]![Analyze button in tooltip of ZDX Score Over Time graph](/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-yengine-analyze-button-and-table2.png)

## May 06, 2022
### Feature Available
#### Admin Access to Zscaler Client Connector Portal
You can now configure admin permissions for Zscaler Client Connector Portal access by using the Add ZDX Role pop-up in Role Management.
[See image.](#ma-portal)
To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
[]![Add ZDX Role modal to configure Zscaler Client Connector Portal permissions](/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-add-role-zccp2.png)

## April 29, 2022
### Feature in Limited Availability
#### ZDX API
Zscaler Digital Experience (ZDX) now supports the use of APIs for programmatic access to ZDX data. This allows you to integrate analytics tools and ITSM solutions. API access requires an API key to authenticate in order to retrieve data.
Contact your Zscaler Account team to request access to the API Key Management feature.
To learn more, see [About the ZDX API](/zdx/about-zdx-api) and [About API Key Management](/zdx/about-api-key-management).

## April 15, 2022
### Feature Available
#### Device Location Icon in Hop View
The cloud path hop view now displays an icon to indicate a device location was determined by latitude and longitude coordinates, rather than IP address.
[See image.](#location-icon)
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).
[]![Example of device location icon in the hop view](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-location-icon.png)

### Feature Available
#### Reverse Traceroute in Cloud Path
The cloud path now displays underlay hops to show the routing path for GRE tunnels.
[See image.](#reverse-tr)
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).
[]![Example of reverse traceroute for GRE tunnels](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-gre-reverse-tr2.png)

## April 13, 2022
### Feature Available
#### ZIA Private Service Edge in Cloud Path
The Zscaler Internet Access (ZIA) Private Service Edge is now displayed in the cloud path hop view for private networks.
[See image.](#zia-pzen)
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard#cloudpath).
[]![Example of ZIA Private Service Edge in hop view](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-zia-pzen_0.png)

## March 18, 2022
### Feature Available
#### UCaaS Monitoring
You can now configure UCaaS Monitoring permissions for access to Zscaler Digital Experience (ZDX) Call Quality applications.
[See image.](#ucaas_monitoring_zdx)
To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
[]![Configure permissions for UCaaS Monitoring](/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-add-role-ucaas2.png)

## March 04, 2022
### Feature Available
#### Baseline for Page Fetch Time
A Zscaler Digital Experience (ZDX) score baseline is now provided in the Page Fetch Time graph on the user details page. For predefined applications, the baseline represents an average score based on device metrics across all organizations. For custom applications, the baseline represents an average score based on device metrics from a given organization.
[See image.](#pft-baseline)
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard#webprobemetrics).
[]![Baseline shown in Page Fetch Time graph](https://help.zscaler.com/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-pft-baseline.png)

### Feature Available
#### Protocol for Adaptive Probes
The Cloud Path Hop View now shows the grouping of protocol with tunnel type for Adaptive probes.
[See image.](#tunnel-protocol)
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard#cloudpath).
[]![Example grouping of protocol with tunnel in hop view](https://help.zscaler.com/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-protocol-leg.png)

## February 09, 2022
### Feature Available
#### NDR Support
The Zscaler Digital Experience (ZDX) cloud path now supports No Default Route (NDR) deployments to the Zscaler cloud.

## February 04, 2022
### Feature Available
#### Messaging for Data Availability
On the User Overview page, messaging has been added to the end of trend lines for Total Active Users and Total Active Devices for the last few minutes if complete data is not yet available from all connected devices.
[See image.](#data-delay)
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).
[]![Tooltip for data ingestion delay](https://help.zscaler.com/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-ingestion-delay2.png)

## January 31, 2022
### Feature Available
#### Support for ZPA Private Service Edge and Web Probe Rate Limiting
Zscaler Digital Experience (ZDX) now supports Zscaler Private Access (ZPA) Private Service Edge in the cloud path and web probe rate limits for internal applications through ZPA. The following versions are required for this ZPA support:
- App Connector: 21.352.1
- Windows: Zscaler Client Connector 3.7.1 (with ZDX Module 3.1 for Windows)
- macOS: Zscaler Client Connector 3.6 (with ZDX Module 3.1 for macOS)
To learn more about ZPA in the cloud path and rate limiting, see [About the Users Dashboard](/zdx/about-users-dashboard) and [About ZDX Web Probe Rate Limiting](/zpa/about-zdx-web-probe-rate-limiting).

### Feature Available
#### Zoom Call Quality for ZDX
Zscaler Digital Experience (ZDX) now supports Zoom Call Quality to monitor calls or meetings among two or more participants in a configured Zoom tenant. The user and device information for call participants is mapped directly to ZDX users and devices. Call Quality works in parallel with cloud path probes and device metrics and events to help you identify issues that are unique to a device, application, or network.
Zoom Call Quality is currently limited by the Zoom API rate limit of 60K probes per day, and may be affected by other Zoom applications using the API.
[See image.](#zoom-card)
To learn more, see [Configuring Zoom Call Quality for ZDX](/zdx/configuring-zoom-call-quality-zdx) and [About Zoom Call Quality for ZDX](/zdx/about-zoom-call-quality-zdx).
[]![Zoom Call Quality application card](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2022/zdx-zoom-card2.png)

## January 14, 2022
### Feature Available
#### ZDX Setup Wizard
As part of the Standard subscription plan, ZDX supports an onboarding wizard for Zscaler Internet Access (ZIA) admins who have full admin and policy access to quickly enable the ZDX service. The wizard also allows admins to add the ZDX admin role to other existing ZIA admins or to new admins. This wizard is now fully supported on all Zscaler clouds for ZIA.
[See image.](#wizard-welcome)
To learn more, see [Using the ZDX Setup Wizard](/zdx/using-zdx-setup-wizard) and [About Notification](/zia/about-notification).
[]![Welcome page of the ZDX Setup Wizard](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/zdx-setup-welcome3.png)
