# About Administrators
Source: https://help.zscaler.com/zpa/about-administrators
PDF: https://help.zscaler.com/pdf/com/en/1483551.pdf

ZPA initially provides a default admin account for your organization (i.e., zpaadmin@<your organization's domain>.com or admin@<your organization's domain>.com). You can configure as many additional admins as necessary. For each admin, you can choose a predefined role or create a custom role. To learn more, see [About Roles](/zpa/about-roles).
Administrators provide the following benefits and enable you to:
- Access the ZPA Admin Portal.
- Provision or manage administrator roles for your organization.
- View a list of all admins that are configured for your organization.
If your organization is subscribed to Shift and ZPA, the admin roles for both services are displayed. In this situation, Zscaler recommends selecting either the ZPA Administrator or ZPA Read Only Administrator role when creating new admin accounts for ZPA.
About the Administrators Page
On the Administrators page, the admins are listed as read-only if you are subscribed to ZIdentity. ZPA admins must be assigned in the [ZIdentity Admin Portal](/zslogin/accessing-and-navigating-zslogin-admin-portal). To learn more, see [About Administrative Entitlements](/zslogin/about-administrative-entitlements) and [What Is ZIdentity?](/zslogin/what-zslogin)
On the Administrators page (Configuration & Control > Administration Control > Administrators), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters **to display the filters.
- Refresh the Administrators page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new admin](/zpa/about-user/new).
- Expand all rows in the table to see more information about each admin.
- View a list of all admins that are configured for your organization. For each admin, you can see:
- **Admin ID**: The username for the admin.
- **Role**: The role for the admin.
- **Status**: Indicates that the admin is enabled or disabled.
- **Two-Factor Authentication**: If two-factor authentication (2FA) is enabled or disabled for the admin.
- **Two-Factor Auth Type**: If two-factor authentication is enabled, the authentication type is displayed in this column.
- Unlock a locked user or administrator.
Locking occurs automatically after three login attempts with invalid credentials and persists for 30 minutes.
- [Edit an existing admin](/zpa/about-user/edit).
The default ZPA Administrator role can be disabled when editing an admin if another role with ZPA Administrator privileges exists. Disabling your own ZPA Administrator role is not allowed. It can take up to two minutes for updates to an admin's permissions for an existing role to take effect.
- Delete an admin.
The ZPA Administrator role does not have permission to delete any users with Shift role privileges. Only users with [Administrator](/shift/configuring-administrators) or Shift Administrator privileges can delete users with Shift role privileges.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Roles](/zpa/about-roles) page to add new admin roles or manage existing roles.
- Go to the [Audit Logs](/zpa/about-audit-logs) page to view and download admin audit log records.
- Go to the [Acceptable Use Policy](/zpa/about-user-portal-acceptable-use-policy) page to view or update the AUP for your [user portals](/zpa/user-portal).
-
Go to the [Microtenants](/zpa/about-microtenants) page to add new Microtenants or manage existing Microtenants.
The Microtenants page is only visible for Default Microtenant admins.
- Go to the [Client Sessions](/zpa/about-client-sessions) page to view or delete current sessions.
- Go to the [Disaster Recovery](/zpa/understanding-disaster-recovery) page to view critical application segments, ZPA Private Service Edge groups, or App Connector groups that are designated for disaster recovery. You can also view and configure the [disaster recovery settings](/zpa/about-disaster-recovery-settings).
-
Go to the [Integrations](/zpa/about-integrations) page to set up File Transfer via Zscaler Internet Access (ZIA).
The Integrations page is read-only for [Microtenant](/zpa/about-microtenants) admins.
- Go to the [Client Connector IP Assignment](/zpa/about-client-connector-ip-assignment) page to manage Zscaler virtual IP addresses and view IP bindings for use with server-to-client connectivity.
![Viewing and managing admins within the Administrators page](/downloads/zpa/documentation-knowledgebase/admin-settings/admins-and-roles/about-administrators/zpa-administrators-page_0.png)