# Adding the Zscaler Client Connector as an IdP
Source: https://help.zscaler.com/zia/adding-zscaler-client-connector-portal-idp
PDF: https://help.zscaler.com/pdf/com/en/1401391.pdf

If you configure the Zscaler Client Connector Portal as your identity provider (IdP), users automatically enroll with the Zscaler Client Connector. Zscaler Client Connector uses a device token generated in the Zscaler Client Connector Portal to authenticate users and their devices for the Zscaler service.
When using Zscaler Client Connector as your IdP, you cannot federate user identities with other external IdPs as the users are hosted locally within your tenant.
Prerequisites
To configure the Zscaler Client Connector Portal as your IdP, you must:
- Add the Zscaler Client Connector Portal as an IdP in the ZIA Admin Portal. To learn more, see [Using the Zscaler Client Connector Portal as an Identity Provider](/zscaler-client-connector/using-zscaler-client-connector-portal-identity-provider).
-
Disable SAML auto-provisioning for your existing [IdP](/zia/adding-identity-providers) or change the **User Repository Type** to **Hosted DB** on the [Authentication Profile page](/zia/configuring-default-authentication-profile).
This authentication method only works with Zscaler Client Connector.
To add the Zscaler Client Connector Portal as the IdP in the ZIA Admin Portal:
- Go to **Administration **>** Authentication Settings**.
- Click the **Identity Providers** tab.
-
Click **Add Zscaler Client Connector Portal as IdP**.
[See image.](#add-zscaler-client-connector-portal-idp-button)
The **Add Zscaler Client Connector Portal as IdP** window appears.
-
In the **Add Zscaler Client Connector Portal as IdP** window:
-
**Authentication Domains**: Select **Any** to map all domains to the Zscaler Client Connector Portal or select specific domains. This allows the Zscaler Client Connector Portal to authenticate an incoming user. Any unselected domains are mapped to the default IdP.
Except the default IdP, any additional IdPs must be mapped to at least one domain.
- **Status**: **Enable** or **Disable** the IdP.
- **Enable SAML Auto-Provisioning**: Enable this field to provision users on the Zscaler service.
[See image.](#add-zscaler-client-connector-portal-idp-window)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
![The Add Zscaler Client Connector Portal as IdP button on the Authentication Settings > Identity Provider page.](/downloads/zia/authentication-administration/user-management-authentication-settings/SAML-SCIM/adding-zscaler-client-connector-IdP/ZIA-adding-zscaler-client-connector-IdP-add-button.png)
[]
[]![The Add Zscaler Client Connector Portal as IdP window on the Authentication Settings > Identity Provider page.](/downloads/zia/authentication-administration/user-management-authentication-settings/SAML-SCIM/adding-zscaler-client-connector-IdP/ZIA-adding-zscaler-client-connector-IdP-adding-window.png)