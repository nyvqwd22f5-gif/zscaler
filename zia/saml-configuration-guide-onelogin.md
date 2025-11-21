# SAML Configuration Guide for OneLogin
Source: https://help.zscaler.com/zia/saml-configuration-guide-onelogin
PDF: https://help.zscaler.com/pdf/com/en/1399666.pdf

This guide illustrates how to configure OneLogin as the identity provider (IdP) for the [[variable:Zscaler-service]]. It also describes how to integrate Active Directory and configure an AD connector. See the OneLogin documentation for additional information about the steps in the example.
Prerequisites
Ensure that you have the following before you start configuring OneLogin as the IdP:
- A OneLogin account with admin privileges
- The Zscaler SAML certificate (See [Adding Identity Providers](/zia/adding-identity-providers#SP-SAML-Certificate))
Configuring OneLogin as the IdP for the Zscaler service
To configure OneLogin as the IdP for the Zscaler service:
- [1. Add the Zscaler Application in OneLogin](#adding-zscaler-service-application)
- [2. Download the OneLogin SAML Certificate](#idp-saml-cert)
- [3. Assign Users to the Zscaler Application](#assign-users)
- [4. Add an Active Directory Server](#ad)
- [5. Install the OneLogin Active Directory Connector](#connector)
- [6. Add OneLogin as the IdP for the Zscaler service](/zia/adding-identity-providers)
- [7. Configure SAML SSO in the ZIA Admin Portal](#saml-zscaler-admin-portal)
- [8. Configure the Zscaler Authentication Exemptions List](#authentication-exemptions)
Testing the SAML Configuration
This testing method only applies if you're forwarding traffic using PAC files, GRE tunnels, or IPSec tunnels, and you've enabled **Enforce Authentication** for the [location](/zia/configuring-locations#EnforceAuthentication) or [sublocation](/zia/configuring-sublocations#EnforceAuthentication).
To test the SAML configuration with OneLogin:
- If you're already logged in to the Zscaler service, browse to https://login.<Zscaler cloud Name>/zscaler.portal, and click **Logout**. Replace <Zscaler cloud Name> with your Zscaler cloud name. To learn how you can find your cloud name, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
- Ensure that your traffic is being forwarded to the Zscaler service and then browse to a website.
- When prompted for authentication, enter your OneLogin credentials.
Troubleshooting
If any errors occur, see [Troubleshooting SAML](/zia/saml-troubleshooting-guidelines) to troubleshoot browser settings and SAML error codes.
[]To add the Zscaler application to OneLogin:
- Log in to OneLogin as an administrator.
- Go to **Portal**, click **Find apps**.
[See image.](#seeimg1)
- In the **Find apps** window, enter "Zscaler" in the search field, then click **add** next to the Zscaler application.
[See image.](#seeimg2)
- In the **Add Zscaler** window, choose **Zscaler** in the **This app will be used by** field.
- Click **Continue**.
- In the **Single Sign-on** tab, do the following, and then click **Update**:
[See image.](#seeimg3)
- **SAML Endpoints URL**: Copy the SAML Endpoints URL. You will paste this in Step f of [6. Configure SAML SSO in the ZIA Admin Portal](/zia/saml-configuration-example-onelogin#saml-zscaler-admin-portal).
- **Credentials**: Select **Configured by admin**.
- **Default values**: Select **Email** for the **NameID (Login)**.
[]To download the OneLogin SAML certificate:
- Go to **Security** > **SAML**.
- Under **x.509 certificate**, click **.PEM format** to download your IdP SAML SSL certificate in PEM format.
[See image.](#seeimg4)
[]You can assign users individually or by roles. This guide describes how to assign users by roles.
To assign users to the Zscaler application:
- Go to **People** > **Roles**.
- Click **edit**.
- Select **Zscaler** from the list of apps.
- Click **Commit changes**, then click **Update**.
[]To add a new Active Directory (AD):
- Go to **People** > **Directories**.
- Click **New Directory**.
- Click **Windows Server Active Directory**.
[See image.](#seeimg5)
- In the **New Directory** window, click **Update**.
- In the **Active Directory** window, do the following, then click **Update**:
[See image.](#seeimg6)
- Download the AD Connector.
- Copy the token to your clipboard. You will need it for step d in [5. Install the OneLogin Active Directory Connector](/zia/saml-configuration-example-onelogin#onelogin-connector).
- When the confirmation message appears, click **Save File**.
[]To install the OneLogin AD connector:
- Start the AD connector.
- When the wizard appears, click **Next**.
- Specify where you’d like to install the connector and click **Next**.
- In the **Directory Token** window, paste the token you copied in step e of [4. Add an Active Directory Server](/zia/saml-configuration-example-onelogin#ad), then click **Next**.
[See image.](#seeimg7)
- Click **Close**.
If a proxy is in place within your network, create a proxy rule to allow the OneLogin AD connector traffic through the proxy.
[]To configure SAML SSO in the ZIA Admin Portal:
- Go to **Administration **>** Authentication Settings**.
- Under **Authentication Frequency**,** **choose how often users are required to authenticate to the Zscaler service. To learn more, see [About Authentication Profile](/zia/about-authentication-profile#authentication-frequency). If you select **Custom**, the following field will appear:
- **Custom Authentication Frequency (days)**: Specify 1 to 180 days.
- Under** Authentication Type**, choose **SAML**.
[See image.](#seeimage-2c)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![The SAML option under Authentication Type on the Authentication Profile page.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/configuring-saml/ZIA-Authentication-Profile-Authentication-Type.png)
[]To configure the Zscaler Authentication Exemptions list and enable users access to Google Apps:
- Go to **Administration **>** Advanced Settings**.
- In the **Authentication Exemptions** section, enter "app.onelogin.com" in **Exempted URLs**.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
If you're using PAC files, enter the following exception to the [PAC file](/zia/using-default-pac-files-forward-traffic-zia) exemption list. Otherwise, the authentication will fail.
If (shExpMatch(host, "app.onelogin.com"))
return "DIRECT";
[]![Logging into OneLogin as an admin and using the find apps link](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-onelogin/find_apps_on_onelogin_.png)
[]![Onelogin portal showing how to add Zscaler as an app](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-onelogin/add_zscaler.png)
[]![OneLogin portal showing how to configure the Zscaler app with single sign-on](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-onelogin/single_sign-on_tab.png)
[]![OneLogin portal showing how to download the x.509 certificate](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-onelogin/x.509_certificate.png)
[]![The Windows Server Active Directory in OneLogin](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-onelogin/windows_server_active_directory.png)
[]![OneLogin portal showing how to download the Active Directory connector and the required token](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-onelogin/active_directory_connector_and_token.png)
[]![Window showing where to add the directory token in the OneLogin Active Directory Connector](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-onelogin/add_the_directory_token.png)