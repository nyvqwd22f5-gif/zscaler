# Configuring Administrator Roles
Source: https://help.zscaler.com/unified/configuring-administrator-roles
PDF: https://help.zscaler.com/pdf/com/en/1491586.pdf

This article describes how to add a new admin role. For a complete list of ranges and limits for roles, see [Ranges & Limitations](/unified/ranges-limitations).
Currently, the following conditions apply when configuring role-based access control:
- If an admin does not have permission to access a page within the Admin Portal, it is still listed within the left-side navigation menu but it is not accessible. If an admin has **Read Only** access, they can still attempt to add or edit, but an error message is displayed when they try to save.
- For ZIdentity-enabled tenants, admin roles must be assigned properly. To learn more, see [About Administrative Assignments](/unified/about-zscaler-service-entitlement).
- Submit a Ticket is always accessible to all roles.
Adding an Admin Role
[]To add a new admin role:
- Go to the **Roles** page (Administration > Admin Management > Role Based Access Control > Private Access).
-
Click **Add Role**.
The **Add Role** window appears.
[See image.](#AddRole1)
-
In the **Add Role** window:
- **Name**: Enter a name for the role. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description for the role.
- Under **Access** **Control**, click **Enable** for the features that this role must have access to. If the role does not have access to a feature, then the functionality for the feature does not appear in the Admin Portal for any admin assigned to this role. You can only create a role that has an equal or lower level of access control than your own.
Choose from the following features:
- [Administration Control](#Administration)
- [API Key Management](#APIkey)
- [App Connector Management](#ConnectorMgmt)
- [Authentication](#Authentication)
- [Business Continuity Management](#businessContinuity)
- [Certificate Management](#CertificateMgmt)
- [Client Connector Portal](#ZAppPortal)
- [Client Sessions](#ClientSessions)
- [Cloud Connector Management](#CloudConnectorMgmt)
- [Company Information](#Company)
- [Configuration](#Configuration)
- [Dashboard](#Dashboard)
- [Diagnostics](#Diagnostics)
- [Log Streaming](#LSS)
- [Machine Management](#Machine)
- [Notification Management](#Notification)
- [Policies](#Policies)
- [Private Service Edge Management](#svcedge)
- [Privileged Remote Access](#prililegedRemoteAccess)
- [Privileged Sessions](#recordings)
- [Security Management](#inspect)
- [SCIM Management](#scim)
A user is always granted the highest level of access control as defined for their role. For example, if a user is assigned a role that permits **Full** access to **Configuration - Policy** and **Read Only** access to **Policies - Policy**, then **Full** access is granted to the user for **Policies**.
You can click on each section to expand it, or click **Expand All**.
[See image.](#AddRole2)
The default selections under each enabled feature are recommended by Zscaler. If you make changes, click **Reset to recommended settings** within a section to revert it to the default. You can also click **Reset to recommended settings** at the top of the **Access Control** area to revert all sections to their defaults.
[See image.](#ResetToRecommended)
- Click **Save**.
Editing an Admin Role
[]To edit an admin role:
- Go to the **Roles** page (Administration > Admin Management > Role Based Access Control > Private Access).
- In the table, locate the role you want to modify and click the **Edit **icon.
- In the** Edit Role **window, modify fields as necessary.
[See image.](#EditRole1)
- Click **Save**.
It can take up to two minutes for updates to the permissions for existing roles to take effect. If the permissions for a custom role are missing, you must edit the custom role and save the new permissions. A warning icon appears next to the permission group that indicates when permissions are missing. When you expand the group, a warning icon also appears next to the missing permissions.
[See image.](#permissionError)
Deleting an Admin Role
To delete an admin role:
- Go to the **Roles** page (Administration > Admin Management > Role Based Access Control > Private Access).
- In the table, locate the role you want to remove and click the **Delete** icon.
- In the confirmation window that appears, click **Delete**.
[]![Adding a custom admin role within the ZPA Admin Portal](/downloads/unified/administration/private-applications/admin-user-role-management/admins-and-roles/configuring-administrator-roles/add-role-window.png)
[]![Enabling and disabling access control settings for a custom admin role](/downloads/unified/administration/private-applications/admin-user-role-management/admins-and-roles/configuring-administrator-roles/add-roles-expand-all-view.png)
[]![Editing a custom admin role within the ZPA Admin Portal](/downloads/unified/administration/private-applications/admin-user-role-management/admins-and-roles/configuring-administrator-roles/edit-role-window.png)
[]Enable to allow admins **Read Only** access to the **Dashboard**.
[]Enable to allow admins **Full **or **Read Only** access to the following **Diagnostics** functionality:
- Diagnostics
- Support Information
- Live Logs
[]Enable to allow admins **Full** or **Read Only** access to the following **Cloud Connector Management** functionality:
- Certificates
- Cloud Connector
- Cloud Connector Group
[]Enable to allow admins **Full** or **Read Only** access to the following **Configuration** functionality:
- Application Segments
- App Connector Groups
- Certificates
- Client Hostname Validation
- Enrollment Certificates
- DNS Search Domains
- Machine Group
- Policies. This includes access to Access Policy and Timeout Policy
- SAML Attributes
- Segment Groups
- Server Groups
- Servers
- Private Service Edge Group
[]Enable to allow admins **Full** or **Read Only** access to the following **Policies** functionality:
- App Connector Groups
- AppProtection Profiles
- Application Segments
- Cloud Connector Group
- IdP Configuration
- Machine Groups
- Segment Groups
- Server Groups
- SAML Attributes
- SCIM Attributes
- SCIM Groups
- SCIM Users
- Policies
This includes access to **Access Policy**,** Client Forwarding Policy**, and** Timeout Policy.**
[]Enable to allow admins **Full** or **Read Only** access to **API Keys**.
[]Enable to allow admins **Full** or **Read Only** access to the following **Authentication** functionality:
- CORS Request
- SameSite Cookie Attribute
- Emergency Access
- Emergency Access Users
-
IdP Configuration. This includes access to Enforce SSO Login for Administrators.
The IdP Configuration field provides access for SAML and SCIM authentication. To learn more about SCIM authentication settings, see SCIM Management.
- Remote Assistance
- SAML Attributes
- Settings
[]Enable to allow admins **Full **or **Read Only** access to the following **Business Continuity Management** functionality:
- Business Continuity Settings
- Certificates
- Customer Version Profile
- Private Cloud Controller Groups
- Private Cloud Controller Provisioning Keys
- Private Cloud Controllers
- Private Clouds
[]Enable to allow admins **Full** or **Read Only** access to **Client Sessions**.
[]Enable to allow admins **Full** or **Read Only** access to the following **App Connector Management** functionality:
- Certificates
- Enrollment Certificates
- App Connector Groups
- App Connector Provisioning Keys
- App Connectors
[]Enable to allow admins **Full** or **Read Only** access to the following **Security Management **functionality:
- AppProtection Controls
- AppProtection Profiles
- ThreatLabZ Controls
[]Enable to allow admins **Full** or **Read Only** access to the following **Log Streaming** functionality:
- Application Segments
- App Connector Groups
- Log Receivers
- SAML Attributes
- Segment Groups
[]Enable to allow admins **Full** or **Read Only** access to the following **Machine Management** functionality:
- Enrollment Certificates
- Machine Groups
- Machine Provisioning Keys
[]Enable to allow **Full** or **Read Only **access to the following **Notification** **Management** functionality:
- Administrators
- App Connectors
- Cloud Connectors
- Events
- Notifications
- Private Service Edges
[]Enable to allow admins **Full** or **Read Only** access to the following **Administration** functionality:
- Administrators
- Audit Logs
- Client Connector IP Assignment
- Disaster Recovery
- Microtenant
- Roles. Access to Roles is always Read Only.
- User Portal AUP
- Zscaler Cloud Sandbox
[]Enable to allow admins **Full** or **Read Only** access to the **Company **profile.
[]Enable to allow admins **Full** or **Read Only** access to **Certificates**.
[]Enable to allow admins **Full** or **Read Only** access to following **SCIM Management **functionality.
-
IdP Configuration. This includes access to Enforce SSO Login for Administrators.
This IdP Configuration field provides access for SAML and SCIM authentication. To learn more about SAML authentication settings, see Authentication.
- SCIM Attributes
- SCIM Groups
- SCIM Users
[]Enable to allow admins **Full** or **Read Only** access to the following **Private Service Edge Management** functionality:
- Access Certificates
- Enrollment Certificates
- Private Service Edge Groups
- Private Service Edge Provisioning Keys
- Private Service Edges
[]Enable to allow admins **Full** access to **Zscaler Client Connector** features in the Admin Portal.
[]Enable to allow admins **Full **or **Read Only** access to the following **Privileged Remote Access** functionality:
- Application Segments
- Certificates
- Credentials
- Privileged Approval
- Privileged Console
- Privileged Portal
[]Enable to allow admins **Full** or **Read Only** access to the following **Privileged Sessions** functionality:
- Session Proctoring
- Session Recordings
[]![Reverting changes back to the Zscaler recommended settings within the ZPA Admin Portal](/downloads/unified/administration/private-applications/admin-user-role-management/admins-and-roles/configuring-administrator-roles/add-role-reset-recommended-settings.png)
[]![Viewing the permission error next to the role in the Edit Role window](/downloads/unified/administration/private-applications/admin-user-role-management/admins-and-roles/configuring-administrator-roles/edit-role-save-permissions.png)