# Adding Identity Providers
Source: https://help.zscaler.com/dspm/adding-identity-providers
PDF: https://help.zscaler.com/pdf/com/en/1478146.pdf

Adding an identity provider (IdP) in DSPM is one of the tasks you must complete when configuring SAML single sign-on (SSO). When you set up the IdP configuration, all the users in a particular tenant of your organization can log in using SSO.
You can add only one IdP configuration for one tenant. After you've configured one IdP, the option to add an IdP configuration is not visible on the Single Sign-On page.
Prerequisites
Make sure the following prerequisites are met:
- Have admin privileges to add or manage IdP configurations.
- Configure SAML for SSO for your organization:
- [Configure Okta as an IdP](/dspm/configuring-okta-idp)
- [Configure PingOne as an IdP](/dspm/configuring-pingone-idp)
Adding an IdP Configuration
To add an IdP configuration:
- Go to **Administration** > **Authentication & Authorization** > **Single Sign-On**.
-
Click **Add IdP Configuration**.
[See image.](#zpc-addidp)
-
In the **Add IdP Configuration** window:
- **Name**: Enter a unique name for the IdP.
- **Identity Provider Issuer**: Enter the unique value of the IdP that you obtained while configuring SAML:
- **Okta**: Enter the **Issuer** URL after [configuring Okta as an IdP](/dspm/configuring-okta-idp).
- **PingOne**: Enter the **Issuer ID** after [configuring PingOne as an IdP](/dspm/configuring-pingone-idp).
- **Single Sign-On URL**: Enter the SSO URL of the SAML portal to which users are sent for authentication. This information is obtained after configuring SAML.
-
**Single Sign-On**: By default, SSO is enabled for all users in the specified tenant.
When SSO is enabled, all users belonging to the specified tenant can log in only through SSO and they cannot log in using the local authentication method, as this option is disabled. When SSO is disabled, then all users receive an email to reset their password and log in through the local authentication method.
- **IdP Certificate**: Upload the IdP certificate that is used to verify the digital signature of the IdP. This is the certificate you downloaded from your IdP.
- **XML Metadata**: Click to download the XML Metadata that you need for configuring SAML.
- **Enable JIT**: Select to enable just-in-time (JIT) provisioning and allow DSPM to automatically retrieve user information from the IdP and provision users in DSPM.
- JIT works only when you log in via an IDP-initiated SSO.
- If you enable JIT provisioning, then make sure to first [create a group](/dspm/adding-group) in the DSPM Admin Portal and enable the SSO option. Then, configure the same group attribute in your IdP and assign users to this group. This attribute is mandatory for DSPM to invoke the same group that is mapped in your IdP. If the user belongs to multiple groups, then you must create at least one group with the same name in DSPM, so the user can log in to DSPM using SSO.
- IdP groups are prioritized over DSPM groups. If a user is a part of both groups, they are logged in to the IdP group.
-
**Auto Update Group Based on IdP**: Select to allow automatic update of user and user's group information from your IdP.
When auto update is selected, the default groups (Default Super Admin, Default Read only, ZIA Viewers, ZIA DLP Managers) associated with the user are not impacted.
[See image.](#zpc-idpconfig-window)
-
Click **Save**.
The IdP is configured and the details are displayed on the **Single Sign-On** page.
[See image.](#zpc-idp-page)
When users try to log in to the DSPM Admin Portal, they are directed to the IdP portal for single sign-on.
[][![Adding an IdP configuration](/downloads/dspm/authentication/idp-configuration/adding-identity-providers/dspm-add-idp-config_0.png)
]
[][![Add an IdP configuration ](/downloads/dspm/authentication/idp-configuration/adding-identity-providers/dspm-add-idp-configr.png)
]
[][![Viewing the IdP details](/downloads/dspm/authentication/idp-configuration/adding-identity-providers/dspm-added-idp-config.png)
]