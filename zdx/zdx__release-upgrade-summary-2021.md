# Release Upgrade Summary (2021)
Source: https://help.zscaler.com/zdx/release-upgrade-summary-2021

This article provides a summary of all new features and enhancements per Zscaler cloud for Zscaler Digital Experience (ZDX). Zscaler will email a notification to your organization's registered support contacts approximately one week before your cloud is upgraded. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** zdxcloud.net, zdxbeta.net
The following service updates were deployed to zdxcloud.net on

## December 16, 2021
### Feature Available
#### Microsoft Teams Call Quality for ZDX
ZDX now supports Microsoft Teams Call Quality to monitor calls or meetings among two or more participants in a configured Microsoft Teams tenant. User and device information garnered from Microsoft for call participants is mapped directly to ZDX users and devices. Call Quality works in parallel with Cloud Path probes and device metrics and events to help you identify issues that are unique to a device, application, or network.
[See image.](#teams-card)
To learn more, see [Configuring Microsoft Teams Call Quality for ZDX](/zdx/configuring-microsoft-teams-call-quality-zdx) and [About Microsoft Teams Call Quality for ZDX](/zdx/about-microsoft-teams-call-quality-zdx).
[![Card for the Microsoft Teams Call Quality app](https://help.zscaler.com/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX-msteams-cqm-card.png)
]

## November 19, 2021
### Feature Available
#### ZDX Setup Wizard
As part of the Standard subscription plan, ZDX now supports an onboarding wizard for Zscaler Internet Access (ZIA) admins who have full admin and policy access to quickly enable the ZDX service. The wizard also allows admins to add the ZDX admin role to other existing ZIA admins or to new admins.
[See image.](#wizard-welcome)
To learn more, see [Using the ZDX Setup Wizard](/zdx/using-zdx-setup-wizard) and [About Notification](/zia/about-notification).
[]![Welcome page of the ZDX Setup Wizard](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/zdx-setup-welcome3.png)

## November 12, 2021
### Feature Available
#### CSV Download from User Overview Page
You can now download a CSV file from the User Overview page. The CSV file reflects the current table view for each ZDX Score category (Poor, Okay, or Good).
[See image.](#csv-download)
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).
[]![Highlights CSV download option on the User Overview page](https://help.zscaler.com/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/zdx-download-icon2.png)

## October 21, 2021
### Feature Available
#### ZPA Support in ZDX
ZDX now supports Zscaler Private Access (ZPA) on Windows platforms to measure internal application performance and display the end-to-end Cloud Path up to the internal application front door. Data is encrypted and stored at rest before being shipped to the ZDX infrastructure using HTTPS. Zscaler Client Connector [version 3.6.1](/zscaler-client-connector/client-connector-app-release-summary-2021?applicable_category=Windows&applicable_version=3.6.1) for Windows and App Connector 21.224.1 are required for this ZPA support.
[See image.](#zpa-cloud-path-rn)
To learn more about ZPA in the Cloud Path and how to configure a probe, see [Evaluating the Cloud Path](/zdx/evaluating-cloud-path) and [Configuring a Probe](/zdx/configuring-probe).
To learn more about deployment recommendations for ZPA to work with ZDX, see [App Connector Deployment Prerequisites](/zpa/connector-deployment-prerequisites).
[![ZPA Public Service Edge shown in Cloud Path](/downloads/zdx/release-notes/release-upgrade-summary-2021/zdx-hop-view-zpa-public.png)
]

## October 01, 2021
### Feature Available
#### Consistent Behavior for Logout and Timeout
When you log out from the ZDX Admin Portal or are logged out because of a session timeout, the Time Range Filter is reset to 2 hours and all other filters are cleared.
When you log in after a session timeout, you will land on the page to which you were navigating when the timeout occurred.
To learn more, see [About the ZDX Admin Portal](/zdx/about-zdx-admin-portal).

### Feature Available
#### Deep Tracing PDF Enhancements
The page layout for Deep Tracing PDF files has been improved to include logical page and line breaks.
To learn more, see [About Deep Tracing](/zdx/about-deep-tracing).

### Feature Available
#### UI Enhancements for Unknown Locations
The geolocations filter on the dashboard and Alerts pages is now streamlined to display only one instance of "Unknown" when city, state, and country are all unknown locations.
[See image.](#geo-dropdown)
To learn more, see [About the ZDX Dashboard](/zdx/about-zdx-dashboard).
[![Example of geolocation filter drop-down showing unknown location](https://help.zscaler.com/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/zdx-geolocation-dropdown.png)
]

## September 17, 2021
### Feature Available
#### Multiple Cloud Support for SAML Login from IdP
In cases where tenants are defined on multiple Zscaler Internet Access (ZIA) clouds and have a common domain, you can now configure an IdP for admins to authenticate with a specific ZIA cloud.
Enter the ZIA cloud domain name (e.g., zscalertwo.net) in the Relay State field of your IdP configuration settings to authenticate with the ZIA cloud. You may need to create an IdP application for each ZIA cloud.

### Feature Available
#### Option to View Current ZDX Score
You can now view the most-current ZDX Score by clicking Current Score, located on the ZDX dashboard, User Overview dashboard, and User details page. The ZDX Score will reflect a time range for the previous 30 minutes.
[See image.](#current-score)
To learn more, see [About the ZDX Dashboard](/zdx/about-zdx-dashboard).
[![Current Score button on ZDX dashboard](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/zdx-current-score-button.png)
]

### Feature Available
#### Time Range Retained for ZDX Score
When you select an application and zoom in to capture a time range within the graph for ZDX Score Over Time, that time range is now retained when navigating to the User Overview and User details pages.
[See image.](#time-range-retained)
To learn more, see [About the Applications Dashboard](/zdx/about-applications-dashboard).
[![User Overview page shows the time range setting retained](https://help.zscaler.com/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX-time-range-retained.png)
]

## August 20, 2021
### Feature Available
#### Enhancements to User Device Events
The user interface for User Device Events has been enhanced to include improved tooltips and the ability to filter device event categories.
[See image.](#events-enhancements)
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).
[![User Device Events graph that shows tooltip and categories](https://help.zscaler.com/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX-user-device-events-tooltip-and-categories.png)
]

### Feature Available
#### Time Zone Added to Dashboard Graphs
The time zone has been added to the beginning and ending of time lines in applicable graphs for the ZDX dashboard, Users dashboard, and Applications dashboard.
[See image.](#time-zone)
[![Example graphs that highlight the time zone designation](https://help.zscaler.com/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX-timezone2.png)
]

### Feature Available
#### Tunnels in Cloud Path Hop View
Tunnel type names have been updated for clarity, and the Hop View now shows a more precise starting point for a tunnel within the cloud path.

### Feature Available
#### User and Application Filters Included in New Tab
When right-clicking the username in the Users Overview or the application name in the Applications Overview, using "Open link in new tab" will now carry over the applicable filters to the new browser tab.
[See image.](#open-link)
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard) and [About the Applications Dashboard](/zdx/about-applications-dashboard).
[![User Overview example that shows how to open link in new tab](https://help.zscaler.com/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX-user-new-tab.png)
]

## July 23, 2021
### Feature Available
#### Edit Protocols for Predefined Cloud Path Probes
Users can now change the protocol port for predefined cloud path probes after initial configuration.
[See image.](#EditCloudPath)
To learn more, see [About Probes](/zdx/about-probes).
[![Edit Cloud Path Probe Protocol](/sites/default/files/downloads/zdx/configuration/probes/about-probes/Edit-CloudPath-Probe_Protocol-dropdown-edit.png)
]

### Feature Available
#### SAML Support for ZDX Admin Login
You can now configure SAML authentication for ZDX admins to log in to the ZDX Admin Portal directly from your single sign-on provider portal. An IdP (such as ADFS or Okta) must already be configured for your organization.
[See image.](#saml-auth)
To learn more, see [Configuring SAML for ZDX Admins](/zdx/configuring-saml-zdx-admins).
[![Screenshot of the SAML Authentication for Administrators section on the Administrator Management page](https://help.zscaler.com/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX-SAML-Authentication-For-Administrators-Section3.png)
]

### Feature Available
#### ZDX Roles for Deep Tracing, Alerts, and Webhooks
Admin roles can now be configured in ZDX for specific permissions to access, configure, and manage Deep Tracing, Alerts, and Webhooks.
To learn more, see [Adding ZDX Roles](https://help.zscaler.com/zdx/adding-zdx-roles).

## June 18, 2021
### Feature Available
#### ZDX Score for Alert Configuration
You can now create Alert rules for your ZDX Score. If you configure a new rule and choose ZDX Score as your Rule Type, you can set criteria to be alerted when the score changes.
[See image.](#ZDX-Score)
To learn more, see [About Alerts](/zdx/about-alerts) and [Configuring a Rule](/zdx/configuring-rule).
[![ZDX Score Rule Type](/sites/default/files/downloads/zdx/configuring-rule/Add-New-Alert-Rule_Rule-Type_ZDX-Score_annotated.png)
]

## June 11, 2021
### Feature Available
#### Adaptive Mode Protocol for Probe Configuration
You can now configure probes using the Adaptive mode protocol option. If you choose Adaptive mode, the best protocol for each leg in the cloud path is selected via an auto-discovery process.
[See image.](#Add-Probe_Protocol_Adaptive)
To learn more, see [About Adaptive Mode](https://help.zscaler.com/zdx/about-adaptive-mode).
[![Add a new probe and choose from the protocol options: Adaptive, ICMP, TDP, UDP](/sites/default/files/downloads/zdx/configuration/probes/configuring-probe/Add-New-Probe_Protocol_Adapt-ICMP-TDP-UDP.png)
]

## May 28, 2021
### Feature Available
#### Device and Device Metrics Selections in the User Page Retained
The device selected in the User Devices Section as well as the Device Health metrics selections in the User page will be retained across navigation and login.
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).

### Feature Available
#### Enhanced User Devices Section in the User Page
The User Devices section in the User page can now display information for multiple devices, as well as additional network, hardware, and software device details.
[See image.](#UserDevices)
[]![View Device Details in the User Page](/sites/default/files/downloads/zdx/analytics/about-users-dashboard/ZDX_ShowDeviceDetails1_LU.png)
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).

### Feature Available
#### Filter Separation between the Probe and the Dashboard pages
Filters applied on the Probe configuration page will not carry over to the Users dashboard page and vice versa.
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard) and [About Probes](/zdx/about-probes).

### Feature Available
#### Maximum of the Zscaler Latency and Egress ISP in the Cloud Path
The maximum of the Zscaler latency to the hop on either side will be indicated above the ZIA Public Service Edge icon in the Cloud Path section. Clicking the magnifying glass icons displays the expanded view with the maximum Zscaler latency on top of the relevant hop. The egress service provider will also be displayed under the egress node.
[See image.](#MaxLatency)
[]![View Maximum Zscaler Latency in the Cloud Path ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/zdx_MaxLatencyonZEN_RN.png)
![Maximum Zscaler Latency in the Cloud Path](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/zdx_MaxLatencyonZEN1.png)
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).

## May 07, 2021
### Feature Available
#### Cloud Path Enhancements
The following enhancements are now available in the Cloud Path
Selectable Latency Graphs per Leg in the Cloud Path
Latency over the different legs will now display in the Cloud Path section in the User page. This option can also be selected in the checkbox below the graph.
[See image.](#LatencyinLegs)
[![View Latency over the Legs in the Cloud Path ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/zdx_LatencyOverLegs.png)
]
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).
Location Enhancements
Service provider information will display for hops in the Cloud Path. Geo information and the Zscaler location will display for the device, and geo information will also display for the Zscaler node in both the Hop View and the Command Line View.
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).

### Feature Available
#### User Search Enhancements
A recently deleted user profile will now be displayed in the User Search results as well as in the search history.
[See image.](#DeletedUser)
[![Deleted User in the User Search ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/zdx_DeletedUser.png)
]
To learn more, see [Using User Search in the ZDX Admin Portal](/zdx/using-user-search-zdx-admin-portal).

### Feature Available
#### Users Dashboard Optimization
The ZDX score processing on the Users Dashboard is now optimized so that the score rendering on the page loads faster for users.
[See image.](#UserDashboardOptimize)
[![Optimized rendering of ZDX Score on Users Dashboard ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/zxd_UserPageOptimize_RN.png?1619653271)
]
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).

## April 16, 2021
### Feature Available
#### Cloud Path Probe Configuration Enhancements
When configuring a cloud path probe for predefined applications, following a web probe is the default value. It is also recommended when configuring cloud path probes for custom applications.
To learn more, see [Configuring a Probe](/zdx/configuring-probe).

### Feature Available
#### Deep Tracing Session Results Enhancements
The Deep Tracing session results charts will now display raw metrics without aggregation. If there is no data, this will be indicated by a gap in the charts as well as an error message.
[See image.](#DTSessionCharts)
[![Deep Tracing Session Charts ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/zdx_DTCharts_RN.png)
]
To learn more, see [Viewing Deep Tracing Session Results](/zdx/viewing-deep-tracing-session-results).

### Feature Available
#### Location Management in the ZDX Admin Portal
Admins can now view the Location Management page in the ZDX Admin Portal by going to Administration > Location Management.
[See image.](#LocationManagement)
[![Location Management on the ZDX Admin Portal ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/zdxLocation_RN.png)
]
To learn more, see [About Locations](/zdx/about-locations).

## April 02, 2021
### Feature Available
#### Alerts Page Enhancements
The information in the Alerts page is now organized into Ongoing alerts and Alert History tabs for easy access to alert details.
[See image.](#AlertsRefactoring)
[![Alerts Page in ZDX ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX_AlertsREfactoring_RN.png)
]
To learn more, see [About Alerts](/zdx/about-alerts).

### Feature Available
#### Cloud Path Enhancements
The following enhancements are now available in the Users Dashboard.
View Cloud Path from the Zscaler Client Connector to ZPA
When accessing an internet application, you can see the cloud path from the Zscaler Client Connector to the application and if there is a ZIA Public Service Edge in the path, that will also be displayed in the User page. If a private application is accessed, you can view the cloud path from the Zscaler Client Connector to the ZPA Public Service Edge or the ZPA Private Service Edge.
[See image.](#ZDXZPA)
[![Viewing Private Applications in the Cloud Path ](/sites/default/files/downloads/zdx/analytics/about-users-dashboard/ZDX_ZPAinCloudPath.png)
]
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).
Differential Latency in the Cloud Path
You can now see differential latency over the different legs of the cloud path and the leg with the highest latency displays in orange.
[See image.](#DiffLatency)
[![Differential Latency in the Cloud Path](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/Difflatency1.png?1617376347)
]
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).
Cloud Path Error Messages in the Command Line View
If there are any errors in the cloud path, they will now be indicated by an icon next to the IP address in the Command Line View. Clicking the icon will display the error message.
[See image.](#ErrMessCLV)
[![Cloud Path Errors on Command Line View](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/Errors%20on%20Command%20Line%20view.png?1617376548)
]
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard) and [Cloud Path Errors](/zdx/cloud-path-errors).

### Feature Available
#### Location Enhancements
The following location enhancements are now available.
Hierarchical Location Display in the ZDX Dashboard
In the ZDX dashboard, the Active Geolocations filter now offers a hierarchical display of locations for easy selection and filtering.
[See image.](#GeolocationDisplay)
[![Active Geolocations Hierarchical Filter Options  ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX_Country.Regionfilters.png?1617378215)
]
To learn more, see [About the ZDX Dashboard](/zdx/about-zdx-dashboard).
Regions by ZDX Score Map in the Applications Page
The Regions by ZDX Score map is now available in the Applications page and provides greater functionality for viewing details and filtering information.
[See image.](#ZDXScoreMap)
[![Regions by ZDX Score Map on Applications Dashboard ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX_RegionsbyZDXScore.png)
]
To learn more, see [About the Applications Dashboard](/zdx/about-applications-dashboard).

### Feature Available
#### Smooth ZDX Score in the User Page
In the ZDX Score Over Time graph in the User page, the Smooth ZDX Score, which uses historical data to reduce short-term variations in the ZDX Score, displays. You can also select the checkbox below the graph to view the ZDX score.
[See image.](#SmoothZDXScore)
[![Smooth ZDX Score in the User Page](/sites/default/files/downloads/zdx/analytics/about-users-dashboard/SmoothandZDXScore1.png)
]
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).

## March 05, 2021
### Feature Available
#### Cloud Path Error Messages in the Users Page
In the Cloud Path section of the Users Page, icons will display in case of any errors. Click the link below the error message to view further details.
[See image.](#CloudPathErrors)
[![Cloud Path Error Messages ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX_UpdatedCloudPathErrors1.png)
]
To learn more, see [Cloud Path Errors](/zdx/cloud-path-errors).

### Feature Available
#### Enhanced User Search
The User Search in the ZDX Admin Portal will now display the 10 most relevant results of a search. Clicking Load More will display 10 more results consecutively till complete.
[See image.](#EnhancedUserSearch)
[![Enhanced User Search ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX_UserSearch.png)
]
To learn more, see [Using User Search in the ZDX Admin Portal](/zdx/using-user-search-zdx-admin-portal).

## February 19, 2021
### Feature Available
#### Deep Tracing for macOS Devices
Users with macOS devices running Zscaler Client Connector 3.0.0.93 (and later) and ZDX 2.0.0.2 (and later) can now start Deep Tracing sessions in the ZDX Admin Portal.
[See image.](#DeepTracingmacOS)
[![Deep Tracing for macOS Devices ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX_ZApp_macOS.png)
]
To learn more, see [About Deep Tracing](/zdx/about-deep-tracing).

### Feature Available
#### Predefined applications for Microsoft Teams and Zoom
Microsoft Teams and Zoom are now predefined applications and can be seen in the Applications tab of the Configurations page. Onboarding these applications will automatically enable web and cloud path probes for them in the ZDX Admin Portal.
[See image.](#MSTeams_Zoom)
[![Microsoft Teams and Zoom in the ZDX Admin Portal ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX_MSTeams_Zoom_RN.png)
]
To learn more, see [About Applications](/zdx/about-applications).

## February 05, 2021
### Feature Available
#### Change Password from the Account Page
ZDX admins can now change their password from their account page. An update made here will apply to both the ZDX and ZIA Admin Portals.
[See image.](#ChangePassword)
[![Change Password from ZDX Account Page ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX_ChangePassword.png)
]
To learn more, see [Customizing Your Admin Account Settings](/zdx/customizing-your-admin-account-settings).

### Feature Available
#### Cloud Path Enhancement
The Cloud Path section of the Users Dashboard will now show the location of the egress, ZIA Public Service Edge, and destination in the Hop View.
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).

### Feature Available
#### EUSA in the ZDX Admin Portal
An End User Subscription Agreement (EUSA) appears in the ZDX Admin Portal when you log in for the first time. Per organization, one admin is required to accept the agreement. You will have Read-Only access in the Portal till the EUSA is accepted.
[See image.](#EUSA)
[![EUSA in the ZDX Admin Portal ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/EUSA%20.png)
]
To learn more, see [About the ZDX Admin Portal](/zdx/about-zdx-admin-portal).

## January 22, 2021
### Feature Available
#### Cloud Path Enhancement
The Cloud Path section of the Users Dashboard will now show a 4-digit number for the ZIA Public Service Edge (formerly known as Zscaler Enforcement Node or ZEN) in the Hop View and Cloud Path View. This hash value will help Zscaler Support locate and troubleshoot any issues faster.
[See image.](#ZENInternalID)
To learn more, see [About the Users Dashboard](/zdx/about-users-dashboard).
[![Internal ID for the ZIA Public Service Edge in Cloud Path ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX_ZEN_ID_HopView.png)
]

### Feature Available
#### Password Expiration in the ZDX Admin Portal
You can now configure Password Expiration for ZDX admins in the ZDX Admin Portal or the ZIA Admin Portal. The latest password expiration settings configured in either portal will apply in both locations.
[See image.](#PasswordExpiration)
[![Password Expiration in ZDX ](/sites/default/files/downloads/zdx/release-notes/release-upgrade-summary-2021/ZDX_SettingPasswordExpiration.png)
]
To learn more, see [Configuring Password Expiration](/zdx/configuring-password-expiration).

## January 08, 2021
### Feature Available
#### Web Probe Updates
Page Fetch Time, collected by the web probes, will now only request the top-level page document and will not request embedded links contained in the web page. This will provide users with a metric similar to other developer tools.
[See image.](#PFTinZDX)
To learn more, see [About Probes](https://help.zscaler.com/zdx/about-probes).
[![Page Fetch Time in ZDX](/sites/default/files/downloads/zdx/release-upgrade-summary-2020/ZDX_PFT_RN1.png)
![Page Fetch Time in Chrome Dev Tools](/sites/default/files/downloads/zdx/release-upgrade-summary-2020/ZDX_PFT_RN2.png)
]
