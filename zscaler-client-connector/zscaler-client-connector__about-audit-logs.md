# Understanding Audit Logs
Source: https://help.zscaler.com/zscaler-client-connector/about-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1345601.pdf

Zscaler records the login name and IP address of every admin who logs in to the Zscaler Client Connector Portal and changes policies or configuration settings. Audit logs display an admin's login and logout record (i.e., timestamps, actions, IP, etc.) and any configuration changes they completed. Audit logs are stored for up to 6 months.
To view and filter admin audit log records, go to Administration > Audit Logs.
For each admin audit record, the following information is displayed:
- **Timestamp**: The local time of the admin’s last login or last logout.
- **Action**: The action performed by the admin.
- [List of all potential actions](#potential-actions)
- [You can also see configuration changes for each action](#action-configuration-changes)
- **Category**: A location in the Zscaler Client Connector Portal where the action was performed.
- [List of all potential categories](#potential-categories)
- **Sub-Category**: The specific location within a category.
- [List of all potential sub-categories](#potential-sub-categories)
- **Resource**: The specific location within a sub-category.
- **Admin ID**: The admin’s login ID.
- **Client IP**: The source IP address for the admin.
- **Result**: The outcome of an action.
- If the action was a success, it will show as a green circle with a check mark inside.
- If the action was a failure, it will show as a red circle with an X inside.
In the **Audit Logs** page:
- You can filter the table by time range, action, category, sub-category, and result by selecting the appropriate option from the drop-down menus.
- You can use the Search option to search for audit entries based on Client IP, Resource, or Admin ID.
- You can also use the Export option to export the audit entries.
![The filters for the Audit Log page](/downloads/audit-logs-zscaler-app-filters.png?1604646059)
- []Create
- Delete
- Sign In
- Sign Out
- Update
[]You can view visual differences between pre and post-configuration changes:
- View additions and deletions by clicking on the ![The view additions and deletions icon](/downloads/view-additions-deletions-icon.png)
icon. See an example of an addition.
[See image.](#addition-example)
- View updates by clicking on the ![The view updates icon](/downloads/view-updates-icon.png)
icon. See an example of modifications to a policy.
[See image.](#modification-example)
[]![An example of an addition configuration change](/downloads/addition-configuration-view.png)
[]![An example of a modification configuration change](/downloads/configuration-change-view.png)
- []Activate Policy
- App Profiles
- Device Overview
- Device Posture
- Forwarding Profile
- IdP User Agent
- Login
- Trusted Networks
- Zscaler Client Connector IdP
- Zscaler Client Connector Notifications
- Zscaler Client Connector Store
- Zscaler Client Connector Support
- Zscaler Service Entitlement
- []Activate Policy
- Advanced Configuration
- Android App Profiles
- App Fail Open
- App Supportability
- AUP Settings
- Device Cleanup
- Device Posture
- End Point Integration
- Export Enrolled Devices
- Force Remove Device
- Forwarding Profile
- IdP User Agent
- iOS App Profiles
- Login
- macOS App Profiles
- Reminder Notification Settings
- Soft Remove Device
- System Tray Notification Settings
- Traceroute Policy
- Trusted Networks
- Update Applications
- User Privacy
- Windows App Profiles
- ZPA Service Entitlement
- Zscaler Client Connector IdP