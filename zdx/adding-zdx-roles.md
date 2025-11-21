# Adding ZDX Roles
Source: https://help.zscaler.com/zdx/adding-zdx-roles
PDF: https://help.zscaler.com/pdf/com/en/1358811.pdf

ZDX roles are used by admins to create levels of permissions for other admin users within an organization. To learn more, see [About ZDX Role-Based Administration](/zdx/about-zdx-role-based-administration).
Access permissions for some features depend on the subscription level. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
To add a ZDX role:
- Go to **Administration **> **Role Management**.
-
Click **Add ZDX Role**.
The **Add ZDX Role** window appears.
-
In the **Add ZDX Role** window:
- **Name**: Enter a name for the role.
- **Permissions**: Select the permissions for the administrator role:
- [Dashboard Access](#DashboardAccess)
- [Device and User Information](#DeviceUserInformation)
- [UCaaS Monitoring](#UCaaSMonitoring)
- [Analytics](#Analytics)
- [Configuration Access](#ConfigurationAccess)
- [Administrator Management](#AdministratorManagement)
- [Locations](#Locations)
- [User Management](#UserManagement)
- [Remote Assistance Management](#RemoteAssistanceManagement)
- [Diagnostics](#Diagnostics)
- [Alerts](#Alerts)
- [Webhooks](#Webhooks)
- [Zscaler Client Connector Portal](#ZscalerClientConnectorPortal)
- [Time Duration](#TimeDuration)
- [Inventory Management](#InventoryManagement)
- [Self Service](#SelfService)
- [Copilot](#Copilot)
- [Wi-Fi Dashboard](#WiFiDashboard)
- [Device Health Scoring](#DeviceHealthDashboard)
[See image.](#Add-ZDX-Role-Window)
- Click **Save** and [activate the changes](/zdx/saving-and-activating-changes-admin-portal).
[]
![Adding ZDX Role Window](/downloads/zdx/administration/adding-zdx-roles/ZDX-Add-ZDX-Role-13.png)
[]Choose one of the following permissions for access to the predefined dashboards and overviews:
- **View Only**: Allows admins to view all dashboards and overviews.
- **None**: Does not allow admins access to dashboards and overviews.
- **Custom**: Allows admins to view specific dashboards or overviews.
If the Dashboard permission setting is set to View Only or the UCaaS permission setting is set to View Only or Full, you can view the ZDX Dashboard and applications.
For **Custom**, choose to give the following specified permissions for access to specific dashboards or overviews:
- [ZDX Dashboard](#ZDXDashboard)
- [Application Overview](#ApplicationsOverview)
- [Application Dashboard](#ApplicationDetails)
- [User Overview](#UsersOverview)
- [User Dashboard](#UserDetails)
- [Incident Dashboard](#IncidentsDashboard)
- [Probe Assignments](#ProbeAssignments)
- [ZIA PSE Health Dashboard](#PSEDashboard)
- [Network Intelligence](#NetworkIntelligence)
- [Device Events](#DeviceEvents)
[]Choose one of the following permissions for access to the Performance dashboard:
- **View Only**: Allows admins to view the Performance dashboard.
- **None**: Does not allow admins access to the Performance dashboard.
To learn more, see [Monitoring the Performance Dashboard](/zdx/monitoring-performance-dashboard).
[]Choose one of the following permissions for access to the Applications Overview:
- **View Only**: Allows admins to view the Applications Overview.
- **None**: Does not allow admins access to the Applications Overview.
To learn more, see [Monitoring the Applications Overview](/zdx/monitoring-applications-overview).
[]Choose one of the following permissions for access to the Application details:
- **View Only**: Allows admins to view the Application Details.
- **None**: Does not allow admins access to the Application Details.
To learn more, see [Monitoring the Applications Overview](/zdx/monitoring-applications-overview).
[]Choose one of the following permissions for access to the Users Overview:
- **View Only**: Allows admins to view the Users Overview.
- **None**: Does not allow admins access to the Users Overview.
To learn more, see [Monitoring the Users Overview](/zdx/monitoring-users-overview).
[]Choose one of the following permissions for access to the User Details:
- **View Only**: Allows admins to view the User Details.
- **None**: Does not allow admins access to the User Details.
To learn more, see [Evaluating User Details](/zdx/evaluating-user-details).
[]Choose one of the following permissions for access to the Incidents dashboard:
- **View Only**: Allows admins to view the Incidents dashboard.
- **None**: Does not allow admins access to the Incidents dashboard.
To learn more, see [Monitoring the Incidents Dashboard](/zdx/monitoring-incidents-dashboard).
[]Choose one of the following permissions for access to the Probe Assignment system-generated report:
- **View Only**: Allows admins to view the Probe Assignment system-generated report.
- **None**: Does not allow admins access to the Probe Assignment system-generated report.
To learn more, see [Viewing System-Generated Reports](/zdx/viewing-system-generated-reports).
[]Choose one of the following permissions for access to the Zscaler Internet Access (ZIA) Private Service Edge (PSE) Health dashboard:
- **View Only**: Allows admins to view the ZIA PSE Health dashboard.
- **None**: Does not allow admins to manage or view the ZIA PSE Health dashboard.
To learn more, see [Monitoring the ZIA Private Service Edge Dashboard](/zdx/monitoring-zia-private-service-edge-dashboard).
[]Choose one of the following permissions for access to the Network Intelligence dashboard:
- **View Only**: Allows admins to view the Network Intelligence dashboard.
- **None**: Does not allow admins to manage or view the Network Intelligence dashboard.
To learn more, see [Monitoring the Network Intelligence Dashboard](/zdx/monitoring-network-intelligence-dashboard).
[]Choose one of the following permissions for access to the Device Events reports:
- **View Only**: Allows admins to view the Device Events reports.
- **None**: Does not allow admins to manage or view the Device Events reports.
To learn more, see [Viewing the Device Events Reports](/zdx/viewing-device-events-reports).
[]Choose one of the following permissions for access to the Applications and Probes configuration:
- **Full**: Allows admins full access to Configuration Access.
- **View Only**: Allows admins to view what has been set up in Configuration Access.
- **None**: Does not allow admins to have access to Configuration Access.
You cannot configure for users when the [User Name ](#UserNameObf2)permission is set to Obfuscated.
To learn more, see [Configuration](/zdx/configuration).
If the Configuration Access permission setting is set to Full:
- You can enable data collection for Software and Device Inventory on the Inventory Settings page. To learn more, see [Configuring Inventory Settings](/zdx/configuring-inventory-settings).
- You can configure Zscaler Hosted Probes. To learn more, see [Configuring Zscaler Hosted Probes](/zdx/configuring-zscaler-hosted-probes).
[]Choose one of the following permissions for access to Administrator Management, Role Management, Location Management, and Audit Logs:
Although roles are created in Role Management, they are managed by Super Admins.
- **Full**: Allows admins full access to Administrator Management.
- **View Only**: Allows admins to view what has been set up in Administrator Management.
- **None**: Does not allow admins to have access to Administrator Management.
[]Choose one of the following permissions for access to the Zscaler Client Connector Portal:
- **Full**: Allows admins full access to manage the Zscaler Client Connector Portal.
- **View Only**: Allows admins to view the current setup in the Zscaler Client Connector Portal.
- **None**: Does not allow admins access to the Zscaler Client Connector Portal.
[]Choose one of the following permissions for access to the device and user information:
- **Visible**: Allows admins to view device and user information.
- **Obfuscated**: Does not allow admins to view device and user information.
- **Custom**: Allows admins to view specific device and user information.
For **Custom**, choose to give the following specified permissions for access to User Name, Location, Device Name, or IP Address:
- [User Name](#UserName)
- [Location](#Location)
- [Device Name](#DeviceName)
- [IP Address](#IPAddress)
- [Wi-Fi Name](#WiFiName)
If Zscaler Client Connector's Collect Machine Hostname Information or Collect Device Owner Information is disabled, then ZDX obfuscates BSSID, SSID, Device Name, and hostname. To learn more, see [About User Privacy](/client-connector/about-user-privacy).
[][][]Choose one of the following permissions for access to view the user name:
- **Visible**: Allows admins to view the user name.
- **Obfuscated**: Does not allow admins to view the user name.
If the User Name permission is set to Visible, then an admin has access to User Search and the ability to download a table in CSV format for Software Inventory. If the User Name permission is set to Obfuscated, then the admin does not have access to User Search and cannot download a table in CSV format for Software Inventory.
[]Choose one of the following permissions for access to the user location:
- **Visible**: Allows admins to view the user location.
- **Obfuscated**: Does not allow admins to view the user location.
Location obfuscation occurs on Users Overview and User Details pages only.
[]Choose one of the following permissions for access to the device name:
- **Visible**: Allows admins to view the device name.
- **Obfuscated**: Does not allow admins to view the device name.
If the Device Name permission is set to Visible, then an admin has the ability to download a table in CSV format for Software Inventory. If the Device Name permission is set to Obfuscated, then the admin cannot download a table in CSV format for Software Inventory.
[]Choose one of the following permissions for access to the device's IP Address:
- **Visible**: Allows admins to view the device's IP Address.
- **Obfuscated**: Does not allow admins to view the device's IP Address.
[]Choose one of the following permissions for access to the device's Wi-Fi Name:
- **Visible**: Allows admins to view the device's Wi-Fi Name.
- **Obfuscated**: Does not allow admins to view the device's Wi-Fi Name.
[]Choose one of the following permissions for access to Users, Groups, and Departments in User Management:
- **View Only**: Allows admins to view what has been set up in User Management.
- **None**: Does not allow admins to view the User Management setup.
[]Choose one of the following permissions for access to Zscaler locations:
- **View Only**: Allows admins to view Zscaler locations.
- **None**: Does not allow admins to view Zscaler locations.
[]Choose one of the following permissions for access to** **Remote Assistance:
- **Full**: Allows admins to have full access to Remote Assistance Management.
- **View Only**: Allows admins to view what has been set up in Remote Assistance Management.
- **None**: Does not allow admins access to Remote Assistance Management.
[]Choose one of the following permissions for access to Diagnostics:
- **Full**: Allows admins to manage and view Diagnostics sessions, and also view and export the results.
- **View Only**: Allows admins to view details of Diagnostics sessions, but not export the results.
- **None**: Does not allow admins to manage or view Diagnostics sessions or results.
If [User Name](#UserNameObf1) and Device Information are set to Obfuscated, then Diagnostics is not accessible.
[]Choose one of the following permissions for access to Alerts:
- **Full**: Allows admins to configure and view alerts, and also receive alert notifications.
- **View Only**: Allows admins to view alerts and receive alert notifications, depending on rule configuration.
- **None**: Does not allow admins to manage or view alerts, nor receive alert notifications.
If you have Full permission for Alerts:
- You can manage alert rules on the Rules page. To learn more, see [About Rules](/zdx/about-rules).
- You can assign labels to an alert rule. You can also create or assign a Workflow Automation as an alert delivery method. To learn more, see [About Labels](/zdx/about-labels).
- You can manage templates on the Templates page. To learn more, see [About Templates](/zdx/about-templates).
[]Choose one of the following permissions for access to Webhooks:
- **Full**: Allows admins to create, manage, and view webhooks.
- **View Only**: Allows admins to view webhooks.
- **None**: Does not allow admins to manage or view webhooks.
To learn more, see [Configuring Webhooks](/zdx/configuring-webhooks).
[]Choose one of the following permissions for access to UCaaS Monitoring:
- **Full**: Allows admins to manage and view Call Quality applications and Call Quality Meetings pages.
- **View Only**: Allows admins to view Call Quality applications and Call Quality Meetings pages, but not manage them.
- **None**: Does not allow admins to manage or view Call Quality applications or Call Quality Meetings pages.
- **Custom**: Allows admins to manage and view specific Call Quality applications and Call Quality Meetings pages.
If the Dashboard permission setting is set to View Only or the UCaaS permission setting is set to View Only or Full, you can view the ZDX Dashboard and applications.
For **Custom**, choose to give the following specified permissions for access to manage or view specific Call Quality Applications and Call Quality Meetings pages:
- [Call Quality Configuration](#CallQualityConfiguration)
- [Call Quality Meetings](#CallQualityMeetings)
- [Call Quality Applications](#CallQualityApplications)
[]Choose one of the following permissions for access to Call Quality Configuration pages:
- **Full**: Allows admins to manage and view Call Quality Configuration pages.
- **View Only**: Allows admins to view Call Quality Configuration pages, but not manage them.
- **None**: Does not allow admins to manage or view Call Quality Configuration pages.
[]Choose one of the following permissions for access to Call Quality Meetings pages:
- **Full**: Allows admins to manage and view Call Quality Meetings pages.
- **View Only**: Allows admins to view Call Quality Meetings pages, but not manage them.
- **None**: Does not allow admins to manage or view Call Quality Meetings pages.
[]Choose one of the following permissions for access to Call Quality Applications pages:
- **Full**: Allows admins to manage and view Call Quality Applications pages.
- **View Only**: Allows admins to view Call Quality Applications pages, but not manage them.
- **None**: Does not allow admins to manage or view Call Quality Applications pages.
[]Choose one of the following permissions for access to Inventory Management pages:
- **Full**: Allows admins full access to Inventory Management pages.
- **View Only**: Allows admins to view the current setup on the Inventory Management pages, but not manage them.
- **None**: Does not allow admins access to Inventory Management pages.
Inventory Management includes the Software, Hardware, and Process Settings pages.
To learn more, see [Inventory](/zdx/analytics/inventory).
[]Choose one of the following time durations for the ZDX Role:
- 2 hours
- 4 hours
- 6 hours
- 12 hours
- 24 hours
- 48 hours
- Full Access
The default is set to Full Access.
[]Choose one of the following permissions for access to Analytics:
- **Full** or **View Only**: Allows admins to view Analytics pages, but not manage them.
- **None**: Does not allow admins to manage or view Analytics pages.
- **Custom**: Allows admins to manage and view specific Analytics pages.
For **Custom**, choose to give the following specified permissions for access to manage or view specific Analytics pages:
- [QBR](#QBR)
- [System Generated Reports](#SystemGeneratedReports)
- [ZDX Snapshots](#ZDXSnapshots)
- [Data Explorer](#DataExplorer)
- [Hosted Monitoring](#hostedmonitoring)
[]Choose one of the following permissions for access to view the System-Generated Reports page:
- **Full** or **View Only**: Allows admins to view the System-Generated Reports page, but not manage them.
- **None**: Does not allow admins to manage or view the System-Generated Reports page.
To learn more, see [Viewing System-Generated Reports](/zdx/viewing-system-generated-reports).
[]Choose one of the following permissions for access to view the Quarterly Business Review (QBR) page:
- **Full** or **View Only**: Allows admins to view the QBR page, but not manage it.
- **None**: Does not allow admins to manage or view the QBR page.
To learn more, see [Viewing Quarterly Business Review Reports](/zdx/viewing-quarterly-business-review-reports).
[]Choose one of the following permissions for access to the ZDX Snapshots page:
- **Full**: Allows admins to manage the ZDX Snapshots page.
- **View Only**: Allows admins to view the ZDX Snapshots page.
- **None**: Does not allow admins to manage or view the ZDX Snapshots page.
To learn more, see [Sharing ZDX Snapshots](/zdx/sharing-zdx-snapshots).
[]Choose one of the following permissions for access to the Data Explorer page:
- **Full**: Allows admins to manage their views on the Data Explorer page.
- **View Only**: Allows admins to view their Data Explorer page.
- **None**: Does not allow admins to manage or view their Data Explorer page.
An admin cannot manage another admin's Data Explorer views.
To learn more, see [Monitoring Data Explorer](/zdx/monitoring-data-explorer-views) and [Configuring Data Explorer](/zdx/configuring-data-explorer-views).
[]Choose one of the following permissions for access to the Zscaler Hosted Monitoring page:
- **Full** or **View Only**: Allows admins to view the Zscaler Hosted Monitoring page, but not manage it.
- **None**: Does not allow admins to view the Zscaler Hosted Monitoring page.
To learn more, see [Understanding Zscaler Hosted Monitoring](/zdx/understanding-zscaler-hosted-monitoring).
[]Choose one of the following permissions for access to Self Service:
- **Full**: Allows admins to manage Self Service notifications for users and access to the Self Service dashboard.
- **View Only**: Allows admins to view the Self Service dashboard, but not manage Self Service notifications.
- **None**: Does not allow admins to manage Self Service notifications or view the Self Service dashboard.
To learn more, see [Monitoring the Self Service Dashboard](/zdx/monitoring-self-service-dashboard).
[]Choose one of the following permissions for access to the ZDX Copilot page:
- **Full**: Allows admins to access and utilize the ZDX Copilot page.
- **View Only**: Allows admins to view the ZDX Copilot page.
- **None**: Does not allow admins access to ZDX Copilot page.
To learn more, see [About ZDX Copilot](/zdx/about-zdx-copilot).
[]Choose one of the following permissions for access to the Wi-Fi Dashboard:
- **View Only**: Allows admins to view the Wi-Fi Dashboard.
- **None**: Does not allow admins access to the Wi-Fi Dashboard.
To learn more, see [Monitoring the Wi-Fi Dashboard](/zdx/monitoring-wi-fi-dashboard).
[]Choose one of the following permissions for access to the Device Health dashboard:
- **Full **or **View Only**: Allows admins to view the Device Health dashboard.
- **None**: Does not allow admins to manage or view the Device Health dashboard.
To learn more, see [Monitoring the Device Health Dashboard](/zdx/monitoring-device-health-dashboard).