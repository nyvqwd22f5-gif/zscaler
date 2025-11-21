# Configuring the Zscaler Identity Proxy for Cloud Apps
Source: https://help.zscaler.com/zia/configuring-zscaler-identity-proxy-cloud-apps
PDF: https://help.zscaler.com/pdf/com/en/1399331.pdf

[Watch a video about ZIA Identity Proxy.](https://fast.wistia.net/embed/iframe/iwyp1wajur)
The Zscaler Identity Proxy forces users to access cloud applications through Zscaler. You can configure Zscaler as an Identity Provider (IdP) for the following cloud apps:
- Box
- Google Apps
- Microsoft 365
- Salesforce
- GitHub
- ShareFile
- ServiceNow
- Slack
When users try to access the cloud apps using their corporate accounts, but without going through the Zscaler service, authentication fails, and the users aren't able to log in.
To configure Identity Proxy settings for cloud applications in the ZIA Admin Portal, see [1. Configure Identity Proxy Settings for each Cloud App](/zia/configuring-zscaler-identity-proxy-cloud-apps#configure-identity-proxy-settings).
Zscaler provides secure access to SaaS applications from unmanaged endpoints to ensure users can access SaaS applications securely, with all the defined ZIA policies being applied and transactions being logged.
The following diagram shows how the authentication process works when the Zscaler service is set up as the IdP for the cloud apps. The cloud app used in this example is Salesforce:
- The user accesses a SaaS application (e.g., Salesforce) from an unmanaged device.
- The customer's SaaS application tenant is configured with a Zscaler Identity Proxy as the IdP. The Zscaler ID works as a proxy between the SaaS application and the customer's IdP (e.g., Okta, PingFederate, Azure, etc.).
- When the end user tries to authenticate to the SaaS application, the user is redirected to the Zscaler ID proxy. The ID proxy component then authenticates the user against the customer's IdP to ascertain the identity of the user.
- If the customer's IdP indicates the authentication request is originating from an unmanaged endpoint (based on the device identity attribute) and if the original request was not made via the ZIA Public Service Edge, the ID proxy evaluates how the traffic is handled based on the action configured in the identity proxy configuration.
- If the **Action** is set to** Block**: Traffic is blocked, ensuring that the user is unable to access the SaaS application from an unmanaged device.
- If the **Action** is set to** Browser Isolate**: User is redirected to an isolated browser.
- The isolated browser then makes a request to a SaaS application via ZIA Service Edge.
- The isolated browser is always proxied to send the traffic via the ZIA Service Edge. All the traffic from the isolated browser is enforced by the policies defined and all the transactions from the isolated browser are logged.
![Isolated Identity proxy](/downloads/zia/authentication-administration/identity-proxy-settings/configuring-zscaler-identity-proxy-cloud-apps/ZIA-Identity-Proxy_0.png)
​​Prerequisite
Ensure [SSL Inspection](/zia/deploying-ssl-inspection) is enabled for the organization location before configuring the Zscaler service as an IdP for the following cloud apps:
- Box
- Google Apps
- Microsoft 365
- Salesforce
- GitHub
- ShareFile
- ServiceNow
- Slack.
Configuring the Zscaler Service as an IdP Proxy
If you have configured a cloud app as an IdP for authentication, it cannot be used for Identity Proxy. For example, if Microsoft Entra ID is configured as your IdP, Office 365 cannot be configured for Identity Proxy.
To configure the Zscaler service as an IdP Proxy:
- [1. Configure Identity Proxy Settings for the Cloud App in the ZIA Admin Portal](#configure-identity-proxy-settings)
- [2. Download the Zscaler Certificate and Obtain Information from the ZIA Admin Portal](#Download)
- [3. Configure Zscaler as the IdP for Your Cloud App](#Configure)
After the Zscaler service is configured as the IdP Proxy, users of the specified cloud app are redirected to Zscaler Identity Proxy for authentication.
[]To download the Zscaler certificate and obtain information from the ZIA Admin Portal:
- Go to** Administration **>** Identity Proxy Settings**.
The Identity Proxy Settings page displays the settings for the cloud apps.
- Click **Download** to download the Zscaler certificate for the cloud app that you are configuring.
- Copy the** Identity Proxy URL** and the **Issuer Entity ID** for the cloud app that you are configuring. Click the values to expand the URL.
[See image.](#Image1)
[]![Screenshot highlighting the Identity Proxy URL and Issuer Entity ID for a cloud app on the Identity Proxy Settings page.](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-zscaler-identity-proxy-cloud-apps-draft/Identity%20Proxy%20URL%20and%20Issuer%20Entity%20Id.png)
[]Ensure that you have the following from the ZIA Admin Portal for the cloud app:
- The Issuer Entity ID
- The Zscaler certificate that you downloaded from the ZIA Admin Portal
- The Identity Proxy URL
Configure Zscaler as the IdP for the cloud app. Following are instructions for each app:
- [Box](#Box)
- [Office 365](#office-365)
- [ShareFile](#sharefile)
- [GitHub](#github)
- [ServiceNow](#servicenow)
- [Google Apps](#Apps)
- [Salesforce](#Salesforce)
- [Slack](#slack)
[]To set up Single Sign-On (SSO), [submit a request](https://support.box.com/hc/en-us/requests/new?ticket_form_id=360002612594) with Box. Box uses the information that you provide to set up the SSO integration.
Complete the following in the request form:
- **Your email address**: Enter your email address.
- **Briefly summarize your issue/question**: Specify that you want to set up SSO for Box.
- **Who is your Identity Provider?**: Select **Other w/o Metadata** or **Other with Metadata**. If you select **Other with Metadata**,** **make sure that you upload the Metadata file in the attachments.
- **Give us more details**: Enter the following information:
- **Entity/Connection ID**: The **Issuer Entity ID **that you copied from the ZIA Admin Portal.
- **Redirect URL**: The **Identity Proxy URL** that you copied from the ZIA Admin Portal.
- **Identity Provider**: Enter **Zscaler Inc.**
- **Attribute for User's First Name**: Enter **NameID**
- **Attribute for Groups**: Provide the group attribute if you are using Groups and have added a Group Identifier Name in the ZIA Admin Portal.
- **Priority**: Set the priority according to your requirement.
- **Box Subdomain**: Enter the Box subdomain of your company.
- **Attachments**: Attach the public certificate that you downloaded from the ZIA Admin Portal. If you've selected **Other with Metadata **as your IdP, attach the Metadata file downloaded from the ZIA Admin Portal as well.
[See image.](#box-sso-form)
[]![Screenshot of request form for SSO configuration](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-zscaler-identity-proxy-cloud-apps-draft/Box%20SSO%20request.png)
[]To set up SSO with Google Apps:
- Log in to the [Google Admin Console](https://admin.google.com/) with your admin account.
- Click **Security**. The Security page appears
- On the Security page, click** Set up single sign-on (SSO**).
- Enable **Setup SSO with third party identity provider**
- Complete the following:
- **Sign-in page URL**: Enter the Identity Proxy URL that you copied from the ZIA Admin Portal.
- **Sign-out page URL**: Enter the Google logout URL: `https://accounts.google.com/logout`.
- **Change password URL**: (Optional) Enter a URL that allows users to change their passwords.
- **Verification certificate**: Upload the Zscaler certificate that you downloaded from the ZIA Admin Portal.
- Click **Save**
[See image.](#g-app)
This configuration only applies if Identity Proxy is enabled for the whole organization. If your organization requires configuration for a specific organization unit (OU), refer to the [Google documentation](https://support.google.com/a/answer/12032922?hl=en#org_profile).
Users who are assigned administrator roles in Google cannot use SSO.
[]To set up SSO with Salesforce:
- [a. Configure the Zscaler SAML SSO Settings](#configure-sso-settings)
- [b. Enable the Zscaler SAML SSO Settings as the Authentication Service](#enable-sso-settings-auth)
- [c. Obtain the Salesforce Login URL](#salesforce-login-url)
[]To configure the Zscaler SAML SSO settings:
- Log in to [Salesforce](https://www.salesforce.com/).
- In the top right corner, click **Setup**. The Setup page appears.
- On the Setup page, expand **Security Controls** in the left-hand menu, and select **Single Sign-On Settings**. The Single Sign-On Settings page appears.
- On the Single Sign-On Settings page, click **Edit**, and check **SAML Enabled**.
- Click **Save**.
- In the Single Sign-On Settings page, click **New**.
- Configure the following SAML SSO settings:
- **Name**: Enter a name for the setting.
- **API Name**: Salesforce automatically uses the value you entered for **Name**. You can customize the name here, if you want.
- **Issuer**: Enter the **Issuer Entity ID** that you copied from the ZIA Admin Portal.
- **Entity ID**: Enter `https://saml.salesforce.com/`.
- Select your **Request Signing Certificate**, **Request Signature Method**, and **Assertion Decryption Certificate** as desired.
- **SAML Identity Type**: Select **Assertion contains the User's Salesforce username**.
- **SAML Identity Location**: Select **Identity is in the NameIdentifier element of the Subject statement**.
- **Service Provider Initiated Request Binding**: Select **HTTP POST**.
- **Identity Provider Certificate**: Upload the certificate you downloaded from the ZIA Admin Portal.
- **Identity Provider Login URL**: Enter the** Identity Proxy URL** that you copied from the ZIA Admin Portal.
- Configure the** Custom Logout URL**, **Custom Error URL**, and **Single Logout Enabled** fields as desired.
[See image.](#Image4)
- Click **Save**
[]To enable the Zscaler SAML SSO settings as the authentication service:
- In the top right corner, click **Setup **and select **Setup** from the drop-down menu. The Setup page appears.
- On the Setup page, expand **Company Settings** in the left-hand menu, and select **My Domain**. The My Domain page appears.
- Scroll down to **Authentication Configuration** and click **Edit**. The **Authentication Configuration** page appears.
- On the Authentication Configuration page, select the **Authentication Service** that you configured in ZIA Admin Portal. In this example, it's ZscalerExample.
- Click **Save**.
[See image.](#sf-auth)
[]After you configure Zscaler as the IdP for Salesforce, you must retrieve the Login URL from the app. To obtain the Salesforce Login URL:
- In the top right corner, click **Setup **and select **Setup** from the drop-down menu. The Setup page appears.
- On the Setup page, expand **Identity** in the left-hand menu, and select **Single Sign-On Settings**. The Single Sign-On Settings page appears.
- In the **Single Sign-On Settings** list, click the Zscaler SAML SSO setting that you configured in ZIA Admin Portal. In this example, it's ZscalerExample.
- Copy the **Login URL** and specify it as the **ACS URL** while when you configure configuring the Salesforce cloud app instance in the ZIA Admin Portal.
[See image.](#sf-url)
[]To set up SSO with GitHub:
- Log in to [GitHub](https://github.com) with your admin account. Ensure that you are logged in to Zscaler service so that the traffic is forwarded to Zscaler.
- Click your profile picture and then click **Your organizations**.
- From the **Organizations** page, click the required organization link.
- Go to **Settings** > **Organization security**.
- Under the **SAML single sign-on** section, select **Enable SAML authentication** and complete the following:
- **Sign on URL**: Enter the Identity Proxy URL that you copied from the ZIA Admin Portal.
- **Issuer**: Enter the Issuer Entity ID that you copied from the ZIA Admin Portal.
- **Public certificate**: Copy and paste the text from the Zscaler certificate you downloaded from the ZIA Admin Portal.
-
Click **Test SAML configuration** and then click **Save** after your SAML SSO identity is successfully authenticated.
[See image.](#github-tested)
- Go to the **Teams** tab and click **Authenticate your account** before using SSO for the first time.
- Click **Continue**.
[]To set up SSO with ServiceNow:
- Log in to your ServiceNow instance with your admin account. Ensure that you are logged in to Zscaler service so that the traffic is forwarded to Zscaler.
- On the left pane, under **Multi-Provider SSO**, click **Identity Providers**.
-
From the **Identity Providers** page, click **New** and then click **SAML**.
[See image.](#servicenow-idp-new-saml)
-
On the **Identity Provider New Record** page:
- **Name**: Enter a name for the identity provider.
- **Identity provider URL**: Enter the Issuer Entity ID that you copied from the ZIA Admin Portal.
- **Identity Provider's AuthnRequest**: Enter the Identity Proxy URL that you copied from the ZIA Admin Portal.
[See image.](#servicenow-idp-url-entityid)
-
Go to the **Advanced** tab.
- **UserField**: Ensure that this is set to email.
- **Single Sign-On Script**: Select **MultiSSOv2_SAML2_custom**.
[See image.](#servicenow-idp-adv)
- Click **Submit**. The IdP is created and added to the **Identity Providers** page.
- From the **Identity Providers** page, click the identity provider record that you created. Edit the following:
-
In the **X.509 Certificate** section, click the **New** button.
[See image.](#servicenow-new-cert)
-
On the **X.509 Certificate New Record** page:
- **Name**: Enter a name for the certificate.
- **Format**: Select the **PEM** format from the drop-down menu.
- **PEM Certificate**: Copy and paste the text from the Zscaler certificate that you downloaded from the ZIA Admin Portal, and click **Submit**.
[See image.](#servicenow-add-public-cert)
- From the **X.509 Certificate** section, click the **Edit** button. The **Edit Members** page appears.
-
From the **Collection** pane, select the certificate that you created and add it to the **X.509 Certificates List** pane and then click **Save**.
[See image.](#servicenow-map-idp-cert)
- Click **Test Connection** on the top right.
-
After the connection is tested successfully, click **Activate**.
[See image.](#servicenow-test-activate)
- From the **Related Links** section, click **Set as Auto Redirect IdP**.
-
Select the **Default** option and click **Update**.
[See image.](#servicenow-auto-redirect)
[]![Screenshot of New IdP for ServiceNow](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/configuring-zscaler-identity-proxy-cloud-apps/ZIA-ServiceNow-New-IdP-SAML.png)
[]![Screenshot of Providing Zscaler IdP URL and Entity ID on ServiceNow](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/configuring-zscaler-identity-proxy-cloud-apps/ZIA-ServiceNow-IdP-URL-EntityID.png)
[]![Screenshot of ServiceNow IdP Advanced Tab](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/configuring-zscaler-identity-proxy-cloud-apps/ZIA-ServiceNow-Idp-Advanced.png)
[]![Screenshot of Adding New Public Certificate for ServiceNow IdP](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/configuring-zscaler-identity-proxy-cloud-apps/ZIA-ServiceNow-Idp-New-Cert.png)
[]![Screenshot of Adding Zscaler Public Certificate to ServiceNow IdP Configuration](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/configuring-zscaler-identity-proxy-cloud-apps/ZIA-ServiceNow-Idp-Public-Cert.png)
[]![Screenshot of Zscaler Public Certificate Mapping with ServiceNow](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/configuring-zscaler-identity-proxy-cloud-apps/ZIA-ServiceNow-IdP-Cert-Mapping.png)
[]![Screenshot of Testing and Activating Zscaler IdP on ServiceNow](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/configuring-zscaler-identity-proxy-cloud-apps/ZIA-ServiceNow-Test-Activate.png)
[]![Screenshot of Saving Zscaler IdP on ServiceNow](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/configuring-zscaler-identity-proxy-cloud-apps/ZIA-ServiceNow-Idp-Save.png)
[]To set up SSO with Slack:
- Log in to Slack with your admin account. Ensure that you are logged in to Zscaler service so that the traffic is forwarded to Zscaler.
- Click **Manage Organization** in the upper right of the page. The **Workspaces** page appears.
-
Go to **Security** > **SSO settings **in the left-side navigation. The **SSO Settings** page appears.
[See image.](#slack-sso-settings-page)
- Click **Configure SSO**. The **Configure SSO** window appears.
-
In the **Configure SSO** window:
- **SSO Name**: Enter a name for the SSO.
- **SAML 2.0 Endpoint URL**: Paste the Zscaler Identity Proxy URL that you copied from the ZIA Admin Portal.
- **Identity Provider Issuer URL**: Paste the Zscaler Issuer Entity ID that you copied from the ZIA Admin Portal.
- **Service Provider Issuer URL**: Enter `https://slack.com`.
- **Public (X.509) Certificate**: Open the zscaler_certificate.cer file that you downloaded from the ZIA Admin Portal with a text editor and copy and paste the entire contents.
- **Sign the Response**: Deselect this checkbox.
[See image.](#slack-configure-sso-windo)
- Click **Test Configuration **on the bottom right of the window. The **Finish SSO Configuration** window appears. If the configuration tests correctly, a confirmation message appears stating that everything looks good at the top of the window. If there is a problem with the configuration, you receive either a glitch reported or a failure and you have to start over from the beginning.
- On the **Finish SSO Configuration** page, click **Confirm Update** to activate the configuration.
[]![Viewing the SSO Settings Page in Slack](/downloads/zia/authentication-administration/identity-proxy-settings/configuring-zscaler-identity-proxy-cloud-apps/ZIA-Slack-SSO-Settings-Page.png)
[]![Configuring SSO on the Configure SSO page for the Slack Identity Provider in Slack](/downloads/zia/authentication-administration/identity-proxy-settings/configuring-zscaler-identity-proxy-cloud-apps/ZIA-Slack-Configure-SSO-Wizard.png)
[]To set up SSO with Microsoft 365:
- [a. Set up SAML for Microsoft Entra Connect (formerly Azure AD Connect)](#set-up-saml)
- [b. Configure AD FS claim rule for Microsoft 365](#configure-adfs)
If you need to reset the Microsoft 365 configuration, complete the following steps:
-
Run the following command to reset your domain authentication and prepare AD FS for setting Zscaler parameters:
`Set-MsolDomainAuthentication -DomainName <YourDomainName> -Authentication Managed`
- (Optional) Delete the AD FS claim rule that was added to the Claim Issuance Policy for the Relying Trust Party. See [Configure AD FS claim rule for Office 365](#set-up-saml).
- []Configure federation with AD FS and connect it via Microsoft Entra Connect. To learn more, refer to the [Microsoft documentation for AD FS](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-install-custom#configuring-federation-with-ad-fs).
-
Log in to the Microsoft Entra Portal via Windows PowerShell using the following command:
`Connect-MsolService`
-
Run the following command to reset your domain authentication and prepare AD FS for setting Zscaler parameters:
`Set-MsolDomainAuthentication -DomainName <YourDomainName> -Authentication Managed`
- Configure your setup script file (PS1) using the following template:
- [See setup script template.](#sample-file)
- [See script parameters and descriptions.](#table-description)
-
Run the following command to execute the script:
`./<setup script name>.ps1`
-
Run the following command to verify the parameters configured:
`Get-MsolDomainFederationSettings -DomainName <YourDomainName> `
[See image.](#o365-windows-configure)
[]
| **Parameter** | **Description** |
| ------------- | --------------- |
| $dom | Name of the domain |
| $Brandname | Custom brand name |
| $LogOnUrl | Identity Proxy URL that you copied from the ZIA Admin Portal |
| $LogOffUrl | Log out URL |
| $ecpUrl | Same as the logon URL |
| $MySigningCert | Text copied from the Zscaler certificate that you downloaded from the ZIA Admin Portal |
| $MyURI | Zscaler cloud name |
| $uri | Issuer Entity ID that you copied from the ZIA Admin Portal |
[]$dom="<Your Domain>"
$BrandName="<Custom Brand Name>"
$LogOnUrl="https://idp.<Zscaler Cloud Name>/samlsso/<Issuer Entity Id>"
$LogOffUrl="https://logout.<Zscaler Cloud Name>/"
$ecpUrl="https://idp.<Zscaler Cloud Name>/samlsso/<Issuer Entity Id>"
$MySigningCert= "<Zscaler Certificate Content>"
$MyURI="<Zscaler Cloud Name>"
$uri="<Issuer Entity Id>"
Set-MsolDomainAuthentication -DomainName $dom -FederationBrandName $BrandName -Authentication Federated -PassiveLogOnUri $LogOnUrl -ActiveLogOnUri $ecpURL -SigningCertificate $MySigningCert -IssuerUri $uri -LogOffUri $LogOffUrl -PreferredAuthenticationProtocol "SAMLP"
[]Ensure that the [SAML 2.0 IdP for single sign-on](http://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-fed-saml-idp) is configured.
- Select your **Relying Party Trust** in the **AD FS Management** portal.
-
Add the following custom rule to the **Claim Issuance Policy**:
`c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname"]
=> issue(store = "Active Directory", types = ("http://schemas.xmlsoap.org/claims/UPN",
"http://schemas.microsoft.com/LiveID/Federation/2008/05/ImmutableID"), query =
"samAccountName={0};userPrincipalName,objectGUID;{1}", param = regexreplace(c.Value,
"(?<domain>[^\\]+)\\(?<user>.+)", "${user}"), param = c.Value);
`
- Log in to [Office 365 Portal](https://portal.office.com) and verify if [login.microsoftonline.com](http://login.microsoftonline.com) gets redirected to IdP.<Zscaler Cloud Name> for authentication.
[]![Screenshot of windows powershell with the configured parameters](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/configuring-zscaler-identity-proxy-cloud-apps/zia-o365-Windows-powershell-parameters-configured.png)
[]![Screenshot of SSO Settings for GitHub IdP Configuration](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/configuring-zscaler-identity-proxy-cloud-apps/ZIA-GitHub-SSO-Settings-Tested-IdP.png)
[]To set up SSO with ShareFile:
- Log in to [ShareFile](https://secure.sharefile.com/Authentication/Login) with your admin account.
- From the ShareFile dashboard, go to **Settings** > **Admin Settings** > **Security** > **Login & Security Policy**.
-
Under the **Basic Settings** section for** Single sign-on / SAML 2.0 Configuration**, complete the following:
- **Enable SAML**: Select **Yes** to enable SAML authentication.
- **Your IDP Issuer / Entity ID**: Enter the Issuer Entity ID that you copied from the ZIA Admin Portal.
- **X.509 Certificate**: Click **Change** and then copy and paste the text from the Zscaler certificate you downloaded from the ZIA Admin Portal.
- **Login URL**: Enter the Identity Proxy URL that you copied from the ZIA Admin Portal.
[See image.](#sharefile-basic)
-
Under **Optional Settings**, complete the following:
- **Require SSO Login**: Select **No**.
- **SP-Initiated SSO certificate**: Choose **HTTP Redirect with no signature**.
- **Enable Web Authentication**: Select **Yes**.
- **SP-Initiated Auth Context**: Choose **Username and Password** and **Minimum**.
[See image.](#sharefile-optional)
- Click **Save**.
[]![Screenshot of SSO Basic Settings for ShareFile IdP Configuration](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/configuring-zscaler-identity-proxy-cloud-apps/ZIA-ShareFile-Basic-Settings-IdP.png)
[]![Screenshot of SSO Optional Settings for ShareFile IdP Configuration](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/configuring-zscaler-identity-proxy-cloud-apps/ZIA-ShareFile-Optional-Settings-IdP.png)
[]To configure Identity Proxy settings for the cloud app:
- Log in to the ZIA Admin Portal.
- Go to** Administration **>** Identity Proxy Settings**.
-
Click **Add Cloud Application** to add a new cloud app instance. You can also click the **Edit **icon to edit a cloud app instance that is already configured. Click **Add Cloud Application** to add a new cloud app instance. To edit a cloud app instance that is already configured, click the **Edit** icon.
You can select **Other Cloud Apps** for other cloud apps that support standard SAML-based authentication.
- In the **Add Cloud Application**/**Edit Identity Proxy Settings** window, do the following:
- **Name**: Enter a name for the cloud app instance.
- **Status**: Enable to use the Zscaler service as the IdP proxy for the cloud app.
- **Cloud Application**: Select the cloud app that you want the IdP for.
- **Domain**: Applicable only to **Google Apps**. Enter the domain name for the Google Apps cloud application.
- **ACS URL**: This is the Assertion Consumer Service URL. For Box, the URL is displayed. For Office 365, the URL is auto-filled. For Google Apps, the URL is completed as you type in your domain. For the rest of the cloud apps, enter the **Login URL** that you copy from your cloud app.
- **Entity ID**: This is auto-populated for most of the cloud apps. For Salesforce, enter the Entity ID that you copy from your cloud app. For Github, enter the ACS URL string without the `/saml/consume` string at the end of the URL.
- **Response Signing SSL Certificate**: Choose the certificate that you want the Identity Proxy to use for signing SAML responses. Zscaler recommends choosing the certificate with the longest validation period.
- **SSL Certificate Expiration Date**: Displays the expiration date for the signing SAML response certificate for the Identity Proxy. You see the expiration date field if the certificate is about to expire or has expired. A **Caution** icon appears if the certificate expires within 30 days.
- **Identity Transformation**: Choose one of the following transformation rules for the login attribute.
- **Pass-through Zscaler Identity**: Passes the Zscaler login name as is.
-
**Change Domain to**: Replaces the domain part of the username with a different domain name that you choose in the **Change Domain to** drop-down menu.
Zscaler recommends that you *not* use this option for GitHub.
- **Remove Domain Name**: Deletes the domain part of the user name in the response and passes only the user ID.
- **Pass-on Group Details**: Enable to send all group information of the user in the response. For GitHub, select **Disable** because groups are not supported on GitHub.
- **Group Identifier Name**: Enter the group attribute name.
- **Managed Device Detection**: One of the following options appears based on whether your account is [[variable:zslogin]]-enabled or not:
- (With [[variable:zslogin]])** Is Device Managed Attribute True**: Enable to identify the user devices as managed devices if their traffic is proxied via Zscaler and matches the configured **Is Device Managed** attributes sent by the [[variable:zslogin]] service. This option is grayed out if the **Is Device Managed** attributes are not configured in the ZIdentity Admin Portal. To configure or edit the attribute in the ZIdentity Admin Portal, see [Adding SAML Identity Providers](/zslogin/adding-saml-identity-providers).
- (Without [[variable:zslogin]])** Device Trust Attribute Matches the Configured Value**: Enable to identify the user devices as managed devices if their traffic is proxied via Zscaler and matches the configured device trust attributes in your default IdP. Ensure that your default IdP configuration specifies the **Device Trust Attribute** and **Device Trust Attribute Value** fields to allow the ZIA service to identify your managed devices, otherwise, this option is grayed out.
- **Device Trust Attribute**: Displays the SAML trust attribute configured on your IdP. This field can't be edited. To configure or edit the trust attribute, see [Adding Identity Providers](/zia/adding-identity-providers).
- **Device Trust Attribute Value**: Displays the SAML trust attribute value configured on your IdP for managed devices. This field can't be edited. To configure or edit the trust attribute value, see [Adding Identity Providers](/zia/adding-identity-providers).
- **Action**: Choose one of the following actions for when unmanaged devices try to access the cloud app:
- **Browser Isolation**: Isolates the traffic from unmanaged devices through a remote browser based on the isolation profile selected. To learn more, see [What Is Isolation?](/isolation/what-is-isolation)
- **Isolation Profile**: &amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;gt;
Select the isolation profile from the list if you chose the **Browser Isolation** action. This list includes the isolation profiles that you created for your organization.
- **Block**: Blocks access to the cloud app from an unmanaged device.
- Click** Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot of Salesforce SAML SIngle Sign-On Settings page](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/configuring-zscaler-identity-proxy-cloud-apps/zia-salesforce-sso.png)
[]![Screenshot of Salesforce Authentication Configuration](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/configuring-zscaler-identity-proxy-cloud-apps/zia-salesforce-auth.png)
[]![Screenshot of the Salesforce Login URL](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/configuring-zscaler-identity-proxy-cloud-apps/zia-salesforce-url.png)
![Screenshot of the setting for Google admin](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/configuring-zscaler-identity-proxy-cloud-apps/zia-google-identity-proxy0.png)
[]