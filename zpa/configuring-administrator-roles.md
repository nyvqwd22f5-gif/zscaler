# Configuring Administrator Roles
Source: https://help.zscaler.com/zpa/configuring-administrator-roles
PDF: https://help.zscaler.com/pdf/com/en/1484001.pdf

This article describes how to add a new admin role. For a complete list of ranges and limits for roles, see [Ranges & Limitations](/zpa/ranges-limitations).
Currently, the following conditions apply when configuring role-based access control:
- If an admin does not have permission to access a page within the ZPA Admin Portal, it is still listed within the left-side navigation menu but it is not accessible. If an admin has **Read Only** access, they can still attempt to add or edit but an error message is displayed when they try to save.
- For ZIdentity-enabled tenants, admin roles must be assigned in the ZIdentity Admin Portal. To learn more, see [About Administrative Entitlements](/zslogin/about-administrative-entitlements).
- Only** **access to [Zscaler Client Connector](/zpa/getting-started/introduction-zpa-admin-portal#mobileadmin) is supported.
- [Submit a Ticket](/zpa/getting-started/introduction-zpa-admin-portal#help) is always accessible to all roles.
Adding an Admin Role
[]To add a new admin role:
- Go to **Configuration & Control **> **Administration Control** > **Roles**.
-
Click **Add**.
The **Add Role** drawer appears.
[See image.](#AddRole1)
-
In the **Add Role** drawer:
- **Name**: Enter a name for the role. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description for the role.
- Under **Access** **Control**, click **Enable** for the features that this role must have access to. If the role does not have access to a feature, then the functionality for the feature does not appear in the ZPA Admin Portal for any admin assigned to this role. You can only create a role that has an equal or lower level of access control than your own.
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
- [VPN (For Legacy Apps)](#vpnConfig)
A user is always granted the highest level of access control as defined for their role. For example, if a user is assigned a role that permits **Full** access to **Configuration - Policy** and **Read Only** access to **Policies - Policy**, then **Full** access is granted to the user for **Policies**.
You can click on each section to expand it, or click **Expand All**.
The default selections under each enabled feature are recommended by Zscaler. If you make changes, click **Reset** within a section to revert it to the default. You can also click **Reset All** at the top of the **Access Control** area to revert all sections to their defaults.
[See image.](#ResetToRecommended)
- Click **Save**.
Editing an Admin Role
[]To edit an admin role:
- Go to **Configuration & Control **>** Administration Control **> **Roles**.
-
In the table, locate the role you want to modify and click the **Edit **icon.
The **Edit Role **drawer appears.
- In the** Edit Role **drawer, modify fields as necessary.
[See image.](#EditRole1)
- Click **Save**.
It can take up to two minutes for updates to the permissions for existing roles to take effect. If the permissions for a custom role are missing, you must edit the custom role and save the new permissions. A warning icon appears next to the permission group that indicates when permissions are missing. When you expand the group, a warning icon also appears next to the missing permissions.
[See image.](#permissionError)
Deleting an Admin Role
To delete an admin role:
- Go to **Configuration & Control **>** Administration Control **> **Roles**.
- In the table, locate the role you want to remove and click the **Delete** icon.
- In the confirmation window that appears, click **Delete**.
[]![Adding a custom admin role ](/downloads/zpa/documentation-knowledgebase/admin-settings/admins-and-roles/configuring-administrator-roles/zpa-add-role-drawer.png)
[]![Editing a custom admin role](/downloads/zpa/documentation-knowledgebase/admin-settings/admins-and-roles/configuring-administrator-roles/zpa-edit-role-drawer.png)
[]Enable to allow admins **Read Only** access to the **Dashboard**.
[]Enable to allow admins **Full **or **Read Only** access to the following **Diagnostics** functionality:
- Analytics** **>** Diagnostics**
- Analytics > **Support Information**
- Analytics >** Live Logs**
[]Enable to allow admins **Full** or **Read Only** access to the following **Cloud Connector Management** functionality:
-
Configuration & Control > Certificate Management > **Certificates**
This includes access to both Certificates (Configuration & Control > Certificate Management > Certificates and Configuration) and Enrollment Certificates (Control > Certificate Management > Enrollment Certificates).
- Configuration & Control > Private Infrastructure > Cloud Connector Management > **Cloud Connector**
- Configuration & Control > Private Infrastructure > Cloud Connector Management > **Cloud Connector Group**
[]Enable to allow admins **Full** or **Read Only** access to the following **Configuration** functionality:
- Resource Management > Application Management > **Application Segments**
- Configuration & Control > Private Infrastructure > App Connector Management > **App Connector Groups**
-
Configuration & Control > Certificate Management > **Certificates**
This includes access to both Certificates (Configuration & Control > Certificate Management > Certificates and Configuration) and Enrollment Certificates (Control > Certificate Management > Enrollment Certificates).
- Resource Management > Application Management > Application Segments > **Client Hostname Validation**
- Configuration & Control > Certificate Management > **Enrollment Certificates**
- Resource Management > Application Management > Application Segments/Segment Groups > **DNS Search Domains**
- Authentication > Device authentication > **Machine Group**
- Policies. This includes access to** Access Policy** and **Timeout Policy**
- Authentication > User Authentication > SAML Management > **SAML Attributes**
- Resource Management > Application Management > **Segment Groups**
- Configuration & Control > Private Infrastructure > App Connector Management > **Server Groups**
- Configuration & Control > Private Infrastructure > App Connector Management > **Servers**
- Configuration & Control > Private Infrastructure > Private Service Edge Management > **Private Service Edge Group**
[]Enable to allow admins **Full** or **Read Only** access to the following **Policy Management** functionality:
- Configuration & Control > Private Infrastructure > App Connector Management > **App Connector Groups**
- Configuration & Control > AppProtection >** AppProtection Profiles**
- Resource Management > Application Management > **Application Segments**
- Configuration & Control > Private Infrastructure > Branch Connector Management >** Branch Connector Groups**
- Configuration & Control > Private Infrastructure > Branch Connector Management >** Branch Connectors**
- Policy > Security Policy > Browser Protection >** Browser Protection Profile Config**
- Configuration & Control > Private Infrastructure > Cloud Connector Management > **Cloud Connector Group**
- Authentication > User Authentication > **IdP Configuration**
- Authentication > Device authentication > **Machine Groups**
-
Policies
This includes access to Access Policy (Policy > Access Policy), Client Forwarding Policy (Policy > Client Forwarding Policy), and Timeout Policy (Policy > Timeout Policy).
- Configuration & Control > Private Infrastructure > Private Service Edge Management > **Private Service Edge Group**
- Authentication > User Authentication >** SAML Attributes**
- Authentication > User Authentication > SCIM Management > **SCIM Attributes**
- Authentication > User Authentication > SCIM Management > **SCIM Groups**
- Authentication > User Authentication > SCIM Management > **SCIM Users**
- Resource Management > Application Management > **Segment Groups**
- Configuration & Control > Private Infrastructure > Application Management > **Server Groups**
[]Enable to allow admins **Full** or **Read Only** access to **API Keys**.
[]Enable to allow admins **Full** or **Read Only** access to the following **Authentication** functionality:
- Authentication > User Authentication > Settings > **CORS and SameSite**
- Authentication > User Authentication > **Emergency Access**
- Authentication > User Authentication > **Emergency Access Users**
-
[]Authentication > User Authentication > **IdP Configuration**
This includes access to Enforce SSO Login for Administrators on the Settings page (Authentication > User Authentication > Settings > Enforce SSO Login for Administrators) and SAML and SCIM authentication. To learn more about SCIM authentication settings, see [SCIM Management](#scimManagement).
- Tools > **Remote Assistance**
- Authentication > User Authentication > SAML Management > **SAML Attributes**
- Authentication > User Authentication > Settings > **Settings**
[]Enable to allow admins **Full **or **Read Only** access to **Business Continuity Management **functionality:
- Administration Control > Business Continuity >** Business Continuity Settings**
-
Administration Control > Certificate Management > **Certificates**
This includes access to both Certificates (Configuration & Control > Certificate Management > Certificates and Configuration) and Enrollment Certificates (Control > Certificate Management > Enrollment Certificates).
- Administration Control > Business Continuity > Private Cloud Controllers > **Customer Version Profile**
- Administration Control > Business Continuity > **Private Cloud Controller Groups**
- Administration Control > Business Continuity > **Private Cloud Controller Provisioning Keys**
- Administration Control > Business Continuity > **Private Cloud Controllers**
- Administration Control > Business Continuity > **Private Clouds**
[]Enable to allow admins **Full** or **Read Only** access to **Client Sessions**.
[]Enable to allow admins **Full** or **Read Only** access to the following **App Connector Management** functionality:
- Configuration & Control > Private Infrastructure > App Connector Management > **App Connector Groups**
- Configuration & Control > Private Infrastructure > App Connector Management > **App Connector Provisioning Keys**
- Configuration & Control > Private Infrastructure > App Connector Management > **App Connectors**
-
Configuration & Control > Certificate Management > **Certificates**
This includes access to both Certificates (Configuration & Control > Certificate Management > Certificates and Configuration) and Enrollment Certificates (Control > Certificate Management > Enrollment Certificates).
- Configuration & Control > Private Infrastructure > App Connector Management > App Connector Groups > **Customer Version Profile**
[]Enable to allow admins **Full** or **Read Only** access to the following **Security Management **functionality:
- Configuration & Control > AppProtection > **AppProtection Controls**
- Configuration & Control > AppProtection > **AppProtection Profiles**
- Configuration & Control > AppProtection > AppProtection Controls >** ThreatLabZ Controls**
[]Enable to allow admins **Full** or **Read Only** access to the following **Log Streaming** functionality:
- Resource Management > Application Management > **Application Segments**
- Administration Control > Private Infrastructure > Log Streaming Service > **App Connector Groups**
- Configuration & Control > Private Infrastructure > Log Streaming Service > **Log Receivers**
- Authentication > User Authentication > SAML Management > **SAML Attributes**
- Resource Management > Application Management > **Segment Groups**
[]Enable to allow admins **Full** or **Read Only** access to the following **Machine Management** functionality:
-
Configuration & Control > Certificate Management > **Enrollment Certificates**
This includes access to both Certificates (Configuration & Control > Certificate Management > Certificates and Configuration) and Enrollment Certificates (Control > Certificate Management > Enrollment Certificates).
- Authentication > Device authentication > **Machine Groups**
- Authentication > Device authentication > **Machine Provisioning Keys**
[]Enable to allow **Full** or **Read Only **access to the following **Notification** **Management** functionality:
- Configuration & Control > Administration Control > **Administrators**
- Configuration & Control > Private Infrastructure > App Connector Management > **App Connectors**
- Configuration & Control > Private Infrastructure > Cloud Connector Management > **Cloud Connectors**
- Analytics > Diagnostics > **Events**
- Configuration & Control > Notifications > **Notifications**
- Configuration & Control > Private Infrastructure > Private Service Edge Management > **Private Service Edges**
[]Enable to allow admins **Full** or **Read Only** access to the following **Administration** functionality:
- Configuration & Control > Administration Control > **Administrators**
- Configuration & Control > Administration Control > **Audit Logs**
- Configuration & Control > Administration Control > **Client Connector IP Assignment**
- Configuration & Control > Administration Control > **Disaster Recovery**
- Configuration & Control > Administration Control > **Microtenant**
-
Configuration & Control > Administration Control > **Roles**
Access to **Roles** is always **Read Only**.
- Configuration & Control > Administration Control > **User Portal AUP**
- Configuration & Control > Administration Control > Integrations > **Zscaler Cloud Sandbox**
[]Enable to allow admins **Full** or **Read Only** access to the **Company **profile.
[]Enable to allow admins **Full** or **Read Only** access to **Certificates**.
This includes access to both Certificates (Configuration & Control > Certificate Management > Certificates and Configuration) and Enrollment Certificates (Control > Certificate Management > Enrollment Certificates).
[]Enable to allow admins **Full** or **Read Only** access to following **SCIM Management **functionality.
-
[]Authentication > User Authentication > **IdP Configuration**
This includes access to Authentication > User Authentication > Settings > Enforce SSO Login for Administrators, and provides access for SAML and SCIM authentication. To learn more about SAML authentication settings, see [Authentication](#samlAuthentication).
- Authentication > User Authentication > SCIM Management > **SCIM Attributes**
- Authentication > User Authentication > SCIM Management > **SCIM Groups**
- Authentication > User Authentication > SCIM Management > **SCIM Users**
[]Enable to allow admins **Full** or **Read Only** access to the following **Private Service Edge Management** functionality:
-
Administration Control > Certificate Management > **Certificates**
This includes access to both Certificates (Configuration & Control > Certificate Management > Certificates and Configuration) and Enrollment Certificates (Control > Certificate Management > Enrollment Certificates).
- Configuration & Control > Private Infrastructure > Private Service Edge Management > **Private Service Edge Groups**
- Configuration & Control > Private Infrastructure > Private Service Edge Management > **Private Service Edge Provisioning Keys**
- Configuration & Control > Private Infrastructure > Private Service Edge Management > **Private Service Edges**
[]Enable to allow admins **Full** access to **Zscaler Client Connector Portal**.
[]Enable to allow admins **Full **or **Read Only** access to the following **Privileged Remote Access** functionality:
- Resource Management > Application Management > **Application Segments**
-
Configuration & Control > Certificate Management > **Certificates**
This includes access to both Certificates (Configuration & Control > Certificate Management > Certificates and Configuration) and Enrollment Certificates (Control > Certificate Management > Enrollment Certificates).
- Resource Management > Privileged Remote Access >** Privileged Approval**
- Resource Management > Privileged Remote Access > **Privileged Consoles**
- Resource Management > Privileged Remote Access > **Privileged Credential**
- Resource Management > Privileged Remote Access >** Privileged Credential Pool**
- Resource Management > Privileged Remote Access > **Privileged Portal**
[]Enable to allow admins **Full** or **Read Only** access to the following **Privileged Sessions** functionality:
- Resource Management > Privileged Sessions > **Session Proctoring**
- Resource Management > Privileged Sessions > **Session Recordings**
[]Enable to allow **Full **or **Read Only** access to the following VPN Configuration functionality:
-
Configuration & Control > Certificate Management > **Certificates**
This includes access to both Certificates (Configuration & Control > Certificate Management > Certificates and Configuration) and Enrollment Certificates (Control > Certificate Management > Enrollment Certificates).
- VPN (For Legacy Apps) > Network Connectors > VPN Connector Groups > **Customer Version Profiles**
- VPN (For Legacy Apps) > Network Connectors > **Network Connector Groups**
- VPN (For Legacy Apps)> Network Connectors > **Network Connector Provisioning Keys**
- VPN (For Legacy Apps) > Network Connectors > **Network Connectors**
- VPN (For Legacy Apps) > **Network Segments**
- VPN (For Legacy Apps) > VPN Service Edges > **VPN Connected Users**
- VPN (For Legacy Apps) > Network Connectors >** External Routers**
- VPN (For Legacy Apps) > Diagnostics > Support Information > **VPN Support Information**
- VPN (For Legacy Apps) > VPN Service Edges > **VPN Service Edges**
[]![Reverting changes back to the Zscaler recommended settings ](/downloads/zpa/documentation-knowledgebase/admin-settings/admins-and-roles/configuring-administrator-roles/zpa-add-roles-drawer-reset.png)
[]![Viewing an error next to the permission group](/downloads/zpa/documentation-knowledgebase/admin-settings/admins-and-roles/configuring-administrator-roles/zpa-edit-role-drawer-permission-error.png)