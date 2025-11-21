# About Identity Providers
Source: https://help.zscaler.com/zia/about-identity-providers
PDF: https://help.zscaler.com/pdf/com/en/1401376.pdf

When configuring [SAML single sign-on](/zia/configuring-saml) and [SCIM provisioning](/zia/configuring-scim) for users, you can configure multiple identity providers (IdPs) based on your organization's requirements. The Zscaler service redirects users to different SAML URLs based on configured IdP criteria. The service can support up to 64 different SAML IdPs per organization. You can manage and view general information about your configured IdPs on the Identity Providers page.
Configuring the IdP Criteria
When [adding an IdP](/zia/adding-identity-providers), the only required criteria for the IdP configuration is the user authentication domains. You must assign at least one authentication domain to a non-default IdP; otherwise, you can't enable it. This restriction doesn't apply to the default IdP. The default IdP is automatically assigned to all domains that aren't associated with an IdP. If a new user attempts to authenticate, the Zscaler service checks the user's domain, and then redirects the user to the appropriate IdP for authentication.
Optionally, you can assign known locations to an IdP. This allows you to map IdPs to specific office locations in your organization. For example, you can assign all locations in Europe to a European AD FS server, but then assign all US locations to a US AD FS server. Any locations that aren't assigned to a specific IdP are automatically mapped to the default IdP.
The following diagram illustrates how the Zscaler service decides which IdP to use based on the user's connection method:
![Flow chart illustrating how the Zscaler service decides which IdP to use based on the unauthenticated user's connection method.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/about-identity-providers/ZIA-Zscaler-IdP-Criteria-Process.png)
About the Default IdP
You can set only one IdP as your organization's default IdP. The default IdP serves as the catchall IdP if you haven't mapped a location or domain to an IdP. For example, you can assign a location or domain to any configured IdP. However, if a location or domain isn't assigned to a specific IdP, it's automatically assigned to the default one. This ensures that there is at least one IdP responsible for authenticating all users in your organization.
The following diagram illustrates how the Zscaler service handles user authentication if you've configured multiple IdPs:
![Flow chart illustrating how the Zscaler service handles user authentication if there are multiple IdPs configured.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/about-identity-providers/ZIA-Zscaler-Multiple-IdP-Process.png?1597100760)
Identity Providers provide the following benefits and enable you to:
- Configure IdPs to authenticate your users.
- Provide a quick and simple way for admins to assign multiple users to an IdP.
The Identity Providers page is not available if you're subscribed to the ZIdentity service. The IdPs can be configured in the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
About the Identity Providers Page
On the Identity Providers page (Administration > Authentication Settings > Identity Providers), you can do the following:
- [Add an IdP](/zia/adding-identity-providers).
- [Add the Zscaler Client Connector Portal as the IdP](/zia/adding-zscaler-app-portal-idp).
- View a list of all configured IdPs. For each IdP, you can see the following information:
- **ID**: The ID or identifier of the IdP.
- **Name**: The name of the IdP.
- **Status**: Displays if the IdP is enabled or disabled.
- **Location**: The locations mapped to the IdP.
- **IdP SSL Certificate Expiration Date**: The expiration date of the IdP SSL certificate.
- **Authentication Domains**: The domains mapped to the IdP.
- **Default IdP**: Displays whether or not the IdP is the default one. Click to make this IdP the default one.
When an IdP is set as the default, all locations and domains are mapped to it. If you have multiple IdPs configured, the default IdP becomes the catchall IdP, so any location or domain that isn't specifically assigned to an IdP gets mapped to the default one. Also, if you set an existing IdP as the default, the Zscaler service removes any specific location or domain mappings associated with that IdP.
You can't delete the default IdP. You must set another existing IdP as the default.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- [Edit a configured IdP](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- Save your changes if you modify the default IdP.
- Go to the [Default Settings page](/zia/about-authentication-default-settings).
- Go to the [Authentication Bridges page](/zia/about-zscaler-authentication-bridge).
![Image of the Identity Providers page](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/about-identity-providers/ZIA-about-IdPs.png)