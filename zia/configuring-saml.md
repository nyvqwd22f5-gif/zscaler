# Configuring SAML
Source: https://help.zscaler.com/zia/configuring-saml
PDF: https://help.zscaler.com/pdf/com/en/1399676.pdf

You can configure the Zscaler service as the service provider (SP) and use Security Assertion Markup Language (SAML) Single Sign-On (SSO) for provisioning and authenticating users. To learn more about SAML, see [Understanding SAML](/zia/understanding-saml).
Prerequisites
Ensure you do the following before configuring the Zscaler service for SAML:
- Obtain the SAML SSL certificate from your identity provider (IdP). You upload this certificate to the ZIA Admin Portal when you configure the service to use SAML.
- Export the XML metadata from your IdP. You use information from the metadata when you configure the service to use SAML.
- If you are using [PAC files](/zia/how-do-i-use-default-pac-files-forward-traffic-zia) to forward traffic to the Zscaler service, add the redirected URL to the authentication exemption list in the PAC files. Otherwise, the authentication fails. This is due to the browser trying to reach the authentication URL via the Zscaler service and the current user isn't yet authorized to use the service, so the request never passes through the ZIA Public Service Edge.
- If you are transparently forwarding traffic to the Zscaler service, you must exempt the SAML IdP traffic from the [GRE](/zia/configuring-gre-tunnels) or [IPSec](/zia/configuring-ipsec-vpn-tunnel) tunnel. You can do this by adding a route at the gateway router to forward the traffic directly to the internet.
Configuring SAML
To configure SAML:
- [1. Configure the IdP for SAML](#configuretheidp)
- [2. Add the IdP in the ZIA Admin Portal](/zia/adding-identity-providers)
- [3. Configure the Zscaler service as the SP for SAML](#configuresamlzia)
Troubleshooting
If any errors occur, see [Troubleshooting SAML](/zia/saml-troubleshooting-guidelines) to troubleshoot browser settings and SAML error codes.
[]Follow the relevant configuration guides to configure the Zscaler service as the SP for your IdP:
- [Active Directory Federation Services 3.0](/zia/saml-configuration-guide-adfs-3.0)
- [Active Directory Federation Services 2.0](/zia/saml-configuration-guide-adfs-2.0)
- [Microsoft Entra ID (formerly Azure Active Directory)](/zia/saml-scim-configuration-example-microsoft-azure-active-directory)
- [CA Single Sign-On](/zia/saml-configuration-example-siteminder)
- [Google Apps](/zia/saml-configuration-example-google-apps)
- [Okta](/zia/saml-scim-configuration-example-okta)
- [OneLogin](/zia/saml-configuration-example-onelogin)
- [PingFederate](/zia/saml-scim-configuration-guide-pingfederate)
[]To configure the Zscaler service as the SP for SAML:
- Go to **Administration **>** Authentication Settings**.
- Under **Authentication Frequency**,** **choose how often users are required to authenticate to the Zscaler service. To learn more, see [About Authentication Profile](/zia/about-authentication-profile#authentication-frequency). If you select **Custom**, the following field appears:
- **Custom Authentication Frequency (days)**: Specify 1 to 180 days.
-
Under** Authentication Type**, choose **SAML**.
[See image.](#seeimage-2c)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot highlighting the SAML option under Authentication Type on the Authentication Profile page.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/configuring-saml/ZIA-Authentication-Profile-Authentication-Type.png)