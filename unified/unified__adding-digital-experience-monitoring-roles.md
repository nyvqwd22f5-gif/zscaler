# Adding Digital Experience Monitoring Roles
Source: https://help.zscaler.com/unified/adding-digital-experience-monitoring-roles
PDF: https://help.zscaler.com/pdf/com/en/1491046.pdf

Digital Experience Monitoring roles are used by admins to create levels of permissions for other admin users within an organization. To learn more, see [About Digital Experience Monitoring Role-Based Administration](/unified/about-digital-experience-monitoring-role-based-administration).
Access permissions for some features depend on the subscription level. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#digital-experience).
Admin roles must be assigned via Administrative Entitlements. To learn more, see [About Administrative Entitlements](/zslogin/about-administrative-entitlements)[.]
To add a Digital Experience Monitoring role:
- Go to **Administration **> **Admin Management** > **Role Based Access Control > Digital Experience**.
-
Click **Add ZDX Role**.
The **Add ZDX Role** window appears.
- In the **Add ZDX Role** window:
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
- [Copilot](#Copilot)
- [Zscaler Client Connector features in Admin Portal](#ZscalerClientConnectorPortal)
- [Time Duration](#TimeDuration)
- [Inventory Management](#InventoryManagement)
- [Self Service IT](#SelfService)
- [Wi-Fi Dashboard](#WiFiDashboard)
- Click **Save** and activate the changes.
[]
[]Choose one of the following permissions for access to the predefined dashboards and overviews:
- **View Only**: Allows admins to view all dashboards and overviews.
- **None**: Does not allow admins access to dashboards and overviews.
- **Custom**: Allows admins to view specific dashboards or overviews.
If the Dashboard permission setting is set to View Only or the UCaaS permission setting is set to View Only or Full, you can view the Digital Experience Monitoring Dashboard and applications.
For **Custom**, choose to give the following specified permissions for access to specific dashboards or overviews:
- [Digital Experience Monitoring Dashboard](#ZDXDashboard)
- [Application Overview](#ApplicationsOverview)
- [Application Dashboard](#ApplicationDetails)
- [User Overview](#UsersOverview)
- [User Dashboard](#UserDetails)
- [Incident Dashboard](#IncidentsDashboard)
- [Probe Assignments](#ProbeAssignments)
[]Choose one of the following permissions for access to the Performance Dashboard:
- **View Only**: Allows admins to view the Performance Dashboard.
- **None**: Does not allow admins access to the Performance Dashboard.
To learn more, see [Monitoring the Performance Dashboard](/unified/monitoring-performance-dashboard).
[]Choose one of the following permissions for access to the Applications Overview:
- **View Only**: Allows admins to view the Applications Overview.
- **None**: Does not allow admins access to the Applications Overview.
To learn more, see [Monitoring the Applications Overview](/unified/monitoring-applications-overview).
[]Choose one of the following permissions for access to the Application Details:
- **View Only**: Allows admins to view the Application Details.
- **None**: Does not allow admins access to the Application Details.
To learn more, see [Monitoring the Applications Details](/unified/monitoring-applications-overview).
[]Choose one of the following permissions for access to the Users Overview:
- **View Only**: Allows admins to view the Users Overview.
- **None**: Does not allow admins access to the Users Overview.
To learn more, see [Monitoring the Users Overview](/unified/monitoring-users-overview).
[]Choose one of the following permissions for access to the User Details:
- **View Only**: Allows admins to view the User Details.
- **None**: Does not allow admins access to the User Details.
To learn more, see [Evaluating User Details](/unified/evaluating-user-details).
[]Choose one of the following permissions for access to the Incidents Dashboard:
- **View Only**: Allows admins to view the Incidents Dashboard.
- **None**: Does not allow admins access to the Incidents Dashboard.
To learn more, see [Monitoring the Incidents Dashboard](/unified/monitoring-incidents-dashboard).
[]Choose one of the following permissions for access to the Probe Assignment system-generated report:
- **View Only**: Allows admins to view the Probe Assignment system-generated report.
- **None**: Does not allow admins access to the Probe Assignment system-generated report.
-
To learn more, see [Viewing System-Generated Reports](/unified/viewing-system-generated-reports).
[]Choose one of the following permissions for access to the Wi-Fi Dashboard:
- **View Only**: Allows admins to view the Wi-Fi Dashboard.
- **None**: Does not allow admins access to the Wi-Fi Dashboard.
To learn more, see [Monitoring the Wi-Fi Dashboard](/unified/monitoring-wi-fi-dashboard).
[]Choose one of the following permissions for access to the Applications and Probes configuration:
- **Full**: Allows admins full access to Configuration Access.
- **View Only**: Allows admins to view what has been set up in Configuration Access.
- **None**: Does not allow admins to have access to Configuration Access.
You cannot configure for users when the [User Name permission](#UserNameObf2) is set to Obfuscated.
If the Configuration Access permission setting is set to Full:
- You can enable data collection for Software and Device Inventory on the Inventory Settings page. To learn more, see [Configuring Inventory Settings](/unified/configuring-inventory-settings).
- You can configure Zscaler Hosted Probes. To learn more, see [Configuring Zscaler Hosted Probes](/unified/configuring-zscaler-hosted-probes).
[]Choose one of the following permissions for access to Administrator Management, Role Management, Location Management, and Audit Logs:
Although roles are created in Role Management, they are managed by Super Admins.
- **Full**: Allows admins full access to Administrator Management.
- **View Only**: Allows admins to view what has been set up in Administrator Management.
- **None**: Does not allow admins to have access to Administrator Management.
[]Choose one of the following permissions for access to Client Connector features in the Admin Portal:
- **Full**: Allows admins full access to manage the Admin Portal.
- **View Only**: Allows admins to view the current setup in the Admin Portal.
- **None**: Does not allow admins access to the Admin Portal.
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
If Zscaler Client Connector's Collect Machine Hostname Information or Collect Device Owner Information is disabled, then Digital Experience Monitoring obfuscates BSSID, SSID, Device Name, and hostname. To learn more, see [About User Privacy](/unified/about-user-privacy).
[]Choose one of the following permissions for access to view the user name:
- **Visible**: Allows admins to view the user name.
- **Obfuscated**: Does not allow admins to view the user name.
If the User Name permission is set to Visible, then an admin has access to User Search and the ability to download a table in CSV format for Software Inventory. If the User Name permission is set to Obfuscated, then the admin does not have access to User Search and cannot download a table in CSV format for Software Inventory.
[]Choose one of the following permissions for access to the user location:
- **Visible**: Allows admins to view the user location.
- **Obfuscated**: Does not allow admins to view the user location.
Location obfuscation occurs on User Overview and User Dashboard pages only.
[]Choose one of the following permissions for access to the device name:
- **Visible**: Allows admins to view the device name.
- **Obfuscated**: Does not allow admins to view the device name.
If the Device Name permission is set to Visible, then an admin has the ability to download a table in CSV format for Software Inventory. If the Device Name permission is set to Obfuscated, then the admin cannot download a table in CSV format for Software Inventory.
[]Choose one of the following permissions for access to the device IP Address:
- **Visible**: Allows admins to view the device IP Address.
- **Obfuscated**: Does not allow admins to view the device IP Address.
[]Choose one of the following permissions for access to the device Wi-Fi names:
- **Visible**: Allows admins to view the device Wi-Fi names.
- **Obfuscated**: Does not allow admins to view the device Wi-Fi names.
[]Choose one of the following permissions for access to Users, Groups, and Departments in User Management:
- **View Only**: Allows admins to view what has been set up in User Management.
- **None**: Does not allow admins to view the User Management setup.
[]Choose one of the following permissions for access to Zscaler locations:
- **View Only**: Allows admins to view Locations.
- **None**: Does not allow admins to view Locations.
[]Choose one of the following permissions for access to** **Remote Assistance:
- **Full**: Allows admins to have full access to Remote Assistance Management.
- **View Only**: Allows admins to view what has been set up in Remote Assistance Management.
- **None**: Does not allow admins access to Remote Assistance Management.
[]Choose one of the following permissions for access to Diagnostics:
- **Full**: Allows admins to manage and view Diagnostics sessions, and also view and export the results.
- **View Only**: Allows admins to view details of Diagnostics sessions, but not export the results.
- **None**: Does not allow admins to manage or view Diagnostics sessions or results.
If you User Name and Device Information are set to Obfuscated, then Diagnostics is not accessible.
To learn more, see [About Diagnostics](/unified/about-diagnostics).
[]Choose one of the following permissions for access to Alerts:
- **Full**: Allows admins to configure and view alerts, and also receive alert notifications.
- **View Only**: Allows admins to view alerts and receive alert notifications, depending on rule configuration.
- **None**: Does not allow admins to manage or view alerts, nor receive alert notifications.
If you have the Full permission for Alerts:
- You can manage alert rules on the Rules page. To learn more, see [About Rules](/unified/about-rules).
- You can assign labels to an alert rule. You can also create or assign a Workflow Automation as an alert delivery method. To learn more, see [About Labels](/unified/about-labels).
- You can manage templates on the Templates page. To learn more, see [About Templates](/unified/about-templates).
[]Choose one of the following permissions for access to Webhooks:
- **Full**: Allows admins to create, manage, and view webhooks.
- **View Only**: Allows admins to view webhooks.
- **None**: Does not allow admins to manage or view webhooks.
To learn more, see [Configuring Webhooks](/unified/configuring-webhooks).
[]Choose one of the following permissions for access to the Copilot page:
- **Full**: Allows admins to access and use the Copilot page.
- **View Only**: Allows admins to view the Copilot page.
- **None**: Does not allow admins access to the Copilot page.
To learn more, see [About Copilot](/unified/about-copilot).
[]Choose one of the following permissions for access to UCaaS Monitoring:
- **Full**: Allows admins to manage and view Call Quality applications and Call Quality Meetings pages.
- **View Only**: Allows admins to view Call Quality applications and Call Quality Meetings pages, but not manage them.
- **None**: Does not allow admins to manage or view Call Quality applications or Call Quality Meetings pages.
- **Custom**: Allows admins to manage and view specific Call Quality applications and Call Quality Meetings pages.
If the Dashboard permission setting is set to View Only or the UCaaS permission setting is set to View Only or Full, you can view the Digital Experience Monitoring Dashboard and applications.
For **Custom**, choose to give the following specified permissions for access to manage or view specific Call Quality Applications and Call Quality Meetings pages:
- [Call Quality Configuration](#CallQualityConfiguration)
- [Call Quality Meetings](#CallQualityMeetings)
- [Call Quality Applications](#CallQualityApplications)
[]Choose one of the following permissions for access to Call Quality Configuration pages:
- **Full**: Allows admins to manage and view Call Quality Configuration pages.
- **View Only**: Allows admins to view Call Quality Configuration pages, but not manage them.
- **None**: Does not allow admins to manage or view Call Quality Configuration pages.
[]Choose one of the following permissions for access to Call Quality Meeting pages:
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
To learn more, see [Inventory & Device](/unified/analytics/digital-experience-monitoring/inventory-device).
[]Choose one of the following time durations for the Digital Experience Monitoring Role:
- 2 hours
- 4 hours
- 6 hours
- 12 hours
- 24 hours
- 48 hours
- Full Access
The default is set to Full Access, which allows you to access data for any time duration.
When a Digital Experience Monitoring role is assigned a time duration between 2 hours and 48 hours, the Digital Experience Monitoring admin with that assigned Digital Experience Monitoring Role has access to data relevant to the selected time duration.
For example, when a Digital Experience Monitoring admin has been assigned a Digital Experience Monitoring role with a time duration of 4 hours and changes are applied, then they can access data (e.g., Performance Dashboard) based on the previous 4 hours from the current time.
![After a time duration is selected and applied, the ZDX admin with the assigned ZDX role sees accessible data for that selected time duration.](/downloads/zdx/administration/admin-configuration/adding-zdx-roles/zdx-adding-zdx-roles-time-duration.png)
[]Choose one of the following permissions for access to Analytics:
- **Full** or **View Only**: Allows admins to view Analytics pages, but not manage them.
- **None**: Does not allow admins to manage or view Analytics pages.
- **Custom**: Allows admins to manage and view specific Analytics pages.
For **Custom**, choose to give the following specified permissions for access to manage or view specific Analytics pages:
- [QBR](#QBR)
- [System Generated Reports](#SystemGeneratedReports)
- [Snapshots](#ZDXSnapshots)
- [Data Explorer](#DataExplorer)
- [Hosted Monitoring](#hostedmonitoring)
If you have the Full permission for Analytics, you have access to Zscaler Hosted Monitoring. To learn more, see [Understanding Zscaler Hosted Monitoring](/unified/understanding-zscaler-hosted-monitoring).
[]Choose one of the following permissions for access to view the System-Generated Reports page:
- **Full** or **View Only**: Allows admins to view the System-Generated Reports page, but not manage them.
- **None**: Does not allow admins to manage or view the System-Generated Reports page.
To learn more, see [Viewing System-Generated Reports](/unified/viewing-system-generated-reports).
[]Choose one of the following permissions for access to view the Quarterly Business Review (QBR) page:
- **Full** or **View Only**: Allows admins to view the QBR page, but not manage it.
- **None**: Does not allow admins to manage or view the QBR page.
[]Choose one of the following permissions for access to the Snapshots page:
- **Full**: Allows admins to manage the Snapshots page.
- **View Only**: Allows admins to view the Snapshots page.
- **None**: Does not allow admins to manage or view the Snapshots page.
To learn more, see [Sharing and Managing Snapshots](/unified/sharing-digital-experience-monitoring-snapshots).
[]Choose one of the following permissions for access to the Data Explorer page:
- **Full**: Allows admins to manage their views on the Data Explorer page.
- **View Only**: Allows admins to view their Data Explorer page.
- **None**: Does not allow admins to manage or view their Data Explorer page.
An admin cannot manage another admin's Data Explorer views.
To learn more, see [Monitoring Data Explorer](/unified/monitoring-data-explorer-views) and [Configuring Data Explorer](/unified/configuring-data-explorer-views).
[]Choose one of the following permissions for access to the Zscaler Hosted Monitoring page:
- **Full** or **View Only**: Allows admins to view the Zscaler Hosted Monitoring page, but not manage it.
- **None**: Does not allow admins to view the Zscaler Hosted Monitoring page.
To learn more, see [Understanding Zscaler Hosted Monitoring](/unified/understanding-zscaler-hosted-monitoring).
[]Choose one of the following permissions for access to Self Service:
- **Full**: Allows admins to manage Self Service notifications for users and access to the Self Service dashboard.
- **View Only**: Allows admins to view the Self Service dashboard, but not manage Self Service notifications.
- **None**: Does not allow admins to manage Self Service notifications or view the Self Service dashboard.
To learn more, see [Monitoring the Self Service Dashboard](/zdx/monitoring-self-service-dashboard).