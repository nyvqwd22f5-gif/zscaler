# Configuring Administrator Management Settings
Source: https://help.zscaler.com/zdx/configuring-administrator-management-settings
PDF: https://help.zscaler.com/pdf/com/en/1507761.pdf

On the Administrator Management page (Administration > Administration Controls > Administrator Management > Administrator Management), you can configure password management, SAML authentication, advanced configuration, and SCIM auto provisioning for ZDX admins.
The Administrator Management page allows you to configure the following:
[See image.](#AdministratorManagementPage)
- [Password Management](/zdx/configuring-password-expiration)
- [SAML Authentication for Administrators](/zdx/configuring-saml-zdx-admins)
- [Advanced Configuration](#AdvancedConfiguration)
- [SCIM Auto Provisioning](#SCIM)
[]
Admins can choose the action to be taken against an admin account if the linked admin user account is deleted using the System for Cross-Domain Identity Management (SCIM) protocol. Admins can allow SCIM to delete the admin user and its linked user account, or they can prevent SCIM from deleting the admin user and its linked user account.
To configure advanced configuration for admins:
- Go to the **Advanced Configuration** section.
- Choose one of the following options for the **Admin Account Action When SCIM Deletes Linked User Account** drop-down menu:
- Select **Delete** if you want to allow SCIM to delete the admin user and its linked user account.
- Select **Do Nothing** if you do not want to allow SCIM to delete the admin user and its linked user account. SCIM will return error 409 (Admin user cannot be deleted). Do Nothing is the default.
- Click **Save** and [activate the changes](/zdx/saving-and-activating-changes-admin-portal).
[]
SCIM Auto Provisioning allows Zscaler to automatically create admin groups in the ZDX Admin Portal based on a SCIM user's group information. By enabling this setting, you can manage limitations and access to the ZDX Admin Portal for ZDX admins with admin groups.
To enable SCIM Auto Provisioning for admins:
- Go to the **SCIM Auto Provisioning** section.
- Select to **Enable SCIM Auto Provisioning**.
- Click **Save** and [activate the changes](/zdx/saving-and-activating-changes-admin-portal).
[]
![Administrator Management Page](/downloads/zdx/administration/admin-configuration/configuring-administrator-management-settings/ZDX-AdministratorManagement-SCIMAutoProvisioning.png)