# About Identity Proxy Settings
Source: https://help.zscaler.com/unified/about-identity-proxy-settings
PDF: https://help.zscaler.com/pdf/com/en/1491681.pdf

You can view and modify Identity Proxy settings for [cloud apps](/unified/about-cloud-app-control). Enabling Identity Proxy settings for certain cloud apps (i.e., Box, Google Apps, Microsoft Office 365, Salesforce, ServiceNow, Slack, etc.) will allow you to configure the Zscaler Identity Proxy for cloud apps. To learn more, see [Configuring the Zscaler Identity Proxy for Cloud Apps](/unified/configuring-zscaler-identity-proxy-cloud-apps).
About the Identity Proxy Settings Page
On the Identity Proxy Settings page (Administration > Identity > Internet & SaaS > Identity Proxy Settings), you can do the following:
- View a list of all Identity Proxy settings for each cloud app. For each setting, you can see the following:
- **Cloud Applications**: The cloud application for the Identity Proxy setting.
- **Status**: Displays if Zscaler service is enabled as the IdP proxy for the cloud app.
- **Setting**: Displays the following Zscaler IdP settings needed for your configuration.
- **SAML Version**: Displays the SAML version implemented by the Zscaler IdP. You can't modify this field.
- **Identity Proxy URL**: The Zscaler service dynamically generates a unique Identity Proxy URL. You add this URL as the IdP for SAML SSO when you configure SSO for the app. You can't modify this field.
- **Issuer Entity ID**: Displays the random part of the Identity Proxy URL.
- **Identity Request Binding**: Displays the SAML assertion (HTTP-POST) that the Zscaler service, as the IdP, sends the cloud app.
- **User Identifier**: NameID is the LDAP attribute that maps to the login name, which users enter when they authenticate to the Zscaler service.
- **Response Signing SSL Certificate**: Displays the certificate that is used by the Identity Proxy for signing SAML responses.
- **Certificate**: Click to download the Zscaler certificate for the cloud app that you are configuring an Identity Proxy for.
- [Add and configure Identity Proxy setting for cloud apps.](/unified/configuring-zscaler-identity-proxy-cloud-apps)
- Edit the Identity Proxy setting for a cloud app.
- Modify the table and its columns.
- Search for an Identity Proxy setting.
![Screenshot of highlighting the features on the Identity Proxy Settings.](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/configuring-zscaler-identity-proxy-cloud-apps/zia-identity-proxy-settings.png)