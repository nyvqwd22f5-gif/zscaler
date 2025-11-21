# About Mobile Administration Audit Logs
Source: https://help.zscaler.com/unified/about-mobile-administration-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1490896.pdf

Zscaler records the session information for each admin that signs in to the Admin Portal. The audit log displays information related to sign-in or sign-out attempts (e.g., timestamps, actions, IP addresses, etc.) and any configuration changes that were completed during their session such as updates or deletes.
Audit logs provide the following benefits and enable you to:
- Analyze administration sessions by reviewing in-depth information such as actions, categories, interface, or configuration changes (e.g., forwarding profile modifications, device posture alterations, etc.)
- Detect and investigate suspicious activity and track unauthorized access to the administrative user interface, demonstrating compliance with security policies.
- Customize filters to search for selected items and export them to a CSV file.
- Review configuration changes for comparison of the before-and-after administration sessions.
If an admin account makes five unsuccessful attempts to log in within one minute, the account is locked out for five minutes and the failed attempts are recorded in the audit log. Audit logs are stored for up to 6 months.
About the Mobile Administration Audit Logs Page
On the Audit Logs page (Administration > Admin Management > Audit Logs > Mobile Administration), you can do the following:
- Filter the table by time range, action, category, sub-category, and result by selecting the appropriate option from the drop-down menus.
- Hide filters.
- Export the audit entries to a CSV file.
- Search for audit entries based on Client IP, Resource, or Admin ID.
- View a list of actions that have occurred. For each action, you can see:
- **Timestamp**: The local time of the admin’s last login or last logout.
- **Action**: The action performed by the admin.
- [List of all potential actions](#potential-actions)
- [You can also see configuration changes for each action](#action-configuration-changes)
- **Category**: A location in the Admin Portal where the action was performed.
- [List of all potential categories](#potential-categories)
- **Sub-Category**: The specific location within a category.
- [List of all potential sub-categories](#potential-sub-categories)
- **Resource**: The specific location within a sub-category.
- **Admin ID**: The admin’s login ID.
- **Client IP**: The source IP address for the admin.
- **Result**: The outcome of an action.
- If the action was a success, it will show as a green circle with a check mark inside.
- If the action was a failure, it will show as a red circle with an X inside.
![Mobile Administration Audit Logs page](/downloads/unified/administration/audit-logs/about-mobile-administration-audit-logs/client-connector-audit-logs.png)
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
- Private Applications Service Entitlement
- Zscaler Client Connector IdP