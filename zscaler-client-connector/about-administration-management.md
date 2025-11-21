# About Administration Management
Source: https://help.zscaler.com/zscaler-client-connector/about-administration-management
PDF: https://help.zscaler.com/pdf/com/en/1402661.pdf

In Administration Management, the super admin can create custom roles and assign them to admins synced from Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA) and Zscaler Digital Experience (ZDX). These roles determine the permission levels that admins have to access and configure settings in the Zscaler Client Connector Portal.
Administration management provides the following benefits and enables you to:
- View all of the admin roles configured for your organization in one place.
- Update the admin access permissions for admins synced from ZIA, ZPA, and ZDX.
Existing admins in ZIA, ZPA, and ZDX are already synced in the Zscaler Client Connector Portal. The following table describes how admin permissions migrate from the Zscaler Client Connector Portal to the Administration Management feature.
| Admin Status | Access in Zscaler Client Connector Portal | Access in Administration Management |
| ------------ | ----------------------------------------- | ----------------------------------- |
| Existing Admin | Write | Super Admin |
| Existing Admin | Read-Only | Read-Only |
| New Admin added as a Super Admin in ZIA/ZPA/ZDX | Super Admin | Super Admin |
| New Admin added in ZIA/ZPA/ZDX | Non-Super Admin | Read-Only that can be modified by Super Admin |
About the Administration Management Page
If you are subscribed to ZIdentity, the Administration tab is not available. You can configure and manage admins in the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity](/zidentity/what-zidentity)?
On the Administration Management page (Administration > Administration Management), you can do the following:
- Display a list of ZIA administrators.
- Display a list of ZPA administrators.
- Display a list of ZDX administrators.
- Manually sync ZIA Admins, ZPA Admins, or** **ZDX Admins.
- View a list of admin roles configured for your organization with the following details:
- **Login Name**: The ZIA, ZPA, or ZDX Admin Portal login ID for the admin.
- **Status**: The admin's account status.
- **Role**: The admin's access level to the ZIA, ZPA, or ZDX Admin Portal.
- View a configured role.
- [Edit](/zscaler-client-connector/assigning-administrator-custom-role) a role.
- Go to the [Role Management](/zscaler-client-connector/about-role-management) page to create and assign roles.
![Administrative Management to create custom roles for access to Zscaler Client Connector settings](/downloads/zscaler-client-connector/administration/about-administration-management/zscaler-client-connector-admin-mgmt.png)