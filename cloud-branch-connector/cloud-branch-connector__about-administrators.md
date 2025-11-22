# About Administrators
Source: https://help.zscaler.com/cloud-branch-connector/about-administrators
PDF: https://help.zscaler.com/pdf/com/en/1420586.pdf

Zscaler's role-based administration enables you to control what different admins can do in the Zscaler Cloud & Branch Connector Admin Portal.
Role-based administrators provide the following benefits and enable you to:
- View and navigate your organization's admins.
- Delegate responsibilities to your organization's admins.
- Granularly control access to the portal to ensure that policies and settings do not conflict.
To facilitate role-based administration, each admin account comprises a role and scope:
- An admin role or partner admin role allows you to specify which features admins can access in the portal.
- An admin scope allows you to specify the areas of the organization (e.g., departments or locations) for which admins can configure policies or settings in the portal.
You can configure role-based administration using role and scope. For example, you can give your organization's CISO the ability to set only security policies in the Cloud & Branch Connector Admin Portal (specified through role), but enable the CISO to set security policies for the entire organization (specified through scope). Similarly, you could give the Marketing Director the ability to set access policies relevant to productivity and compliance (specified through role), but allow them to do so only for a specific location or department (specified through scope).
Zscaler provides a default admin account that has full access to the Cloud & Branch Connector Admin Portal and scope over the entire organization. You cannot edit or delete this account. With role-based administration, you can add as many additional admins as necessary to meet the specific needs of your organization. You can also edit and delete admins as necessary at any time.
About the Administrators Page
If you are subscribed to ZIdentity, certain options are unavailable on the Administrators page, but you can configure them in the ZIdentity Admin Portal. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
On the Administrators page (Administration > Administrator Management), you can do the following:
- [Add an admin](/cloud-branch-connector/adding-admins).
- View a list of all admins configured for your organization. For each admin, you can see:
- **Login ID**: The portal login ID for the admin.
- **Name**: The name of the admin.
- **Role**: The admin's level of access to the portal.
- **Scope**: The areas of the organization the admin can manage in the portal.
- **Login Type**: Lists if SAML single sign-on (SSO) login, direct password access login, or both are enabled for the admin.
- **Type**: Displays the type of admin role, such as Cloud Connector Admin.
- **Comments**: Displays any comments regarding the admin, if available.
- **Password Expired**: If password expiration is enabled for admins, displays whether the admin's password has expired.
- **Status**: Enable or disable the admin. If you disable the admin, the password is automatically reset. If you re-enable the status of the disabled admin, you must set a password again. If SAML is enabled, then setting this password is optional. You can save your changes only after the admin authentication is complete.
- [Edit an admin](/cloud-branch-connector/editing-deleting-or-duplicating-items).
- [Delete an admin](/cloud-branch-connector/editing-deleting-or-duplicating-items).
- Modify the table and its columns.
- Search for a configured admin.
- Go to the** **[Administrators Management](/cloud-branch-connector/accessing-administrator-management)** **page.
![The Administrators page in the Zscaler Cloud & Branch Connector Admin Portal ](/downloads/cloud-connector/administration/administrator-role-management/about-administrators/About%20Administrators.jpg)