# Release Upgrade Summary (2025)
Source: https://help.zscaler.com/zpa/release-upgrade-summary-2025

This article provides a summary of all new features and enhancements per Zscaler cloud for the ZPA Admin Portal. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).
When Zscaler cloud and Admin Portal updates are deploying, some functionality will not be available until the deployment process completes.

**Clouds:** private.zscaler.com, zpatwo.net, zpabeta.net, zpapreview.net
The following service updates were deployed to private.zscaler.com on

## November 20, 2025
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 8.x and 9.x, and Private Cloud Controller and Network Connector RPM packages for Red Hat Enterprise Linux 9.x.
You can download the Manager software for [App Connectors](/zpa/app-connector-deployment-guide-linux), [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux), [Private Cloud Controllers](/zpa/private-cloud-controller-deployment-guide-linux), or [Network Connectors](/zpa/network-connector-deployment-guide-linux) from our repository. The Manager software version is 25.49.4.
To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades).

## November 14, 2025
### Feature Available
#### Resolved Issues
A fix was released to address a validation issue when using the 14 Days preset date range in the User Activity diagnostics.
To learn more, see [Accessing User Activity Diagnostics](/zpa/accessing-user-activity-diagnostics).

## November 13, 2025
### Feature Available
#### Agent Manager Status and Version for Microsegmentation
The Agent Manager Status and Agent Manager Version are available to view in the Agent table, as well as the expanded Agent Details section for each agent.
[See image.](#Agent-Status-Agent-Manager)
To learn more, see [About Agents](https://help.zscaler.com/zpa/about-agents).
[]![A view of the Agents page along with an expanded view of details for one agent. ](/sites/default/files/downloads/zpa/microsegmentation/about-the-agents-page/Agent-Manager-Version_and_Agent-Manager-Status_Agent-Table.png)

### Feature Available
#### App Connector GCP and Azure Image Support for Automated OS Security Updates, ZPA Manager Software Updates, and OAuth 2.0 Enrollment Support
Updated Red Hat Enterprise Linux 9 App Connector images are available to support upcoming releases of automated OS security updates, ZPA Manager software updates, and OAuth 2.0 enrollment support. The following updated images are available:
- Google Cloud Platform
- Microsoft Azure
To learn more, see [ZPA App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform).

## November 12, 2025
### Feature Available
#### AWS Prebuilt Image Support for Network Connector
A new Network Connector image is available for Amazon Web Services (AWS) that includes support for upcoming VPN redundancy features.
If you want to enable firewalld on a system running the Network Connector, you must perform additional steps to modify the firewall filter rule for VPN redundancy to work properly.
To learn more, see [Network Connector Deployment Prerequisites](/zpa/network-connector-deployment-prerequisites) and [Network Connector Software by Platform](/zpa/network-connector-software-platform).

## November 07, 2025
### Feature Available
#### VPN Service Edge Software Update
An update was released to fix an issue where VPN Service Edge encountered an error condition when a large number of network segments were configured.
To learn more, see [About VPN Service Edges](/zpa/about-vpn-service-edges).

## November 05, 2025
### Feature Available
#### App Connector AWS Image Support for Automated OS Security Updates, ZPA Manager Software Updates, and OAuth 2.0 Enrollment Support
An updated Red Hat Enterprise Linux 9 App Connector AWS image is available to support upcoming releases of automated OS security updates, ZPA Manager software updates, and OAuth 2.0 enrollment support.
To learn more, see [ZPA App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform).

## November 04, 2025
### Feature Available
#### Events and Notifications Enhancements
The Notifications service supports Network Connectors when configuring a notification. The following events are supported for Network Connectors:
-
Last Component Disconnected
-
Upgrade Complete
-
Upgrade Failed
-
Outdated Component Manager Version
-
Provisioning Key Usage Exceeded
-
Enrollment Completed
-
Enrollment Failed
-
Enrollment Certificate Expired
-
Control Connection Disconnected
-
CPU Starvation
[See image.](#pcc)
[]![Private Cloud Controller Notification Events in the ZPA Admin Portal](/sites/default/files/downloads/zpa/business-continuity-management/configuring-business-continuity-settings/zpa-vpn-network-conn-notification.png)

## October 31, 2025
### Feature Available
#### App Connector OVA Image Support for Automated OS Security Updates, ZPA Manager Software Updates, and OAuth 2.0 Enrollment Support
Updated Red Hat Enterprise Linux 9 App Connector OVA images are available to support upcoming releases of automated OS security updates, ZPA Manager software updates, and OAuth 2.0 enrollment support. The following updated images are available:
- Nutanix AHV
- VMware
To learn more, see [ZPA App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform).

### Feature Available
#### VPN Service Edge Software Update
An update was released to fix an issue where the VPN Service Edge dropped packets with asymmetric routing.
To learn more, see [About VPN Service Edges](/zpa/about-vpn-service-edges).

## October 29, 2025
### Feature Available
#### Resolved Issues
Multiple fixes for agent version zms-1.6.3 have been released to address several issues. Zscaler recommends upgrading to this agent version to avoid any disruption to traffic due to these issues:
- An issue was fixed in the agent where customers would continue to see flow logs from agents after they were disabled by an admin.
- An issue was fixed in the agent where it would fail to reconnect if it detected any network configuration changes after a host reboot. This might continue to occur in cases where a host is configured with one or more virtual interfaces (i.e., in Microsoft clusters, Ubuntu hosts, etc.).
- Agent stability issues were fixed, such as inaccurate service status and configured exceptions that required additional admin management.
- An issue was fixed where an agent, when installed on a supported OS and on a bare metal server, was reported as an Unknown type, failing to be recognized as a valid resource for the applied policy.
- An issue was fixed where the agent policy enforcement engine dropped outbound packets if interleaved between outbound and inbound packet flows.
- An issue was fixed where the agent policy enforcement engine was leaking memory after rule validation against certain flows.

## October 27, 2025
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 8.x and 9.x, and Private Cloud Controller and Network Connector RPM packages for Red Hat Enterprise Linux 9.x.
You can download the Manager software for [App Connectors](/zpa/app-connector-deployment-guide-linux), [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux), [Private Cloud Controllers](/zpa/private-cloud-controller-deployment-guide-linux), or [Network Connectors](/zpa/network-connector-deployment-guide-linux) from our repository. The Manager software version is 25.48.4.
To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades).

## October 13, 2025
### Feature Available
#### Filtered Reports for Application and User Group Relationships
You can download reports for filtered application segments on the Application and User Group Relationships insights page.
[See image.](#filteredReportDownload)
To learn more, see [Viewing Application and User Group Relationships](/zpa/viewing-application-and-user-group-relationships).
[]![Downloading a filtered report ](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-application-user-relationships-insights-filtered-report-download.png)

## October 09, 2025
### Feature Available
#### GCP Prebuilt Image Support for Network Connector
A new Network Connector image is available for Google Cloud Platform (GCP) that includes support for upcoming VPN redundancy features.
If you want to enable firewalld on a system running the Network Connector, you must perform additional steps to modify the firewall filter rule for VPN redundancy to work properly.
To learn more, see [Network Connector Deployment Prerequisites](/zpa/network-connector-deployment-prerequisites) and [Network Connector Software by Platform](/zpa/network-connector-software-platform).

## October 08, 2025
### Feature in Limited Availability
#### High Availability and Redundancy in VPN (for Legacy Apps)
VPN (for Legacy Apps) uses Border Gateway Protocol (BGP) to ensure high availability and fault tolerance by providing alternate paths to reach applications during Network Connector node failures and Network Connector to VPN Service Edge path or link failures. If a failure occurs on a Network Connector within a Network Connector group, VPN Service Edges use BGP to reroute traffic to another Network Connector for the specific IP Address subnet or FQDN.
VPN redundancy and the Admin Probe are supported on VPN Service Edges and Network Connectors starting from version 25.46.2 or later.
This release includes the following enhancements for high availability and redundancy:
-
Support is available for configuring a global BGP for VPN Service Edges and Network Connectors, including options to use BGP Timers or bidirectional forwarding detection (BFD) to detect session failures. You can also override the global BGP setting when adding or editing individual VPN Service Edges and Network Connectors.
[See image.](#global-bgp)
-
Options for adding an external router to the Network Connector for BGP configuration are available.
[See image.](#external-router)
-
An option to advertise LAN segments locally was added for Network Connector groups. When disabled, you can select which routers to use for the Network Connector and set options such as Multi-hop to peer with routers that are multiple network hops away.
[See image.](#advertise-lan-segment)
- Support for selecting multiple Network Connector groups in Network segments is available. To learn more, see [Configuring Network Segments](/zpa/configuring-network-segments) and [Editing Network Segments](/zpa/editing-network-segments).
[See image.](#add-network-segment)
-
A new BGP Peers page allows you to view the routing of Network Connectors for each VPN Service Edge to help troubleshoot, and it also shows peers and connection information.
[See image.](#dashboard)
-
A new Network Connector Throughput chart on the Network Connectors Dashboard lets you monitor throughput to determine when more Network Connectors are needed. To learn more, see [Viewing the Network Connectors Dashboard](/zpa/viewing-network-connectors-dashboard).
[See image.](#nc-dashboard)
-
A new Redundant Mode option is available to help determine if redundancy is enabled during troubleshooting. You can view this option when expanding a group on the Network Connector Groups page, or by adding the column on the VPN Service Edges page.
[See image.](#redundant-mode-table)
-
You can execute commands with VPN sessions for VPN Service Edges, Network Connectors, and Network Connector groups on the VPN Support Information page.
[See image.](#Support)
- Outbound VPN tunnels can establish a gateway to VPN Service Edges using a port range from 51820 to 53000. To learn more, see [Network Connector Deployment Guide for Linux](/zpa/network-connector-deployment-guide-linux).
[]![External Routers Page in VPN (for Legacy Apps)](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-vpn-external-routers-w-steps.png)
[]![Edit Network Connector Group Page in VPN (for Legacy Apps)](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-vpn-advertise-lan-segments.png)
[]![Add Network Segment Page in VPN (for Legacy Apps)](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-vpn-add-network-segment_2.png)
[]![BGP Peers Page on the VPN (for Legacy Apps) Dashboard](/sites/default/files/downloads/zpa/release-notes/zpa-network-connector-release-notes/network-connector-release-summary-2025/zpa-vpn-dashboard-bgp-peers.png)
[]![Network Connector Throughput Chart in the Network Connectors Dashboard](/sites/default/files/downloads/zpa/release-notes/zpa-network-connector-release-notes/network-connector-release-summary-2025/zpa-vpn-dashboard-throughput.png)
[]**Example BGP Configuration Page:**
**![Example BGP Configuration Page for VPN (for Legacy Apps)](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/ZPA-vpn-bgp-configuration.png)
**
[]
[]![Redundant Mode Column in VPN (for Legacy Apps)](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-vpn-nc-redundant-mode_1.png)
[]![The VPN Support Information page in the ZPA Admin Portal](/sites/default/files/downloads/zpa/vpn-legacy-apps/accessing-and-viewing-vpn-support-information/Update%20full%20page.png)

## October 06, 2025
### Feature Available
#### Agent Connection Status Log Updates for Microsegmentation
The Agent Connection Status Logs have been updated to specify the different reasons why an agent failed to deploy or upgrade.
To learn more, see [About Agent Connection Status Logs](https://help.zscaler.com/zpa/about-agent-connection-status-logs).

### Feature Available
#### Agent Groups for Resource Group Environment in Microsegmentation
When configuring resource groups, you can add an Agent Group as an option for Dynamic Criteria. This is listed under a new category named ZMS.
[See image.](#ZMS-option)
To learn more, see [Configuring Resource Groups](https://help.zscaler.com/zpa/configuring-resource-groups).
[]![A view of the Criteria section and the new ZMS option for Dynamic Membership. ](/sites/default/files/downloads/zpa/microsegmentation/resource-management/configuring-resource-groups/Add-New-Resource-Group_Criteria_Dynamic-Membership_ZMS_Agent-Group_release-notes.png)

### Feature Available
#### Custom Timestamp Tool for Analytics in Microsegmentation
A customizable timestamp selector tool has been added for the Analytics Logs tables in Microsegmentation. This is available for Flow Logs, Agent Telemetry, Agent Connection Status Logs, and Event Logs.
[See image.](#custom-timestamp-tool)
To learn more, see [About Flow Logs](https://help.zscaler.com/zpa/about-flow-logs), [About Agent Connection Status Logs](https://help.zscaler.com/zpa/about-agent-connection-status-logs), [About Agent Telemetry](https://help.zscaler.com/zpa/about-agent-telemetry), and[ About Event Logs](https://help.zscaler.com/zpa/about-event-logs).
[]![The new custom timestamp tool.](/sites/default/files/downloads/zpa/microsegmentation/about-flow-logs-page/Custom-Timestamp-Tool.png)

### Feature Available
#### Initial Target Version in Microsegmentation
You can specify the initial target version of the agent for an agent group. This means that whenever you start the agent, it automatically checks to see if it needs to update itself to the target version you specify, and apply the update if needed.
[See image.](#Custom-Agent-Upgrade)
To learn more, see [Configuring Agent Groups](https://help.zscaler.com/zpa/configuring-agent-groups).
[]![The new custom agent upgrade option. ](/sites/default/files/downloads/zpa/microsegmentation/configuring-agent-groups/Custom-Agent-Upgrade_Target-Version-text.png)

### Feature Available
#### Manual Agent Upgrade Option for Microsegmentation
You can manually upgrade your agents either individually or by initiating an Agent Group upgrade. You can find the Upgrade Now button in the Actions column of the Agents page or Agent Groups page.
[See image.](#Upgrade-Now-button)
To learn more, see [About Agents](https://help.zscaler.com/zpa/about-agents).
[]![The new Upgrade Now button in the Actions column.](/sites/default/files/downloads/zpa/microsegmentation/about-agents-page/Manual-Agent-Upgrade.png)

### Feature in Limited Availability
#### API Discovery for AppProtection
API Discovery Insights provides you with deeper insight into API logs and API users for AppProtection. The analytics for API Discovery Insights can be viewed on the AppProtection Diagnostics page using the API Insight filter. API Discovery is supported on the [Manager software version 25.44.6](/zpa/release-upgrade-summary-2025?applicable_category=private.zscaler.com&deployment_date=2025-06-03&id=1528903).

## October 03, 2025
### Feature in Limited Availability
#### Backup Support for Private Cloud Controllers
Users can schedule a maximum of 100 backup copies of the configuration and policy downloaded by Private Cloud Controllers to improve reliability and availability. You can restore a backup using a script.
[See image.](#backup)
To learn more, see [Configuring Business Continuity Settings](/zpa/configuring-business-continuity-settings).
[]![Business Continuity Backup in the ZPA Admin Portal](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-business-continuity-backup-setting.png)

### Feature in Limited Availability
#### Business Continuity Updates
Business Continuity includes the following updates:
-
A manual override is available to force Private Cloud Controllers, Private Service Edges, and App Connectors into Business Continuity mode. This option is available when editing a Private Cloud.
[See image.](#forcebc)
To learn more, see [Editing Private Clouds](/zpa/editing-private-clouds).
-
The Private Clouds page includes a new column that indicates whether Force Business Continuity Mode is enabled. You can also expand the row to view the reconnect interval and the date and time that Force Business Continuity started.
[See image.](#forcebc-col)
To learn more, see [About Private Clouds](/zpa/about-private-clouds).
-
Existing IdP configurations can be used to authenticate users during Business Continuity.
[See image.](#existing-idp)
To learn more, see [Configuring Business Continuity Settings](/zpa/configuring-business-continuity-settings).
- The Primary Channel Control Path was moved from the Business Continuity Settings page to the Private Cloud page. To learn more, see [Configuring Private Clouds](/zpa/configuring-private-clouds).
-
Last sync times are available for Private Cloud Controllers on the Private Cloud Controllers page. The Policy and Configuration Sync indicates the last time the policy and configuration database was synchronized with the Private Cloud Controller.
[See image.](#PCCsync)
To learn more, see [About Private Cloud Controllers](/zpa/about-private-cloud-controllers).
-
You can create a Private Service Edge group specifically for Business Continuity or Disaster Recovery. When enabled, Private Service Edges in this group are not used for user redirection except when Business Continuity or Disaster Recovery is in effect, or when a redirection policy is configured with the Private Service Edge group.
[See image.](#pse-exclusive)
To learn more, see [Configuring Private Service Edges](/zpa/configuring-service-edges).
[]
![Edit Private Cloud window with Force Business Continuity Mode Option](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-edit-private-cloud-rn_1.png)
[]![ZPA Business Continuity Private Clouds Page](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-pcc-forcebc-private-cloud.png)
[]![Existing IdP for Authentication in Business Continuity](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-business-continuity-settings-existing-idp.png)
[]![Sync Information on the Private Cloud Controller Page in the ZPA Admin Portal](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-private-cloud-controllers-page-sync-fields.png)
[]![Edit Private Service Edge Window with Option to Use Exclusively for Business Continuity](/sites/default/files/downloads/zpa/business-continuity-management/private-cloud-controllers/restoring-business-continuity-backups/zpa-pse-exclusive-to-bc.png)

### Feature in Limited Availability
#### Private Cloud Controller Support for Remote Troubleshooting
You can create sessions for Private Cloud Controllers for remote troubleshooting on the Support Information page of the ZPA Admin Portal.
[See image.](#addSessionPcc)
To learn more, see [Accessing and Viewing Support Information](/zpa/accessing-and-viewing-support-information).
[]![Add Session Drawer in the ZPA Admin Portal](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-support-information-pcc-support-release-note2.png)

### Feature in Limited Availability
#### Support for Private Cloud Controllers in the Notifications Service
The Notifications service supports Private Cloud Controllers when configuring a notification. The following events are supported for Private Cloud Controllers:
- Control Connection Disconnected
- CPU Starvation
- Enrollment Completed
- Invalid System Listen IP Configuration
- Last Component Disconnected
- Outdated Component Manager Version
- Provisioning Key Utilization Exceeded Limit
- Upgrade Complete
- Upgrade Failed
[See image.](#addNotificationPcc)
To learn more, see [Configuring Notifications](/zpa/configuring-notifications).
[]![Add Notification Page in the ZPA Admin Portal](/sites/default/files/downloads/tech-pubs-drafts/zpa-draft-articles/configuring-notifications-doc-57271/zpa-add-notifications-page-release-note.png)

## October 01, 2025
### Feature Available
#### Default Filter Operator in Diagnostics
You can configure the default filter operator in the diagnostics settings.
[See image.](#defaultFilterOperator)
To learn more, see [Configuring Diagnostics Settings](/zpa/configuring-diagnostics-settings).
[]![Settings drawer in the diagnostics](/sites/default/files/downloads/tech-pubs-drafts/configuring-diagnostics-settings-doc-60060/zpa-diagnostics-settings-drawer.png)

### Feature Available
#### Deleting Disabled IdP Configurations for ZIdentity Admin Migration
Disabled admin IdP configurations that are migrated to ZIdentity will be permanently deleted after 30 days after migration. This only applies to admins that are subscribed to ZIdentity for users.
[See image.](#idpDeletionWarning)
To learn more, see [About IdP Configuration](/zpa/about-idp-configuration) and [What Is ZIdentity?](/zidentity/what-zidentity)
[]![Disabled IdP warning](/sites/default/files/downloads/tech-pubs-drafts/zpa-draft-articles/about-idp-configuration-doc-59898/zpa-disabled-idp-deletion-release-note.png)

### Feature Available
#### Source IP Address Filter in User Activity Diagnostics
You can filter by Source IP Address in the user activity diagnostics.
[See image.](#sourceIpFilter)
To learn more, see [Accessing User Activity Diagnostics](/zpa/accessing-user-activity-diagnostics#filters).
[]![Filter by Source IP Address](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-user-activity-diagnostics-source-ip-address-filter.png)

## September 29, 2025
### Feature Available
#### Scheduled VPN Service Edge Software Updates
This release includes the following enhancements for scheduling updates for VPN Service Edges:
- When adding a VPN Service Edge, you can schedule when a VPN Service Edge software update occurs to avoid service interruptions.
Zscaler strongly recommends scheduling updates to avoid service interruption when the device reboots during a software update.
[See image.](#software-updates)
To learn more, see [Configuring VPN Service Edges](/zpa/configuring-vpn-service-edges).
-
You can edit the day and time the existing VPN Service Edge software is updated from the Edit VPN Service Edge drawer.
[See image.](#edit-updates)
To learn more, see [Editing VPN Service Edges](/zpa/editing-vpn-service-edges).
-
A banner also appears when logging in to the ZPA Admin Portal to recommend that you schedule updates for each VPN Service Edge to avoid service interruptions. If an update window is not set, the software updates on Sunday at 2:00 AM UTC.
[See image.](#update-banner)
To learn more, see [About VPN Service Edges](/zpa/about-vpn-service-edges).
[]![VPN Service Edge Software Update in VPN (for Legacy Apps) in the ZPA Admin Portal](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-vpn-service-edge-add-update_2.png)
[]![Editing a VPN Service Edge Software Update in VPN (for Legacy Apps) in the ZPA Admin Portal](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-vpn-edit-service-edge_3.png)
[]![VPN Service Edge Update Banner for VPN (for Legacy Apps)](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-vpn-service-edge-upgrade-banner_0.png)

## September 23, 2025
### Feature Available
#### Azure Prebuilt Image Support for Network Connector
A new Network Connector image is available for Microsoft Azure that includes support for upcoming VPN redundancy features.
If you want to enable firewalld on a system running the Network Connector, you must perform additional steps to modify the firewall filter rule for VPN redundancy to work properly.
To learn more, see [Network Connector Deployment Prerequisites](/zpa/network-connector-deployment-prerequisites) and [Network Connector Software by Platform](/zpa/network-connector-software-platform).

### Feature Available
#### Manager Software Updates
A recommended update was released that ensures that if an OS upgrade is successful, and any underlying libraries that might be used by the Manager software are changed, the Manager software immediately restarts to make sure that there aren't any dependency errors. This release also includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 8.x and 9.x.
You can download the Manager software for [App Connectors](/zpa/app-connector-deployment-guide-linux) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux) from our repository. The Manager software version is 25.47.3.
To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades).

### Feature Available
#### Resolved Issues
Resolved a rare root password expiration condition for 2024.11 and 2024.12 images when upgrading to the latest ZPA Manager software release.
To learn more, see [Understanding the Manager Software](/zpa/understanding-manager-software).

## September 18, 2025
### Feature Available
#### Notifications Service Updates
The following updates were made to the notifications service:
- The Disk Space Exceeded Limit event threshold was increased from 1024 MB to 2048 MB.
- The Enrollment Certificate Expired and Enrollment Failed events were added for App Connectors and ZPA Private Service Edges.
To learn more, see [Configuring Notifications](/zpa/configuring-notifications#events).

### Feature in Limited Availability
#### Privileged Approval Request Email Notifications
When you add or edit a privileged portal for Privileged Remote Access (PRA), you can add email addresses to notify administrators when a privileged approval request has been created, approved, and rejected. To use this feature, you must have an access policy that allows privileged approvals and a privileged portal policy with Request Approvals and Review Approvals enabled.
To learn more, see [Configuring Privileged Portals](/zpa/configuring-privileged-portals).

## September 12, 2025
### Feature Available
#### Manager Software Updates Version
A recommended update was released that ensures that if an OS upgrade is successful, and any underlying libraries that might be used by the Manager software are changed, the Manager software immediately restarts to make sure that there aren't any dependency errors. This release also includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 8.x and 9.x.
You can download the Manager software for [App Connectors](/zpa/app-connector-deployment-guide-linux) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux) from our repository. The Manager software version is 25.46.3.
To learn more, see [Understanding the Manager Software](/zpa/understanding-manager-software).

## September 11, 2025
### Feature Available
#### VMware Prebuilt Image Update for Network Connector
An updated Network Connector image is available for VMware that includes support for upcoming VPN redundancy features.
If you want to enable firewalld on a system running the Network Connector, you must perform additional steps to modify the firewall filter rule for VPN redundancy to work properly.
To learn more, see [Network Connector Deployment Prerequisites](/zpa/network-connector-deployment-prerequisites) and [Network Connector Software by Platform](/zpa/network-connector-software-platform).

## September 09, 2025
### Feature Available
#### Discovered Application Segments Update for Usage Insights
Discovered Host Count reports provide insight into the top 10 application segments by discovered host count, and are visible on the Application Segments Usage page.
[See image.](#discoveredHostCountReports)
In addition, a Discovered Application column was added to the table of a detailed report's CSV file to indicate if an application was discovered. Detailed reports can be downloaded from the Download CSV File window on the Application and User Group Relationships page.
[See image.](#discoveredApps)
To learn more, see [Viewing Application Segments Usage](/zpa/viewing-application-segments-usage) and [Viewing Application and User Group Relationships](/zpa/viewing-application-and-user-group-relationships).
[]![Viewing the Discovered Host Count Reports on the Application Segments Usage Page](/sites/default/files/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-application-segments-usage-doc-59370/zpa-app-segment-usage-insights-discovered-host-count-full-page-rn.png)
[]![Detailed Report for Discovered Applications](/sites/default/files/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/applications-users-insights/viewing-application-and-user-group-relationships/zpa-application-and-user-group-relationships-detailed-report-discovered-column.png)

### Feature Available
#### Repository Update to Upgrade the Host OS to RHEL 9.6
A repository update that enhances virtual images is available for App Connectors, ZPA Private Service Edges, and Private Cloud Controllers. This update allows the host operating system (OS) to upgrade from Red Hat Enterprise Linux (RHEL) 9.4 and 9.5 to RHEL 9.6.
To learn more, see [Updating the Host OS and Software Packages](/zpa/updating-app-connector-host-os-and-software-packages).

## September 08, 2025
### Feature Available
#### SAML & SCIM Support for Usage Insights
You can select SAML and SCIM attributes in the Settings drawer of the Application and User Group Relationships page.
[See image.](#samlScimAppUserGroupSettings)
To learn more, see [Viewing Application and User Group Relationships](/zpa/viewing-application-and-user-group-relationships).
[]![Selecting SAML & SCIM Attributes in the Application and User Group Relationships Settings Page](/sites/default/files/downloads/zpa/zpa-application-user-group-relationships-settings-saml-scim-release-notes.png)

## September 05, 2025
### Feature Available
#### AI-Powered Recommendations Updates
The Recommended Configuration drawer includes the following updates:
- The Users tab and Attributes tab for observed users includes a Total Users or Group Size column that lets you compare the number of observed users in the recommendation to the total number of users.
- The Users column was renamed to Observed Users to more easily identify observed versus total users.
[See image.](#observed-users)
To learn more, see [About AI-Powered Recommendations for Application Segments](/zpa/about-ai-powered-recommendations-application-segments).
[]![AI-Powered Recommended Configuration with Total Users ](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-ai-powered-recommendations-total-users.png)

## September 04, 2025
### Feature Available
#### Disk Space Exceeded Limit Update in Events Diagnostics
An update was released that increases the Disk Space Exceeded Limit event threshold from 1024 MB to 2048 MB in Events Diagnostics.
[See image.](#diskSpaceExceeded)
To learn more, see [Viewing and Managing Events Diagnostics](/zpa/viewing-and-managing-events-diagnostics#Event).
[]![Viewing Threshold Usage for Disk Space Exceeded Limit in the Events Diagnostics](/sites/default/files/downloads/zpa/notification-management/about-notifications/zpa-events-diagnostics-disk-space-exceeded.png)

## September 02, 2025
### Feature Available
#### AppProtection API Protection Update
The following updates were made to the AppProtection API Protection feature:
- API Protection is included when configuring an application segment, by default.
- Some API Protection controls were moved to OWASP Predefined controls and ThreatLabZ controls.
- New filters were added to the AppProtection Diagnostics page: API Request, API Style, Auth type, Path, and Request method.
- The Recent API Activity widget was added to the API Protection dashboard.
To learn more, see [Configuring Defined Application Segments](/zpa/configuring-defined-application-segments), [Configuring AppProtection Profiles](/zpa/configuring-appprotection-profiles), [Accessing AppProtection Diagnostics](/zpa/accessing-approtection-diagnostics), and [Viewing the API Protection Dashboard](/zpa/viewing-api-protection-dashboard).

### Feature Available
#### Enhanced Capabilities for API Protection
An update was released to support enhanced visibility and controls for API Protection.
To learn more, see [Configuring AppProtection Profiles](/zpa/configuring-appprotection-profiles).

## August 27, 2025
### Feature Available
#### Amazon Web Services Image Update for App Connector
A new AWS image is available for App Connector to support upcoming automated Manager software and OS security updates.
To learn more, see [App Connector Deployment Guide for Amazon Web Services](/zpa/connector-deployment-guide-amazon-web-services).

## August 15, 2025
### Feature Available
#### Network Tag-Based Resource Groups for Microsegmentation
When configuring a resource group for Microsegmentation and adding cloud tags, you can now select the key "Exists." This allows the results to show if the tag itself exists at all or not, instead of matching that key to a value. When selected, the value field for the key is disabled.
Selecting this key option is especially useful when adding Google Cloud Platform (GCP) tags. It lets admins create resource groups based specifically on Google network tags.
[See image.](#Is-Present)
To learn more, see [About Resource Groups](https://help.zscaler.com/zpa/about-resource-groups) and [Configuring Resource Groups](https://help.zscaler.com/zpa/configuring-resource-groups).
[]![A view of the new Is Present toggle filter.](/sites/default/files/downloads/zpa/microsegmentation/resource-management/configuring-resource-groups/Add-New-Resource-Group_Criteria_Dynamic-Membership_Exists-tag_release-notes.png)

### Feature Available
#### New Session Status Codes for Disconnections
If an App Connector or ZPA Private Service Edge was disconnected because of a planned restart, a redirect session status code is available on the User Activity Diagnostics page.
To learn more, see [Understanding ZPA Session Status Codes](/zpa/understanding-connector-software-updates).

## August 14, 2025
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 8.x and 9.x.
You can download the Manager software for [App Connectors](/zpa/app-connector-deployment-guide-linux) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux) from our repository. The Manager software version is 25.46.2.
To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades).

### Feature Available
#### Multimatch Validation for Application Segments
When Multimatch is enabled, a Multimatch Validation window appears for you to review any impacted application segments and conflicting features. Depending on the application segments selected, you might need to do one of the following:
- Edit an application segment and disable unsupported features before proceeding.
- Review conflicting features in a local Microtenant and select the checkboxes that appear to proceed.
- Contact the default administrator when Multimatch includes the default application segment.
- Cancel and disable Multimatch if an application segment belongs to another local tenant.
[See image.](#Multimatch)
To learn more, see [Using Application Segment Multimatch](/zpa/using-app-segment-multimatch).
[]![Application Segment Multimatch Validation page](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-app-segment-multimatch-validation.png)

## August 13, 2025
### Feature Available
#### Cloud Service API Updates to Enable Multimatch in Bulk
The cloud service API includes the following new endpoints to extend programmatic access for application segment Multimatch:
- `POST /customers/{customerId}/application/multimatchUnsupportedReferences`
- `PUT /customers/144118148382064640/application/bulkUpdateMultiMatch`
To learn more, see [Configuring Application Segment Multimatch Using API](/zpa/configuring-application-segment-multimatch-using-api), [Application Segment Management](/zpa/application-segment-management), and [Using Application Segment Multimatch](/zpa/using-app-segment-multimatch).

## August 11, 2025
### Feature Available
#### Resolved Issues
A fix was released to update how data is processed for the Peak Zscaler Client Connector Redirections to Private Service Edges widget and the Zscaler Client Connector Redirections to Private Service Edges activity monitor widget in the Private Cloud Controllers dashboard.
To learn more, see [Viewing the Private Cloud Controllers Dashboard](/zpa/viewing-private-cloud-controllers-dashboard#MonitorWidgets).

### Feature Available
#### Update to AI-Powered Recommendations by Confidence % Widget
The AI-Powered Recommendations by Confidence % widget was updated to AI-Powered Recommendations by Attack Surface Reduction % in the Applications dashboard.
[See image.](#AiPoweredRecAsr)
To learn more, see [Viewing the Applications Dashboard](/zpa/viewing-applications-dashboard).
[]![AI-Powered Recommendations by Attack Surface Reduction % in the Applications dashboard](/sites/default/files/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-applications-dashboard-doc-59379/zpa-ai-powered-recommendations-by-asr-percentage.png)

## August 08, 2025
### Feature Available
#### Kubernetes and OpenShift Enhancements for App Connector
This release provides the following updates for usability, security, and cross-platform compatibility improvements for the App Connector Helm charts:
-
Improved container security includes fine-grained capability control options (minimal, full, custom). If `CAP_NET_RAW` is omitted in custom mode, a failsafe mechanism automatically injects it to ensure functionality. OpenShift deployments default to `capabilityMode: full` to maintain compatibility with platform restrictions.
For App Connector version 25.45.1 or earlier, use only `full` mode to avoid unexpected behavior or compatibility issues. The `minimal` and `custom` capability modes are supported in App Connector versions later than 25.45.1.
- Namespace handling improvements include:
- The chart deployed in a Kubernetes cluster no longer auto-creates the specified namespace by default (e.g., `zscaler-zpa`). For OpenShift, the previous behavior is retained.
- Custom namespace support allows you to add `--namespace` and `--create-namespace` flags during installation. Namespaces are created by setting the `createNamespace: true/false` in `values.yaml`. Follow Helm's best practices for using these flags for consistent deployments.
- For K8s, if `createNamespace: true`, the previous behavior is retained for legacy automation and scripts for backward compatibility in Kubernetes. For OpenShift, the previous behavior is retained because the `createNamespace` flag isn't relevant, and the namespace is always created.
- Deployment-level labels are supported in `values.yaml`, enhancing chart customization for monitoring, alert routing, and resource filtering. Defaults are retained via the existing logic in` _helpers.tpl` for backward compatibility.
- A single, platform-aware chart structure supports both Kubernetes and OpenShift. It uses `.Capabilities.APIVersions.Has` to auto-detect and apply OpenShift-specific templates (e.g., SCC). This helps reduce duplication and simplify ongoing chart maintenance.
- Helm charts have been consolidated into a single, unified chart that supports both Kubernetes and OpenShift platforms with the following structure:
-
The Helm Charts directory is unchanged:
`zscaler-et-dist/helm-charts/`
-
A new unified chart name has been created:
`zpa-app-connector`
-
The following chart directories have been deprecated:
`zscaler-et-dist/helm-charts/k8s/
zscaler-et-dist/helm-charts/openshift/`
Zscaler recommends that you review and set the appropriate values in `values.yaml`:
- ``capabilityMode` (minimal, full, custom)`
- ``createNamespace``
- ``namespace``
- ``labels``
To learn more, see [App Connector Deployment Guide for Kubernetes](/zpa/app-connector-deployment-guide-kubernetes) and [App Connector Deployment Guide for OpenShift](/zpa/app-connector-deployment-guide-openshift).

### Feature Available
#### Multifile Support for Isolation in ZPA
Users can now upload multiple files simultaneously while in an isolated session. There is no minimum or maximum limit while uploading.
[See image.](#Multi-File-Upload)
To learn more, see [Transferring and Viewing Files in Isolation](https://help.zscaler.com/isolation/transferring-and-viewing-files-isolation).
[]![A view of the upload log while in Isolation.](/sites/default/files/downloads/isolation/end-user-isolation-experience/transferring-and-viewing-files-isolation/Multi-File-Upload_RNs.png)

## August 07, 2025
### Feature Available
#### AWS and Azure Image Support for Private Cloud Controllers
A new Red Hat Enterprise Linux 9 Private Cloud Controller image is available in the AWS Marketplace and Microsoft Azure Marketplace.
To learn more, see [Private Cloud Controller Software by Platform](/zpa/private-cloud-controller-software-platform).

## July 30, 2025
### Feature Available
#### Docker Image Updates
New Red Hat Enterprise Linux 9 App Connector and ZPA Private Service Edge images are available for Docker. This release includes:
- Auto-updates for security patches during every container start or restart using `micro-dnf`.
- New Docker deployments that automatically include the latest available Manager software version and provide compatibility for seamless future Manager software and OS updates.
To learn more, see [App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform) and [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform).

## July 21, 2025
### Feature Available
#### Provisioning Key Hardening in the ZPA Admin Portal
When creating a provisioning key for ZPA features such as App Connectors, Private Service Edges, Private Cloud Controllers, Network Connectors, or Machine Tunnels, you can choose to hide the provisioning key so it doesn't appear in the ZPA Admin Portal and can't be copied or downloaded for security purposes.
The View or Export Provisioning Key After Creation option must be enabled for Branch Connector and App Connector deployment.
[See image.](#pkexport)
To learn more, see [About App Connector Provisioning Keys](/zpa/about-connector-provisioning-keys), [About ZPA Private Service Edge Provisioning Keys](/zpa/about-zpa-service-edge-provisioning-keys), and [About Private Cloud Controller Provisioning Keys](/zpa/about-private-cloud-controller-provisioning-keys).
[]![Image of Create Provisioning Key page](/sites/default/files/downloads/zpa/app-connector-management/app-connectors/configuring-app-connectors/zpa-addconnector-createprovisioningkey.png)

### Feature Available
#### Updates to Cloud Service API
The cloud service API includes the following new categories of endpoints to extend programmatic access to various ZPA features and functionalities:
- [API Keys](#ApiKey)
- [Authentication](#auth)
- [Client-to-Client Connectivity](#clientToClient)
- [Private Cloud Controllers](#privateCloudController)
- [Private Cloud Controller Groups](#privateCloudControllerGroup)
- [User Portals](#userPortals)
- [User Portal Links](#userPortalLinks)
To learn more, see the [ZPA API Developer & Reference Guide](/zpa/zpa-api/api-developer-reference-guide).
- []`GET /mgmtconfig/v1/admin/customers/{customerId}/apiKeys/{id}`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/apiKeys`
- `PUT /mgmtconfig/v1/admin/customers/{customerId}/apiKeys/{id}`
- `DELETE /mgmtconfig/v1/admin/customers/{customerId}/apiKeys/{id}`
- []`GET /mgmtconfig/v1/admin/customers/{customerId}/v2/ssoLoginOptions`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/v2/ssoLoginOptions`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/configOverrides/{id}`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/configOverrides`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/configOverrides`
- `PUT /mgmtconfig/v1/admin/customers/{customerId}/configOverrides/{id}`
- []`GET /mgmtconfig/v1/admin/customers/{customerId}/privateCloudController`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/privateCloudController/{privateCloudControllerId}`
- `PUT /mgmtconfig/v1/admin/customers/{customerId}/privateCloudController/{privateCloudControllerId}/restart`
- `PUT /mgmtconfig/v1/admin/customers/{customerId}/privateCloudController/{privateCloudControllerId}`
- `DELETE /mgmtconfig/v1/admin/customers/{customerId}/privateCloudController/{privateCloudControllerId}`
- []`GET /mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup/{privateCloudControllerGroupId}`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup/summary`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup`
- `PUT /mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup/{privateCloudControllerGroupId}`
- `DELETE /mgmtconfig/v1/admin/customers/{customerId}/privateCloudControllerGroup/{privateCloudControllerGroupId}`
- []`GET /mgmtconfig/v1/admin/customers/{customerId}/userPortal/{id}`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/userPortal`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/userPortal`
- `PUT /mgmtconfig/v1/admin/customers/{customerId}/userPortal/{id}`
- `DELETE /mgmtconfig/v1/admin/customers/{customerId}/userPortal/{id}`
- []`GET /mgmtconfig/v1/admin/customers/{customerId}/userPortalLink`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/userPortalLink/userPortal/{portalId}`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/userPortalLink/{id}`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/userPortalLink`
- `POST /mgmtconfig/v2/admin/customers/{customerId}/userPortalLink/bulk`
- `PUT /mgmtconfig/v1/admin/customers/{customerId}/userPortalLink/{id}`
- `DELETE /mgmtconfig/v1/admin/customers/{customerId}/userPortalLink/{id}`
- []`GET /mgmtconfig/v1/admin/customers/{customerId}/v2/ipRanges`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/v2/ipRanges/{ipRangeId}`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/v2/ipRanges/search`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/v2/ipRanges`
- `PUT /mgmtconfig/v1/admin/customers/{customerId}/v2/ipRanges/{ipRangeId}`
- `DELETE /mgmtconfig/v1/admin/customers/{customerId}/v2/ipRanges/{ipRangeId}`

## July 17, 2025
### Feature Available
#### Event Logs for Agents and Resources
Microsegmentation now shows event logs for agent and resource diagnostics data. You can view a timestamp and priority level based on each log's information.
[See image.](#Event-Logs)
To learn more, see [About Agents](https://help.zscaler.com/zpa/about-agents) and [About Resources](https://help.zscaler.com/zpa/about-resources).
[]![A view of the Event Logs page with its filters and widgets.](/sites/default/files/downloads/zpa/microsegmentation/dashboard/RN_Event-Logs.png)

### Feature Available
#### Managing Ignored ML Recommendations in Microsegmentation
You can now edit the list of ignored Machine Learning (ML) Recommendations for resource groups in Microsegmentation. This allows you to review the list of previously ignored recommendations and have the option to accept them.
To learn more, see [About ML Recommendations for Resource Groups](https://help.zscaler.com/zpa/about-ml-recommendations-resource-groups) and [About Resource Groups](https://help.zscaler.com/zpa/about-resource-groups).

### Feature Available
#### ML Recommendations Dashboard Widget for Microsegmentation
The Overview Dashboard has a new widget to show Machine Learning (ML) Resource Group Recommendations for Microsegmentation. It provides a quick glimpse of enablement status and how many recommendations have been generated.
[See image.](#ML-widget)
To learn more, see [Viewing the Overview Dashboard](https://help.zscaler.com/zpa/viewing-overview-dashboard).
[]![The new ML recommendations widget.](/sites/default/files/downloads/zpa/microsegmentation/analytics/about-event-logs-microsegmentation/Agent-overview_ML-Recs-widget_RN.png)

## July 14, 2025
### Feature Available
#### Usage Insights
Usage Insights provides you with actionable insights into an organization's usage patterns between users and applications.
[See image.](#UsageInsights)
To learn more, see [About Usage Insights](/zpa/about-usage-insights), [Viewing Policy Usage](/zpa/viewing-policy-usage), [Viewing Policy Usage Details](/zpa/viewing-policy-usage-details), and [Viewing Application and User Group Relationships](/zpa/viewing-application-and-user-group-relationships).
[]![Access usage insights for applications, user groups, or policy usage.](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/ZPA-UsageInsightsPage-Overview-release-note.png)

### Feature in Limited Availability
#### Application Segments Usage
You can view or download Application Segments Usage reports from the ZPA Admin Portal to review insights into which application segments are actively used, and to provide visibility into which user groups are accessing the applications.
Application Segments Usage reports are only available to customers with the Segmentation add-on for eligible licenses.
[See image.](#applicationSegmentUsage)
To learn more, see [Viewing Application Segments Usage](/zpa/viewing-application-segments-usage) and [Viewing Application Segments Usage Details](/zpa/viewing-application-segments-usage-details).
[]![Viewing the Application Segment Usage Page ](/sites/default/files/downloads/zpa/zpa-application-segment-insights.png)

## July 10, 2025
### Feature Available
#### AI-Powered Recommendations Updates
The following updates for AI-powered recommendations are available:
-
When adding an application segment from an AI-powered recommendation, you can create an access policy rule at the Policies step. The rule is added to the middle of the rule order. Click Edit Policy if you need to move the rule higher or lower in the order.
[See image.](#policy)
To learn more, see [Configuring AI-Powered Recommendations](/zpa/configuring-ai-powered-recommendations).
-
The AI-Powered Recommendations page includes the following updates:
- Clicking an AI-powered recommendation in the Name column opens the Recommended Configuration details drawer.
- A new column was added that displays the total number of Recommended Users.
[See image.](#recommendations-table)
To learn more, see [About AI-Powered Recommendations for Application Segments](/zpa/about-ai-powered-recommendations-application-segments).
-
The Recommended Configuration drawer includes the following updates:
- Information for recommended users and observed users appears when selecting a filter.
- A Groups or Attributes tab was added for both recommended and observed users that shows the SCIM groups, and attributes. You can also view the number of observed users for each SCIM group.
- An option to copy the list of recommended users is available to set up Group or Attribute configuration in your identity provider (IdP).
- An option to download a list of missing users is available from the warning message for those users missing the Group/Attribute configuration on your IdP side.
- User email addresses can be searched from the Groups or Attributes tab.
[See image.](#recommended-config-drawer)
To learn more, see [About AI-Powered Recommendations for Application Segments](/zpa/about-ai-powered-recommendations-application-segments).
[]![Policy Page when Adding an Application Segment](/sites/default/files/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/creating-certificate-signing-requests-enrollment-ca-certificates/zpa-app-segment-edit-policy.png)
[]![AI-Powered Recommendations Table in the ZPA Admin Portal](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-ai-powered-recommendation-table_1.png)
[]![AI-Powered Recommended Configuration Drawer in the ZPA Admin Portal](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-ai-powered-recommendations-groups-tab-with-download-missing-users.png)

### Feature Available
#### Increased Limit for Privileged Consoles
You can have a maximum total of 9,000 privileged consoles per Privileged Remote Access (PRA) Portal.
To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).

### Feature Available
#### VMware and Nutanix Images Available for App Connector
New VMware and Nutanix images are available for App Connector to support upcoming automated Manager software and OS security updates.
To learn more, see [App Connector Deployment Guide for VMware Platforms](/zpa/connector-deployment-guide-vmware-platforms) and [App Connector Deployment Guide for Nutanix AHV](/zpa/app-connector-deployment-guide-nutanix-ahv).

## July 07, 2025
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 8.x and 9.x.
You can download the Manager software for [App Connectors](/zpa/app-connector-deployment-guide-linux) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux) from our repository. The Manager software version is 25.45.1.
To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades).

## June 30, 2025
### Feature Available
#### Custom Controls Negative Match
When you define custom control parameters for AppProtection, you can select negative value operator options (Does not match, Does not contain, Does not start with, Does not end with, and Does not exist) and the positive value operator option (Exists). When you select the request method, you can choose a negative option (Not Get, Not Put, etc.).
To learn more, see [Configuring Custom Controls](/zpa/configuring-custom-controls).

## June 16, 2025
### Feature Available
#### Removal of Executive Insights App
An update was released to remove the Executive Insights App from the ZPA Admin Portal. The Executive Insights App is supported in the ZIA Admin Portal and requires a subscription with Zscaler Internet Access (ZIA).
To learn more, see [Accessing and Using the Executive Insights App](/zia/accessing-and-using-executive-insights-app).

## June 12, 2025
### Feature Available
#### Agent Admin Status Inheritance for Microsegmentation
Agent Admin Status is enhanced to reflect if it is based on inheritance from the agent group that it is a part of, or set individually at the agent level, overriding the selection.
[See image.](#Admin-Status)
[]![A view of the dropdown menu for Admin Status on the Agents page.](/sites/default/files/downloads/zpa/microsegmentation/about-agents-page/About-the-Agents-page_Admin-Status-menu.png)
To learn more, see [About Agents](https://help.zscaler.com/zpa/about-agents).

### Feature Available
#### Google Compute Engine Support for Microsegmentation
Google Compute Engine support has been added when configuring agent groups. Agents can now discover metadata like cloud region, project name, and VPC name for workloads when running in Google Cloud.
[See image.](#GCP-option)
[]![A view of GCP chosen for the cloud option in the new agent group window.](/sites/default/files/downloads/zpa/microsegmentation/configuring-agent-groups/Add-Agent-Group_Name-AdminStatus-PolicyStatus-Description-Cloud_GCP-SELECTED.png)
To learn more, see [Configuring Agent Groups](https://help.zscaler.com/zpa/configuring-agent-groups).

### Feature Available
#### Microsegmentation Overview Dashboard
Microsegmentation now has an Overview Dashboard that provides the current status of your environment. This dashboard introduces two new widgets that show percentages of Protected-to-Unprotected Resources and Protected-to-Unprotected Resource Groups. Additionally, it contains the existing Agent Connection Status and Agent Versions widgets.
[See image.](#Overview-Dashboard)
[]![A view of the Overview Dashboard.](/sites/default/files/downloads/zpa/microsegmentation/dashboard/viewing-overview-dashboard/Overview-Dashboard2.png)
To learn more, see [Viewing the Overview Dashboard](https://help.zscaler.com/zpa/viewing-overview-dashboard).

## June 03, 2025
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector, ZPA Private Service Edge, and Private Cloud Controller RPM packages for Red Hat Enterprise Linux 8.x and 9.x.
You can download the Manager software for App Connectors, ZPA Private Service Edges, and Private Cloud Controllers from our repository. The Manager software version is 25.44.6.
To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades).

### Feature Available
#### Support for Existing IdPs in Business Continuity
Existing IdP configurations can be used to authenticate users during Business Continuity.
[See image.](#existing-idp)
To learn more, see [Configuring Business Continuity Settings](/zpa/configuring-business-continuity-settings).
[]![Existing IdP for Authentication in Business Continuity](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/zpa-business-continuity-settings-existing-idp.png)

### Feature Available
#### Updated Status Code for Web Browser Client Type Timeout
When the ZPA service blocks a Web Browser request because the timeout policy requires the user to authenticate, an SE: Timeout policy blocked access status code appears.
To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).

### Feature Available
#### ZPA Hosting Detection for App Connectors
An update was released that allows ZPA to automatically detect data center hosting information, or you can enter it manually.
[See image.](#seeimage)
To learn more, see [Configuring App Connectors](/zpa/configuring-connectors).
[]![Add App Connector window in Add App Connector Group tab](/sites/default/files/downloads/zpa/release-notes/zpa-app-connector-release-notes/april-2025-release-notes/Add-App-Connector-HostDetect.png)

### Feature in Limited Availability
#### API Discovery for API Protection
An update was released to support API Discovery for API Protection.
To learn more, see [API Discovery for AppProtection](/zpa/release-upgrade-summary-2025?applicable_category=private.zscaler.com&deployment_date=2025-10-06&id=1531059).

## June 02, 2025
### Feature in Limited Availability
#### Zscaler-Managed Business Continuity Cloud
The Zscaler-managed Business Continuity cloud is a fully managed Private Cloud solution that is built on the isolated and dedicated Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) infrastructures. This ensures consistent cyber and data protection during critical failure events. For simplified operations and faster Business Continuity enablement, ZPA leverages the Business Continuity functionality that is deployed in a fully managed and hosted single-tenant environment.
Contact your Zscaler Account team for more information.
To learn more, see [Understanding Business Continuity](/zpa/understanding-business-continuity), [Configuring Business Continuity Settings](/zpa/configuring-business-continuity-settings), and [Understanding Zscaler-Managed Business Continuity Cloud](/zia/understanding-zscaler-managed-business-continuity-cloud).

## May 30, 2025
### Feature Available
#### Viewing Where Your Apps Are Served
View hosting provider and analytical details of the App Connectors that have been serving your applications for the last quarter on the Where Are My Apps Being Served From? page.
This insight allows you to understand where your applications are hosted because App Connectors act as a good proxy for your private applications in certain cases.
[See image.](#map)
To learn more, see [Viewing Where Your Apps Are Served](/zpa/viewing-where-your-apps-are-served).
[]
![View where your private applications are hosted](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/ZPA-Where-page-2.png)

## May 28, 2025
### Feature Available
#### Client Platform and Hostname in the LSS and Cloud Service API
Client platform and hostname details are available in the User Activity transaction logs when configuring a log receiver. Additionally, these fields are returned by the format field when managing Log Streaming Service (LSS) configurations using the cloud service API.
[See image.](#platformUserActivityLogReceiver)
[]![Adding Platform and Hostname Fields When Configuring a Log Receiver](/sites/default/files/downloads/zpa/zpa-platform-hostname-user-activity-log-receiver.png)
To learn more, see [Understanding User Activity Log Fields](/zpa/understanding-user-activity-log-fields) and [Managing Log Streaming Service Configurations Using API](/zpa/managing-log-streaming-service-configurations-using-api).

## May 23, 2025
### Feature Available
#### STIG VM Private Service Edge Image for Nutanix
A Red Hat Enterprise Linux 9 Private Service Edge image that supports Security Technical Implementation Guide (STIG) is available for Nutanix.
To learn more, see [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform) and [ZPA Private Service Edge Deployment Guide for Nutanix AHV](/zpa/zpa-private-service-edge-deployment-guide-nutanix-ahv).

## May 21, 2025
### Feature Available
#### Resolved Issues
A fix was released to address an issue where extra braces in the JSON log format for Log Streaming Service (LSS) prevented logs from going to the SIEM.
To learn more, see [About the Log Streaming Service](/zpa/about-log-streaming-service).

## May 20, 2025
### Feature Available
#### Credentials Diagnostics for Privileged Remote Access (PRA)
You can view analytics for privileged credentials on the Credentials Diagnostics page, including the total amount of privileged credentials and how many are currently in use. The privileged credentials based on protocol type are also displayed.
To learn more, see [Accessing Privileged Credentials](/zpa/accessing-privileged-credentials).

### Feature in Limited Availability
#### Updates to Approval Requests for Privileged Remote Access (PRA)
The following updates have been made to approval requests for Privileged Remote Access (PRA):
- You can approve and reject approval requests in the ZPA Admin Portal, similar to how you review approval requests in the PRA Portal.
- The Requests Diagnostics page name has been updated to the Approval Requests Diagnostics page.
- When you create an Acceptable Use Policy (AUP), Markdown format is supported.
[See image.](#Approvals)
To learn more, see [Accessing Privileged Approval Requests](/zpa/accessing-privileged-requests).
[]![The Approval Requests table on the Approval Requests page](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/Approvals%20Request%20page.png)

## May 19, 2025
### Feature Available
#### Disable Pop-Up Message to User
An update was released that renamed the Message to User field to Pop-Up Message to User when configuring or editing an access policy. As part of this update, the ability to disable the Pop-Up Message to User field is supported. This field only appears when the Rule Action is set to Block Access.
[See image.](#AddAccessPolicyBlockAccess)
This feature is only supported for Zscaler Client Connector version 4.7 for Windows.
To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies).
[]![Enabling the Message to User field in the Add Access Policy window](/sites/default/files/downloads/zpa/authentication/settings/configuring-authentication-settings/zpa-add-access-policy-window-block-access-pop-up.png)

## May 15, 2025
### Feature Available
#### Cloud Service API Support for Onboarding Customers
The cloud service API includes the following new endpoints for administrator management, administrator role management, and client settings management:
- `GET /mgmtconfig/v1/admin/customers/{customerId}/administrators/{adminId}`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/administrators`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/administrators`
- `PUT /mgmtconfig/v1/admin/customers/{customerId}/administrators/{adminId}`
- `DELETE /mgmtconfig/v1/admin/customers/{customerId}/administrators/{adminId}`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/permissionGroups`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/roles`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/roles/{roleId}`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/roles`
- `PUT /mgmtconfig/v1/admin/customers/{customerId}/roles/{roleId}`
- `DELETE /mgmtconfig/v1/admin/customers/{customerId}/roles/{roleId}`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/clientSetting`
- `GET /mgmtconfig/v1/admin/customers/{customerId}/clientSetting/all`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/clientSetting`
- `DELETE /mgmtconfig/v1/admin/customers/{customerId}/clientSetting`
Additionally, the following new endpoints are included to provision applications with all related objects, to generate self-signed enrollment (CA) certificates, and to generate certificate signing requests for enrollment certificates:
- `POST /mgmtconfig/v1/admin/customers/{customerId}/application/provision`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/enrollmentCert/selfsigned/generate`
- `POST /mgmtconfig/v1/admin/customers/{customerId}/enrollmentCert/csr/generate`
To learn more about each endpoint, see [Managing Administrators Using API](/zpa/managing-administrators-using-api), [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api), and [Managing Client Settings Using API](/zpa/managing-client-settings-using-api).

## May 09, 2025
### Feature Available
#### Last Component Disconnected Event Priority Update
The priority for the Last Component Disconnected event in the events diagnostics and notifications service was updated from Low to High. This only applies to newly created events for App Connectors and ZPA Private Service Edges after May 9, 2025.
To learn more, see [Configuring Notifications](/zpa/configuring-notifications) and [Viewing and Managing Events Diagnostics](/zpa/viewing-and-managing-events-diagnostics).

### Feature Available
#### OWASP Predefined Controls Update
The OWASP predefined controls were updated to support version OWASP_CRS/4.8.0. By default, the version is set to OWASP_CRS/4.8.0 on the OWASP Predefined Controls page and the AppProtection Profiles page. The OWASP_CRS/4.8.0 version is supported on [App Connector version 25.43.2](/zpa/app-connector-release-summary-2025?applicable_category=private.zscaler.com&applicable_version=25.43.2&deployment_date=2025-04-23&id=1520451) and later.
To learn more, see [About AppProtection Controls.](/zpa/about-appprotection-controls)

## May 08, 2025
### Feature Available
#### Audit Log Updates for Microsegmentation Recommended Resource Groups
A new resource type for Microsegmentation Managed Recommended Resource Group was added to the Audit Logs.
[See image.](#MicrosegmentationResourceGroup)
To learn more, see [About ML Recommendations for Resource Groups](/zpa/about-ml-recommendations-resource-groups), [About Audit Logs](/zpa/about-audit-logs#resourceType), [About Audit Log Fields](/zpa/about-audit-log-fields#objectType), and [What Is Microsegmentation?](/zpa/what-is-microsegmentation)
[]![Viewing the Microsegmentation Managed Resource Group Resource Type in the Audit Logs](/sites/default/files/downloads/zpa/zpa-audit-logs-microsegmentation-managed-resource-groups.png)

### Feature Available
#### Number of API Keys with This Role
A new column was added to the Roles page to track the number of API keys per assigned role.
[See image.](#ApiKeysPerRole)
To learn more, see [About Roles](/zpa/about-roles).
[]![Viewing the Number of API Keys with the Role ](/sites/default/files/downloads/zpa/documentation-knowledgebase/admin-settings/admins-and-roles/about-roles/zpa-roles-page-number-of-api-keys-release-note.png)

## May 07, 2025
### Feature Available
#### VPN (for Legacy Apps) Network Connector RPM Package
Zscaler has released a Network Connector RPM package that contains only the installation packages and privileges required by the Network Connector. VPN (for Legacy Apps) customers who previously installed the App Connector RPM package that included the Network Connector dependencies should uninstall it and then install the new Network Connector RPM package.
App Connector customers can run the `yum upgrade` command in this release to remove the Network Connector dependencies from their App Connectors.
To learn more, see the [Network Connector Deployment Guide for Linux](/zpa/network-connector-deployment-guide-linux).

## April 30, 2025
### Feature Available
#### Chrome Enterprise Browser Diagnostics
You can view Chrome Enterprise browser analytics and policy log data on the Chrome Enterprise Browser Diagnostics page.
[See image.](#chromeEnterpriseDiagnostics)
To learn more, see [Accessing Chrome Enterprise Browser Diagnostics](/zpa/accessing-chrome-enterprise-browser-diagnostics).
[]![Viewing the Chrome Enterprise Browser Diagnostics](/sites/default/files/downloads/zpa/zpa-chrome-enterprise-browser-diagnostics-rn.png)

### Feature Available
#### Evaluate Access with Chrome Posture Profiles
ZPA integrates with Google's Chrome Enterprise browser to utilize its device posture signals, enabling more granular security controls (Browser Version, Operating System, OS Firewall status, etc.) and enhanced visibility for clientless access to private applications via ZPA Browser Access and Browser Isolation.
[See image.](#posture)
To learn more, see [About Chrome Posture Profiles](/zpa/about-chrome-posture-profiles), [Configuring Chrome Posture Profiles](/zpa/configuring-chrome-posture-profiles), and [Managing Chrome Posture Profiles](/zpa/managing-chrome-posture-profiles).
[]
![Add a Chrome posture profile](/sites/default/files/downloads/zpa/browser-access/configuring-chrome-posture-profiles/ZPA-Chrome-Device-Posture-3.png)

### Feature Available
#### Flow Dashboard Update in Microsegmentation
The Flow dashboard is enhanced to include policy decisions in the widgets, with the addition of new widgets for blocked flow records. The categories are divided into the Top Permitted Talkers, Top Blocked Talkers, Top Permitted Listeners, Top Blocked Listeners, Top Permitted Agent-to-Agent Flows, and Top Permitted Flows Between Agent And Non-Agent.
[See image.](#Flow-dashboard)
To learn more, see [Viewing the Flow Dashboard](https://help.zscaler.com/zpa/viewing-flow-dashboard).
[]![A view of the new Flow dashboard.](/sites/default/files/downloads/zpa/microsegmentation/Flow-dashboard4_0.png)

### Feature Available
#### Installation Directory Update for Microsegmentation Linux Agent
The installation directory for the Linux agent in Microsegmentation has changed from `/opt/zscaler` to `/opt/zscaler/zms`. This change also affects the location of the provisioning key, which is now copied to `/opt/zscaler/zms/var`. For existing agents on version 1.1 or earlier, the upgrade of an agent from 1.1 to 1.2 automatically moves the folder to the new location.
To learn more, see [Configuring Agents](https://help.zscaler.com/zpa/configuring-agents).

### Feature Available
#### ML Recommendations for Resource Groups in Microsegmentation
Machine-learning (ML) recommendations are available for configuring resource groups in Microsegmentation. The recommendations are based off of analyzed resources that have multiple similarities, such as cloud user-defined tags, cloud environment metadata, and host data. Each ML recommendation also includes a Confidence Score, which determines the likelihood from 1 to 100 of how optimal it is for configuration. This can save admins time and effort in reviewing which individual resources should be grouped together.
[See image.](#ML-Recommended-resource=groups-page)
To learn more, see [About Resource Groups](https://help.zscaler.com/zpa/about-resource-groups).
[]![A view of the ML Recommended resource groups page.](/sites/default/files/downloads/zpa/microsegmentation/resource-management/resources/about-ml-recommendations-resource-groups/ML-Recommendation-Resource-Groups-page_Release-Notes.png)

### Feature Available
#### VMware Image Available for Network Connectors
A new Network Connector image is available for VMware.
To learn more, see [Network Connector Software by Platform](/zpa/network-connector-software-platform).

### Feature in Limited Availability
#### VMware Image Available for Private Cloud Controller
A new Red Hat Enterprise Linux 9 Private Cloud Controller image is available for VMware.
To learn more, see [Private Cloud Controller Deployment Guide for VMware Platforms](/zpa/private-cloud-controller-deployment-guide-vmware-platforms) and [Private Cloud Controller Software by Platform](/zpa/private-cloud-controller-software-platform).

## April 28, 2025
### Feature Available
#### AppProtection Update
AppProtection updates to provide improved payload support for API formats (JSON and XML payloads) are available.

### Feature in Limited Availability
#### Application Load Balancing and High Availability
Load balancing allows applications to be weighted between individual server groups or designated in dedicated passive groups for high availability.
[See image.](#WLB-window)
To learn more, see [Configuring Application Load Balancing and High Availability](/zpa/configuring-load-balance-server-groups).
[]![A view of the load balance server group window.](/sites/default/files/downloads/zpa/documentation-knowledgebase/servers/server-groups/configuring-application-load-balancing-high-availability/load-balance-window_2.png)

### Feature in Limited Availability
#### ZPA API Application Load Balancing Configuration
Applications can be updated to assign weights between individual server groups or designated in dedicated passive groups via the ZPA cloud service API.
To learn more, see the [ZPA API Developer & Reference Guide](/zpa/application-segment-management) and [Managing Application Load Balancing and High Availability Using API](/zpa/managing-application-load-balancing-and-high-availability-using-api).

## April 23, 2025
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector, ZPA Private Service Edge, and Private Cloud Controller RPM packages for Red Hat Enterprise Linux 8.x and 9.x.
You can download the Manager software for [App Connectors](/zpa/app-connector-deployment-guide-linux) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux) from our repository. The Manager software version is 25.43.2. To learn more, see [Understanding the Manager Software](/zpa/understanding-manager-software).

## April 21, 2025
### Feature Available
#### Enhancing Security for Third-Party Clientless Access with ZPA and Chrome Enterprise Browser Integration
ZPA now integrates with the Chrome Enterprise browser to enhance security access to private applications using Browser Access. By leveraging Chrome's device posture signals, ZPA enforces granular security controls to manage clientless (third-party or contractor access) to private applications.
This integration verifies access to private applications and provides visibility for users that connect via the managed Chrome Enterprise browser based on the end user's access posture.
To learn more, see [Configuring Chrome Enterprise Browser Connector Settings](/zpa/configuring-chrome-enterprise-browser-connector-settings), [About Access Policy](/zpa/about-access-policy), and [Configuring Access Policies](/zpa/configuring-access-policies).

## April 01, 2025
### Feature Available
#### Filter Resources by Status for Microsegmentation
Microsegmentation resources can be filtered by Active or Inactive status.
[See image.](#Resource-Status)
To learn more, see [About Resources](/zpa/about-resources).
[]![Resources_Filters_Status.png](/sites/default/files/downloads/zpa/microsegmentation/about-resources-page/Resources_Filters_Status.png)

### Feature Available
#### Flow Log Filters for Direction and Resource Group Name in Microsegmentation
Microsegmentation flow logs can be filtered by Inbound or Outbound traffic direction and by Resource Group Name.
[See image.](#Direction-and-Resource-Group-Name)
To learn more, see [About Flow Logs](/zpa/about-flow-logs).
[]![Orange squares showcase the new filter additions for Direction and Resource Group Name.](/sites/default/files/downloads/zpa/microsegmentation/about-flow-logs-page/Direction_and_Resource-Group-Name_filters.png)

### Feature Available
#### Ubuntu Linux Support for Microsegmentation
Microsegmentation supports Ubuntu Linux devices for the following versions:
- 16.04.7
- 18.04 LTS
- 20.04 LTS
- 22.04 LTS
- 24.04 LTS

### Feature Available
#### Update to Agent Groups Filter for Upgrade Status for Microsegmentation
Microsegmentation agent groups have a new Upgrade Status filter option called Completed With Failures. This option allows you to filter which agent groups completed the latest version upgrade, but had failures occur. You can click the Upgrade Status for the agent group to expand the details panel and view the failure information.
[See image.](#Completed-With-Failures)
To learn more, see [About Agent Groups](/zpa/about-agent-groups).
[]![Orange squares showcase the new agent group filter option for Upgrade Status.](/sites/default/files/downloads/zpa/microsegmentation/about-the-agent-groups-page/Agent-Groups_Filters_Upgrade-Status_Completed-With-Failures.png)

## March 28, 2025
### Feature Available
#### Alert for Disconnected App Connectors
If any App Connectors have been disconnected for one year or more, an alert appears when you log in to the ZPA Admin Portal. Click the number of disconnected App Connectors to open the App Connectors page, which is filtered by the disconnected App Connectors so you can review or delete them.
[See image.](#alert)
To learn more, see [About App Connectors](/zpa/about-connectors).
[]![Image of Disconnected App Connector Alert](/sites/default/files/downloads/zpa/app-connector-management/app-connectors/about-app-connectors/zpa-disconnected-app-connector-alert.png)

## March 24, 2025
### Feature Available
#### API Keys Page Update
An update was released to remove the ZPA API Portal link from the API Keys page.
To learn more, see [About API Key Management](/zpa/about-api-key-management).

### Feature Available
#### VPN (for Legacy Apps)
ZPA can natively support a secondary Layer 3 network-based VPN tunnel for applications and services (e.g., VoIP or server-to-client) that require Layer 3 IP-based connectivity consistent with its Zero Trust security architecture and inside-out connection. From a single client for users and a single console for IT administrators, you can migrate to Zero Trust Network Access (ZTNA) with ZPA and completely eliminate legacy VPNs. You can accelerate application modernization while retaining access for users during the transition.
To learn more, see [Step-by-Step Configuration Guide for VPN (for Legacy Apps)](/zpa/step-step-configuration-guide-vpn-legacy-apps).

## March 21, 2025
### Feature Available
#### STIG VM Image Updates for Microsoft Azure
Red Hat Enterprise Linux 9 App Connector and Private Service Edge images that support Security Technical Implementation Guide (STIG) without requirements to disable password expiration are available for Microsoft Azure. The Azure STIG-hardened images released on December 12, 2024, required the password to be disabled. To verify if your image is affected, see [Disabling Password Expiration for STIG-Hardened App Connector Images](/zpa/disabling-password-expiration-stig-hardened-app-connector-images#verify) or [Disabling Password Expiration for STIG-Hardened Private Service Edge Images](/zpa/disabling-password-expiration-stig-hardened-zpa-private-service-edge-images#verify).
The following guidelines have been disabled in the STIG images:
- Minimum and maximum password expiration
- Account expiration grace period after password expiration
- Account lock after three failed password attempts
- Writing all OS events to logs causes excessive disk usage in rare cases
To learn more, see [ZPA App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform) or [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform).

### Feature Available
#### Update to Automatic Certificate Generation
An update to automatic certificate generation for AppProtection is available. By enabling AppProtection for an application segment and selecting an AppProtection enrollment (CA) certificate, you can automatically generate certificates to support AppProtection TLS inspection.
To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments) and [Generating Zscaler-Issued Enrollment (CA) Certificates](/zpa/generating-zscaler-issued-enrollment-ca-certificates).

## March 19, 2025
### Feature Available
#### AppProtection Control Exceptions
When configuring an AppProtection profile, you can add exceptions to OWASP predefined controls. After you create exceptions, you can review the exceptions under the OWASP predefined controls they are assigned to on the AppProtection Profile page.
To learn more, see [About AppProtection Profiles](/zpa/about-appprotection-profiles) and [Configuring AppProtection Profiles](/zpa/configuring-appprotection-profiles).

## March 18, 2025
### Feature Available
#### Client Connector for VDI Support
ZPA supports a new client type called Client Connector for VDI. Client Connector for VDI is a lightweight client for multi-session VDI environments. Admins can view and configure user-level ZPA policies to protect their multi-session ZPA users.
To learn more, see [What Is Zscaler Client Connector for VDI?](/cloud-branch-connector/what-zscaler-client-connector-vdi), [About Access Policy](/zpa/about-access-policy), and [Configuring Access Policies](/zpa/configuring-access-policies).

### Feature Available
#### ZPA API Support for Multi-Session VDI
A new client type is available in the ZPA cloud service API to support multi-session VDI.
To learn more, see the [API Developer & Reference Guide](/zpa/zpa-api/api-developer-reference-guide), [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api#getClientTypes), and [Configuring Log Streaming Service Configurations Using API](/zpa/configuring-log-streaming-service-configurations-using-api#getClientTypes).

## March 14, 2025
### Feature Available
#### STIG VM Image Update for Nutanix
A Red Hat Enterprise Linux 9 App Connector image that supports Security Technical Implementation Guide (STIG) without requirements to disable password expiration is available for Nutanix. The Nutanix STIG-hardened image that was released on December 12, 2024, required the password to be disabled. To verify if your image is affected, see [Disabling Password Expiration for STIG-Hardened App Connector Images](/zpa/disabling-password-expiration-stig-hardened-app-connector-images#verify).
The following guidelines have been disabled in the STIG image:
- Minimum and maximum password expiration
- Account expiration grace period after password expiration
- Account lock after three failed password attempts
- Writing all OS events to logs causes excessive disk usage in rare cases
To learn more, see [ZPA App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform).

### Feature Available
#### STIG VM Image Updates for VMware
Red Hat Enterprise Linux 9 App Connector and Private Service Edge images that support Security Technical Implementation Guide (STIG) without requirements to disable password expiration are available for VMware. The VMware STIG-hardened images that were released on December 12, 2024, required the password to be disabled. To verify if your image is affected, see [Disabling Password Expiration for STIG-Hardened App Connector Images](/zpa/disabling-password-expiration-stig-hardened-app-connector-images#verify) or [Disabling Password Expiration for STIG-Hardened Private Service Edge Images](/zpa/listpgm1/disabling-password-expiration-stig-hardened-zpa-private-service-edge-images#verify).
The following guidelines have been disabled in the STIG images:
- Minimum and maximum password expiration
- Account expiration grace period after password expiration
- Account lock after three failed password attempts
- Writing all OS events to logs causes excessive disk usage in rare cases
To learn more, see [ZPA App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform) or [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform).

## March 13, 2025
### Feature Available
#### Business Continuity Support
ZPA Business Continuity ensures continued access to applications for users in events where the reachability or availability of the ZPA cloud is affected. ZPA Business Continuity requires Business Continuity Settings, Private Clouds, and Private Cloud Controllers to be configured in the ZPA Admin Portal. Private Cloud Controller dashboard and diagnostics are available to help you monitor the health and diagnose issues for your organization's Private Cloud Controllers.
As part of this feature, the Private Cloud for Business Continuity field has been included when adding or editing an App Connector group or ZPA Private Service Edge group.
To learn more, see [Understanding Business Continuity](/zpa/understanding-business-continuity), [Configuring Business Continuity Settings](/zpa/configuring-business-continuity-settings), [About Private Clouds](/zpa/about-private-clouds), [About Private Cloud Controllers](/zpa/about-private-cloud-controllers), [Viewing the Private Cloud Controllers Dashboard](/zpa/viewing-private-cloud-controllers-dashboard), [Accessing the Private Cloud Controller Status Diagnostics](/zpa/accessing-private-cloud-controller-status-diagnostics), [Configuring App Connectors](/zpa/configuring-connectors), and [Configuring ZPA Private Service Edges](/zpa/configuring-service-edges).

### Feature Available
#### LSS Support for Private Cloud Controllers
An update was released in the Log Streaming Service (LSS) to provide stats for Private Cloud Controller status and metrics. The new log types can be selected when [configuring a log receiver](/zpa/configuring-log-receiver#Step2).
To learn more, see [Understanding Private Cloud Controller Status Log Fields](/zpa/understanding-private-cloud-controller-status-log-fields) and [Understanding Private Cloud Controller Metrics Log Fields](/zpa/understanding-private-cloud-controller-metrics-log-fields).

## March 10, 2025
### Feature Available
#### Microphone and Camera Functionality for Isolation Profiles in ZPA
Isolation allows microphone and camera functionality on the user's device while in an isolated browser. This can be enabled per isolation profile if Turbo Mode is also enabled.
[See image.](#mic-and-camera-toggle)
To learn more, see [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa).
[]![Enable the toggle to allow microphone and camera functionality for your device while in Isolation.](/sites/default/files/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/ZPA-RN-mic-camera.png)

### Feature Available
#### Role-Based Access Control for ZPA API
Granular role-based access control (RBAC) for ZPA API is available. You can select predefined roles or custom roles for API keys when adding them in the API Keys page of the ZPA Admin Portal. To enforce RBAC on all publicly available ZPA API operations, create a predefined or custom role in the ZPA Admin Portal, and then create an API client in the ZIdentity Admin Portal.
[See image.](#API-Keys-Page)
To learn more, see [Understanding Role-Based Access Control for ZPA API](/zpa/understanding-role-based-access-control-zpa-api), [About API Key Management](/zpa/about-api-key-management), [Adding API Keys](/zpa/adding-api-keys), [About API Clients](/zidentity/about-api-clients), and [Adding an API Client](/zidentity/adding-api-client).
[]![Viewing Roles for API Keys ](/sites/default/files/downloads/zpa/api-key-management/adding-api-keys/zpa-api-keys-page-release-note2.png)

## March 06, 2025
### Feature Available
#### STIG VM Image Updates for AWS and GCP
Red Hat Enterprise Linux 9 App Connector and Private Service Edge images that support Security Technical Implementation Guide (STIG) without requirements to disable password expiration are available for Amazon Web Services (AWS) and Google Cloud Platform (GCP). AWS and GCP STIG-hardened images released on November 24, 2024, required the password to be disabled. To verify if your image is affected, see [Disabling Password Expiration for STIG-Hardened App Connector Images](/zpa/disabling-password-expiration-stig-hardened-app-connector-images#verify) or [Disabling Password Expiration for STIG-Hardened Private Service Edge Images](/zpa/listpgm1/disabling-password-expiration-stig-hardened-zpa-private-service-edge-images#verify).
The following guidelines have been disabled in the STIG images:
- Minimum and maximum password expiration
- Account expiration grace period after password expiration
- Account lock after three failed password attempts
- Writing all OS events to logs causes excessive disk usage in rare cases
To learn more, see [ZPA App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform) or [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform).

## March 05, 2025
### Feature Available
#### Microsegmentation Admin Config Resource Type Update
A new resource type for Microsegmentation Admin Config was added to the Audit Logs page.
[See image.](#MicrosegmentationResourceTypes)
To learn more, see [About Audit Logs](/zpa/about-audit-logs#resourceType) and [About Audit Log Fields](/zpa/about-audit-log-fields).
[]![Applying a Resource Type filter in the Audit Logs page of the ZPA Admin Portal](/sites/default/files/downloads/zpa/zpa-microsegmentation-admin-config-resourceType.png)

## March 03, 2025
### Feature Available
#### Disconnect Time UX Improvement for App Connectors
Resolved a UX issue in the ZPA Admin Portal where the App Connector disconnect time appeared as zero.
To learn more, see [Accessing App Connector Status Diagnostics](/zpa/accessing-connector-diagnostics).

### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 7.x, 8.x, and 9.x.
You can download the Manager software for [App Connectors](/zpa/app-connector-deployment-guide-linux) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux) from our repository. The Manager software version is 25.42.4. To learn more, see [Understanding the Manager Software](/zpa/understanding-manager-software).

### Feature Available
#### Platform Information Available for User Activity Log
An update was made to support the platform where Zscaler Client Connector is installed in the User Activity Logs.
To learn more, see [Accessing User Activity Diagnostics](/zpa/accessing-user-activity-diagnostics).

### Feature in Limited Availability
#### Extranet Application Support Available on Cloud & Branch Connectors
Extranet Application Support is available on ZPA Cloud Connectors and Branch Connectors.
To learn more, see [About Extranet](/zia/about-extranet), [About Cloud Connectors](/zpa/about-cloud-connectors), and [About Branch Connectors](/zpa/about-branch-connectors).

## February 28, 2025
### Feature Available
#### Managed Browser Access and Portal Certificates
You can publish Browser Access applications, user portals, and Privileged Remote Access (PRA) Portals with Zscaler-managed certificates and DNS. This reduces the need to create and renew custom certificates.
You can also publish links from a user portal in a PRA privileged portal to provide a unified end user experience.
To learn more, see [Configuring User Portals](/zpa/configuring-user-portals), [Configuring Privileged Portals](/zpa/configuring-privileged-portals), and [Configuring Defined Application Segments](/zpa/configuring-application-segments#BAsteps).

## February 25, 2025
### Feature Available
#### Cookie Persistence Renamed to Persistent State for Isolation Profiles
In ZPA isolation profiles, the cookie persistence toggle has been updated to be called Persistent State.
[See image.](#new-toggle-name)
To learn more, see [Using Persistent State for Isolation](/isolation/using-persistent-state-isolation) and [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa).
[]![Persistent State toggle enabled](/sites/default/files/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/Persistent-State_enabled.png)

### Feature Available
#### Credential Pooling for Privileged Remote Access (PRA)
You can assign multiple privileged credentials within a privileged credentials policy using a privileged credential pool. When you create a privileged credential pool, you can include one or more privileged credentials. This allows users to simultaneously access the same privileged console, but with different privileged credentials from the available set in the privileged credential pool. You can view the privileged credential ID and privileged credential pool IDs on the User Activity Diagnostics page. This feature is only available with a license. Contact your account manager for more information.
To learn more, see [About Privileged Credential Pools](/zpa/about-privileged-credential-pools), [Configuring Privileged Credentials Policies](/zpa/configuring-privileged-credentials-policies), and [Accessing User Activity Diagnostics](/zpa/accessing-user-activity-diagnostics).

### Feature Available
#### Generating AI-Powered Recommendations for Application Segments
ZPA allows you to generate AI-powered recommendations for application segments. You can view the time when the recommendations were last generated and the next time the recommendations will be available.
[See image.](#generate)
To learn more, see [About AI-Powered Recommendations for Application Segments](/zpa/about-ai-powered-recommendations-application-segments).
[]
![Generate AI-powered recommendations](/sites/default/files/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-ai-powered-recommendations-application-segments/zpa-ai-powered-recommendations-generate-blue-release%20note.png)

### Feature Available
#### My Approvals in the PRA Portal
You can create and manage privileged approval requests, approve existing privileged approvals, and reject existing privileged approvals in the Privileged Remote Access (PRA) Portal. You can view the analytics for the privileged approval requests on the Requests page in the ZPA Admin Portal. This feature is only available with a license. Contact your account manager for more information.
To learn more, see [About My Approvals](/zpa/about-my-approvals), [Creating Approvals in the PRA Portal](/zpa/creating-approvals-pra-portal), [Reviewing Privileged Approvals in the PRA Portal](/zpa/reviewing-privileged-approvals-pra-portal), and [Accessing Privileged Requests](/zpa/accessing-privileged-requests).

### Feature Available
#### User Platform Filter for Activity Logs
A new diagnostics user activity filter was introduced to support filtering user activity by client platform (i.e., Windows, macOS, Linux, Android, or iOS).
To learn more, see [Accessing User Activity Diagnostics](/zpa/accessing-user-activity-diagnostics).

## February 24, 2025
### Feature Available
#### Increased Administrators Limit
The maximum limit of administrators per organization has increased to 5,000.
To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).

## February 20, 2025
### Feature Available
#### ZPA API Log Streaming Service (LSS) Support for Microsegmentation
LSS support for Microsegmentation is available in the ZPA API when creating or updating LSS configurations using the `zms_flow_log` log type.
To learn more, see [Managing Log Streaming Service Configurations Using API](/zpa/managing-log-streaming-service-configurations-using-api) and the [API Developer & Reference Guide](/zpa/log-streaming-service-lss-configuration).

### Feature in Limited Availability
#### Azure Virtual Machine Support for Microsegmentation
Agents deployed in Azure virtual machines provide visibility into the Azure cloud environment, including user-defined tags. The Azure environment variables and user-defined tags can be used to configure resource groups.

### Feature in Limited Availability
#### Enforcement Flow Logs Enhancements for Microsegmentation
Microsegmentation flow logs are enhanced to include fields and filters for policy information, such as Action, Rule Name, and Enforcement Reason.
[See image.](#Flow-Logs-new-filters)
[]![Go to Analytics then click Flow Logs and view the new filter additions.](/sites/default/files/downloads/zpa/microsegmentation/policy/about-microsegmentation-policies/Flow-Logs-enhancements_Release-Notes.png)

### Feature in Limited Availability
#### Log Streaming Service Support for Microsegmentation
Microsegmentation policy enforcement flow logs can be sent to an admin's external SIEM via the ZPA Log Streaming Service (LSS) for archival and analysis.
Microsegmentation audit logs are already streamed via LSS as part of ZPA audit logs.

### Feature in Limited Availability
#### Microsegmentation Policy Enforcement
Admins can create Layer 3 and Layer 4 Microsegmentation enforcement policies to protect east-west traffic in both cloud and data center environments. Global policy enforcement settings such as enablement and default policy selection can be found in the ZPA Admin Portal under Microsegmentation > Policy > Settings.
[See image.](#Policy-Settings)
[]![The user can navigate to the new policy enforcement section by going to Microsegmentation then clicking Policy.](/sites/default/files/downloads/zpa/microsegmentation/policy/about-microsegmentation-policies/Microsegmentation-Policy-Enforcement_Release-Notes.png)

### Feature in Limited Availability
#### Policy Map in Microsegmentation
The Policy Map provides a read-only graphical view of Microsegmentation policy configurations. Admins can view policies that are configured for particular AppZones by selecting from the AppZone drop-down menu. They can also see a bird's-eye view of what other policies might need to be configured.
[See image.](#Policy-Map)
[]![Click Policy and then Policy Map to see the read-only graph of policy configurations.](/sites/default/files/downloads/zpa/microsegmentation/policy/about-microsegmentation-policies/Policy-Map_Release-Notes.png)

### Feature in Limited Availability
#### Resource Group Configuration for Microsegmentation
Resource groups are the anchor for configuring Microsegmentation enforcement policies. Admins can create resource groups based on a combination of the resources added to them and a mix of dynamic criteria, including hosts, environments, and cloud tag data. Resource groups can be found in the ZPA Admin Portal under Microsegmentation > Resource Management > Resource Groups.
[See image.](#Resource-Groups-page)
[]![You can configure and manage resource groups by going to Resource Management then clicking Resource Groups. ](/sites/default/files/downloads/zpa/microsegmentation/policy/about-microsegmentation-policies/Resource-Groups_Release-Notes.png)

## February 19, 2025
### Feature in Limited Availability
#### App Segment Multimatch Rule Processing
Multimatch is a feature that allows an application request to match multiple application segments. When Multimatch is enabled, policy evaluation is applied to multiple application segments, whereas the policy evaluation is applied to a single application segment for the default behavior. The same functionality is supported via the ZPA cloud service API.
[See image.](#enable-multimatch)
To learn more, see [Using Application Segment Multimatch](/zpa/using-app-segment-multimatch) and [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).
[]
![Enabling Multimatch in the Edit Application Segment Workflow](/sites/default/files/downloads/zpa/sharing-defined-application-segments/Edit-App-Segment_Multimatch-toggle_squircle.png)

### Feature in Limited Availability
#### Pattern Matching for Application Segments
Admins can define applications with patterns within application segments. Pattern matching allows the policy evaluation to be used with hostname patterns instead of exact fully qualified domain names (FQDNs). The same functionality is supported via the ZPA cloud service API.
To learn more, see [Using Pattern Matching for Application Segments](/zpa/using-pattern-matching-application-segments) and [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).

## February 18, 2025
### Feature Available
#### Transaction ID in Audit Logs
An update was released to include a Transaction ID column on the Audit Logs page of the ZPA Admin Portal. A Transaction ID, created by the OneAPI framework, is the unique identifier that binds multiple related API requests to assist in troubleshooting API request issues.
[See image.](#auditLogs_transactionID)
To learn more, see [About Audit Logs](/zpa/about-audit-logs) and [OneAPI Authentication](/zidentity/integration/oneapi-authentication).
[]![Viewing the Transaction ID column](/sites/default/files/downloads/tech-pubs-drafts/zpa-draft-articles/about-audit-logs-doc-54957/zpa-transactionId-audit-logs.png)

### Feature in Limited Availability
#### Backup and Restore
You can create a backup of configuration settings in the ZPA Admin Portal. After a backup is created, you can restore a backup and return to the previous configuration.
[See image.](#BackupAndRestore)
In addition, the following updates were made to the events and notifications features:
- Log data for backup and restore is populated in the Events Diagnostics. This includes new events for backup and restore, backup name, and backup ID.
- New events are available when configuring notifications that notify the user when a backup or restore has completed or failed.
Contact Zscaler Support to enable this feature for your organization.
To learn more, see [About Backup and Restore](/zpa/about-backup-and-restore), [Restoring Policies and Configurations from a Backup](/zpa/restoring-policies-and-configurations-backup), [Creating Scheduled Backup Configurations](/zpa/creating-scheduled-backup-configurations), [Viewing and Managing Events Diagnostics](/zpa/viewing-and-managing-events-diagnostics), [About Notifications](/zpa/about-notifications), and [Configuring Notifications](/zpa/configuring-notifications).
[]![Viewing the Backup and Restore page](/sites/default/files/downloads/zpa/notification-management/editing-notifications/zpa-backup-restore-page-no-annotations.png)

## February 10, 2025
### Feature Available
#### Quarterly Business Review Reports
View or download Quarterly Business Review (QBR) reports from the ZPA Admin Portal to review insights into how Zscaler helps protect your network. The reports provide emerging traffic trends of private application usage across your organization.
[See image.](#qbr-download-rn)
To learn more, see [Viewing Quarterly Business Review Reports](/zpa/viewing-quarterly-business-review-reports).
[]
![Quarterly Business Review Reports](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2024/ZPA-QBR.png)

## February 04, 2025
### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and Private Service Edge RPM packages for Red Hat Enterprise Linux 7.x, 8.x, and 9.x. If you have IMDSv2 set to Required, the Manager software update is highly recommended. The Manager software version is 24.692.9.
You can download the Manager software for [App Connectors](/zpa/app-connector-deployment-guide-linux) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux) from our repository. To learn more, see [Understanding the Manager Software](/zpa/understanding-manager-software).

## January 16, 2025
### Feature Available
#### Invalid System Listen IP Address Configuration for Events and Notifications
An update was released to add system metrics to the events diagnostics and notification management service for invalid listen IP address configurations on a ZPA Private Service Edge.
To learn more, see [Viewing and Managing Events Diagnostics](/zpa/viewing-and-managing-events-diagnostics) and [Configuring Notifications](/zpa/configuring-notifications).

### Feature Available
#### Manager Software Updates
A recommended update was released that includes updated App Connector and ZPA Private Service Edge RPM packages for Red Hat Enterprise Linux 7.x, 8.x, and 9.x. The Manager software version is 24.692.8.
You can download the Manager Software for [App Connectors](/zpa/app-connector-deployment-guide-linux) or [ZPA Private Service Edges](/zpa/private-service-edge-deployment-guide-linux) from our repository. To learn more, see [Understanding the Manager Software](/zpa/about-manager-software#managerUpgrades).

## January 10, 2025
### Feature Available
#### AI-Powered Recommendations Updates
The AI-Powered Recommendations page was updated to include:
- User recommendations based on the SCIM groups if the SCIM groups are synced for application segments access.
- A new column called Attack Surface Reduction that displays the percentage difference between potential users and recommended users.
- The capability to download a CSV file with all AI-powered recommended application segments.
To learn more, see [About AI-Powered Recommendations for Application Segments](/zpa/about-ai-powered-recommendations-application-segments) and [Configuring AI-Powered Recommendation Settings](/zpa/configuring-ai-powered-recommendations-settings).

### Feature Available
#### Recommended Application Segments Renamed to AI-Powered Recommendations
An update was released that renamed Recommended Application Segments to AI-Powered Recommendations on the Application Segments page. The Description column was consolidated into the Grouping Reasons column. The Settings page is now a drawer located on the AI-Powered Recommendations page. These updates do not change any current functionality.
[See image.](#AI-Powered-Recommendations)
To learn more, see [About AI-Powered Recommendations for Application Segments](/zpa/about-ai-powered-recommendations-application-segments) and [Configuring AI-Powered Recommendations Settings](/zpa/configuring-ai-powered-recommendations-settings).
[]
![AI-Powered Recommendations](/sites/default/files/downloads/zpa/release-notes/zpa-service-release-notes/release-upgrade-summary-2025/ZPA-AI-Powered-Recommendations-ReleaseNote_0.png)

## January 09, 2025
### Feature Available
#### STIG Platform Image Support on Microsoft Azure
A new Red Hat Enterprise Linux 9 Private Service Edge image that supports Security Technical Implementation Guide (STIG) is available for Microsoft Azure.
To learn more, see [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform).
Passwords for STIG-hardened images automatically expire after 60 days. If the password expires without disabling or changing its expiration, admin access to the ZPA Private Service Edge becomes unavailable. When admin access expires, the only recovery method is to deploy a new ZPA Private Service Edge.
To learn how to disable password expiration for STIG-hardened images, see [Disabling Password Expiration for STIG-Hardened ZPA Private Service Edge Images](/zpa/disable-password-expiration-stig-hardened-private-service-edge-images).

### Feature in Limited Availability
#### Application Segment Import for Merging Application Segment Data
Users can upload application data through Application Segment Import and merge the uploaded data to easily configure defined application segments. This allows granular application data to be imported in bulk and later used for different configurations depending on the type of application segment needed.
To learn more, see [Using Application Segment Import](/zpa/using-application-segment-import) and [Merging Imported Application Segments](/zpa/merging-imported-application-segments).

## January 08, 2025
### Feature in Limited Availability
#### Extranet Application Support
Extranet allows Zscaler customers to access a business partner's private application without needing to install an App Connector in the partner's environment or extend an IPSec tunnel from the customer's data center to the business partner's data center. Instead, a Zscaler customer's business partner can establish IPSec tunnels directly to the Zero Trust Exchange (ZTE). This significantly reduces operational complexity and empowers customers to leverage ZTE to access partner applications in a seamless and secure way.
Extranet applications leverage the ZIA cloud for partner onboarding, IPSec, and location management. These locations and location groups for business partners are synchronized to the ZPA cloud and mapped to the server group using Extranet as a new connector type in application segments. This ensures that only authorized users can access the partner's application.
To access Extranet Application Support, contact your Zscaler Account team.
To learn more, see [About Extranet](/zia/about-extranet), [Configuring Server Groups](/zpa/configuring-server-groups), [Configuring Application Segments](/zpa/configuring-application-segments), and [Configuring Access Policies](/zpa/configuring-access-policies).
