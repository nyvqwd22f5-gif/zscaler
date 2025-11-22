# Configuring Advanced Configuration for Admins
Source: https://help.zscaler.com/business-insights/configuring-advanced-configuration-admins
PDF: https://help.zscaler.com/pdf/com/en/1473151.pdf

Every Business Insights admin has a *user account. *You can configure the action to be taken against the admin accounts when an admin's user account is deleted using SCIM.
Actions on admins through SCIM are reflected in the Business Insights Admin Portal. For example, disabling an admin's user account through SCIM disables both the admin and its linked user account in the Business Insights Admin Portal. Configuring the action for deleted users only affects deleted users, and does not affect disabled users.
If you are subscribed to the ZIdentity service, the Administrator Management page shows a link to the ZIdentity Admin Portal. You can manage your admins from the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
[See image.](#zidentity-administration)
To configure advanced configuration for admins:
- Go to **Administration** > **Administrator Management**.
- Click the **Administrator Management** tab.
- On the **Administrator Management** page, in the **Advanced Configuration** section, choose one of the following options from the **Admin Account** **Action When SCIM Deletes Linked User Account **drop-down menu:
- Select** Delete** if you want to allow SCIM to delete the admin and its linked user account.
- Select** Do Nothing** if you do not want to allow SCIM to delete the admin and its linked user account. SCIM will return error 409 (Admin user cannot be deleted). **Do Nothing** is the default.
[See image.](#advanced-config)
- Click **Save**.
[]![Advanced Configuration](/downloads/business-insights/authentication-administration/configuring-saml-admins-business-insights/Business-Insights-Administrator%20management-page.png)
![Administrator Management page for ZSLogin-enabled tenants](/downloads/business-insights/authentication-administration/configuring-saml-admins-business-insights/Business-Insights-ZIdentity-Administration.png)
[]