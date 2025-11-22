# About Administration Management
Source: https://help.zscaler.com/unified/about-administration-management
PDF: https://help.zscaler.com/pdf/com/en/1490846.pdf

In Admin Management, the super admin for Client Connector can create custom roles and assign them to admins synced from Internet & SaaS, Private Applications, and Digital Experience Monitoring. These roles determine the permission levels that admins have to access and configure settings in the Admin Portal.
Existing admins in Internet & SaaS, Private Applications, and Digital Experience Monitoring are already synced in the Admin Portal. The following table describes how admin permissions migrate from the Admin Portal to the Administration Management feature.
| Admin Status | Access in Admin Portal | Access in Administration Management |
| ------------ | ---------------------- | ----------------------------------- |
| Existing Admin | Write | Super Admin |
| Existing Admin | Read-Only | Read-Only |
| New Client Connector Admin added as a Super Admin for Internet & SaaS/Private Applications/Digital Experience Monitoring | Super Admin | Super Admin |
| New Client Connector Admin added for Internet & SaaS/Private Applications/Digital Experience Monitoring | Non-Super Admin | Read-Only that can be modified by Super Admin |
About the Administration Management Page
On the Administration Management page (Administration > Admin Management > Role Based Access Control > Client Connector > Administrators), you can do the following:
- Display a list of administrators (i.e., admins for Internet & SaaS, Private Applications, and Digital Experience Monitoring).
- View a list of admin roles configured for your organization with the following details:
- **Login Name**: The Internet & SaaS, Private Applications, or Digital Experience Monitoring Admin Portal login ID for the admin.
- **Status**: The admin's account status.
- **Role**: The admin's access level to the Admin Portal.
- View a configured role.
- Go to the [Role Management](/unified/about-role-management-0) page.
![Administrative Management to create custom roles](/downloads/unified/administration/client-connector/admins-users-role-management/about-administration-management/client-connector-admin-management_1.png)