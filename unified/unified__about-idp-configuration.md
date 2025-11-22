# About IdP Configuration
Source: https://help.zscaler.com/unified/about-idp-configuration
PDF: https://help.zscaler.com/pdf/com/en/1490891.pdf

For users to access your applications, they must first authenticate into Zscaler Client Connector using any SAML 2.0-compliant identity provider (IdP) with the service provider-initiated (SP-initiated) model. User SSO is SP-initiated, but admin SSO can be SP-initiated or IdP-initiated. When an admin selects **Single Sign-On Using IdP** on the Admin Portal's Sign In page, the login is SP-initiated. If the admin logs directly into their IdP, it's IdP-initiated.
Prior to configuring your IdP, Zscaler recommends reading [IdP Configuration Best Practices](/unified/idp-configuration-best-practices).
The IdP must be configured to recognize Zscaler as a valid SP, and you must configure the full details for the IdP within the Admin Portal. To learn more, see [Configuring an IdP for Single Sign-On](/unified/configuring-idp-single-sign).
IdP configuration provides the following benefits and enables you to:
- Authenticate and access applications.
- Use SCIM, a standard protocol for automating the exchange of identity information, so that you can provision users and groups.
About the IdP Configuration Page
The IdP Configuration page is read only if you are subscribed to ZIdentity for users. An orange **Info** icon ![Orange Info Icon within the ZPA Admin Portal](/downloads/zpa/authentication/idp-configuration/about-idp-configuration/zpa-orange-info-icon.png)
is displayed next to disabled IdPs that have been migrated to ZIdentity. These IdPs will be deleted 30 days after migration. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
On the IdP Configuration page (Administration > Identity > Private Access > IDP Configuration), you can do the following:
-
[Add a new IdP configuration.](/unified/configuring-idp-single-sign)
The **Add **icon is hidden if you are subscribed to ZIdentity for users. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
- View a list of the names of all IdPs that were configured for your organization. For each IdP configuration, you can see:
-
**Name**: The name of the IdP configuration. An icon shows next to the name of the IdP if the IdP certificate is close to expiring or has expired:
- If the IdP certificate has expired, a red warning icon (![Red warning icon in the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/about-idp-configuration/zpa-red-warning-icon.png)
) is displayed.
- If the IdP certificate has less than 7 days before expiration, a yellow caution icon (![Yellow caution icon in the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/about-idp-configuration/zpa-yellow-caution-icon.png)
) is displayed.
- If the IdP certificate has less than 30 days before expiration, an orange info icon (![Orange info icon in the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/about-idp-configuration/zpa-orange-info-icon.png)
) is displayed.
If the IdP certificate is part of a certificate chain instead of a single certificate, the certificate expiring the earliest is considered to reflect the expiration icons.
- **Status**: The status of the IdP configuration (i.e., enabled, disabled, or resume if the configuration was [paused during set up](/unified/configuring-idp-single-sign#Pause)).
- **IdP Entity ID**: The entity ID URL for the IdP.
- **Single Sign-On**: Indicates whether the IdP is set up for **Admin** or **User** SSO.
You can expand the row to view details regarding the configuration, [import SAML attributes](/unified/about-saml-attributes), or [verify that SSO](/unified/configuring-idp-single-sign) was configured correctly for the IdP.
-
[Edit an existing IdP configuration](/unified/editing-idp-configuration).
IdP configurations that are managed by Zscaler are read only and cannot be edited.
- Delete an IdP configuration.
An IdP cannot be deleted if it is used for [emergency access](/unified/configuring-emergency-access) or managed by Zscaler.
![Viewing the IdP Configuration page](/downloads/unified/administration/private-applications/identity/idp-device-configuration/idp-configuration/about-idp-configuration/unified-idp-configuration-page.png)