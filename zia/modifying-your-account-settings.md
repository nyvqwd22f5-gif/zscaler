# Modifying Your Account Settings
Source: https://help.zscaler.com/zia/modifying-your-account-settings
PDF: https://help.zscaler.com/pdf/com/en/1401976.pdf

[Account settings](/zia/about-account-settings) include options that allow you to modify various aspects of your account to suit your preferences (e.g., email notifications, Admin Portal color scheme, logo, etc.). You can make changes to the information associated with your tenant's account.
To modify your partner account settings, you can do the following:
- In the left-side navigation, go to **Settings**.
- Make changes to the following fields:
- **End User Subscription Agreement**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select the end user subscription agreement from the drop-down menu. You can view the selected end user subscription agreement notification for your customers when you log in to the ZIA Admin Portal.
-
**Partner UI Logout URL**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--{C}%3C!%2D%2D%7BC%7D%253C!%252D%252Dtd%2520%257Bborder%253A%25201px%2520solid%2520%2523ccc%253B%257Dbr%2520%257Bmso-data-placement%253Asame-cell%253B%257D%252D%252D%253E%2D%2D%3E--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Enter the URL that the tenants see when they log out of the ZIA Admin Portal.
This option is only available for white labeled partners.
- **White Labeling**: Enable this to white label the Admin Portals of your tenant accounts. For example, the partner can configure their logo that the tenants can see at the time of login. The partner can white label the following items:
- Partner Support
- Partner CSS Color Scheme (Magenta)
- Partner UI Logout URL
- Account Logo
- Background Color
- **SSO to Tenants' ZIA Admin Portal**: Enable Single Sign-On (SSO) to log in to the tenants' ZIA Admin Portal. You must obtain the SSO certificate from your SAML service provider before enabling this option. If you enable this option, you see the following options:
- **Certificate (.der)**: Extract and upload the public key from the SSO certificate provided by your SAML service provider. Ensure that the key is binary-encoded using a Distinguished Encoding Rules (DER) file before you upload it. The file extension must be .der and should not have other periods (.) in the file name.
- **Algorithm**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--{C}%3C!%2D%2D%7BC%7D%253C!%252D%252D%257BC%257D%25253C!%25252D%25252Dtd%252520%25257Bborder%25253A%2525201px%252520solid%252520%252523ccc%25253B%25257Dbr%252520%25257Bmso-data-placement%25253Asame-cell%25253B%25257D%25252D%25252D%25253E%252D%252D%253E%2D%2D%3E--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select the decryption algorithm for the SSO certificate.
You can log in to the tenants' ZIA Admin Portal using the following URLs:
- **Assertion Consumer Service (ACS) URL/Destination URL**: https://admin.<Cloud_Name>/ssologin.do
- **Entity ID**: https://admin.<Cloud_Name>
[See image.](#sso_to_tenant_zia_admin_portal)
- **SSO to Management Portal for Partners**: Enable SSO to log in to the Management Portal for Partners. You must obtain the SSO certificate from your SAML service provider before enabling this option.
- **Certificate (.pem)**: Upload the SSL public certificate that is used to verify the digital signature of the identity provider (IdP). This is the Base64-encoded PEM format certificate that you downloaded from your IdP. The file extension must be .pem and have no other periods (.) in the file name.
You can log in to the Management Portal for Partners using the following URLs:
- **Assertion Consumer Service (ACS) URL/Destination URL **(Depends on the IdP used (i.e., Okta or Azure)): https://partners.zscalerscm.net/partnersso.do.
- **Entity ID**: As a default value, Zscaler recommends using https://partners.zscalerscm.net/, or you can use any value that is unique to a customer or partner IdP.
[See image.](#sso_to_management_portal)
The following explains how the IdP-Initiated SSO works when you enable the SSO to Tenants' ZIA Admin Portal and SSO to Management Portal for Partners.
**IdP-Initiated SSO Workflow**
An IdP stores and verifies user identity. The users can access various applications and resources securely through the IdP portal. The Zscaler Management Hub supports IdP-initiated Single Sign-On for which the access and authentication take place through the partner's IdP portal. To learn more, see [Understanding SAML](/zia/understanding-saml).
The IdP-Initiated workflow is as follows:
- [SSO to Tenants' ZIA Admin Portal](#ssotenant)
- [SSO to Management Portal for Partners](#sso_management_portal)
[See image.](#sso_tile)
- []Enter the user name and password to log in to the IdP portal (e.g., Azure, Okta, etc.).
- Click the **SSO to Tenants ZIA Admin Portal **tile in the IdP portal to initiate SSO.
The browser sends a SAML message containing an assertion to the Partner Portal ACS URL.
- The Partner Portal identifies the user and sends back the signed assertion to the browser.
- The signed assertion is then received from the Partner Portal and the destination URL (i.e., Admin Portal) is authenticated.
Access to the Tenants' ZIA Admin Portal is complete.
- []Enter the username and password to log in to the IdP portal (eg., Azure, Okta, etc.).
- Click the **SSO to Management Portal for Partner **tile in the IdP portal to initiate SSO.
The browser sends a SAML message containing an assertion, identifies it, and sends back the signed assertion to https://partners.zscalerscm.net/partnersso.do.
- The signed assertion is then received and the destination URL is authenticated.
Access to the Management Portal for Partners is complete.
- **Internal Domain**: This field shows your internal domain generated when creating your partner account. It is a default domain created for the partner to log in for the first time.
- **Partner Domain**: This field shows your company domain. A partner can have a maximum of 16 domains. Contact Zscaler Support to change or add a partner domain.
- **Color Scheme**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select the color scheme you want the tenants to see in all the Admin Portals.
- **Partner Support**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select the support type for your account. Tenants can view this support information in their Admin Portals.
- **Partner Support Email**: If you select **Email **as the partner support, enter your support email address.
- &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
**Partner Support URL**: If you select **Portal** **URL **as the partner support, enter your support website URL.
-
**Reset Password and Send Activation Email**: Select this option to reset your default admin account password. You receive the password reset email link.
[See image.](#reset-password-email)
- **Partner Contact Name**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--{C}%3C!%2D%2Dtd%20%7Bborder%3A%201px%20solid%20%23ccc%3B%7Dbr%20%7Bmso-data-placement%3Asame-cell%3B%7D%2D%2D%3E--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Enter the name of the primary contact person of your partner account.
- &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
**Activation Email Recipient**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Enter the email recipient to receive the password reset link. You can enter multiple recipients. Click **Add Email** after each entry. You can remove all the recipients from the list (**Remove All**) or only specific emails from the list (**X**).
[See image.](#modifysettings)
- Click **Save **to** **save your changes.
[]![Settings section in the Settings page](/downloads/zscaler-tech-pubs-style-guide/draft-articles/modifying-your-account-settings-draft/Management%20Portal%20-%20Settings%20page.png)
[]![SSO to Management Portal for Partners](/downloads/zia/zscaler-management-portal-partners/getting-started/management-portal/modifying-your-account-settings/SSO%20to%20Management%20Portal%20for%20Partners.png)
[]![SSO to Tenants' ZIA Admin Portal](/downloads/zia/zscaler-management-portal-partners/getting-started/management-portal/modifying-your-account-settings/SSO%20to%20Tenants.png)
[]![SSO Tile](/downloads/zia/zscaler-management-portal-partners/getting-started/management-portal/modifying-your-account-settings/SSO%20Tile.png)
[]![Reset password email](/downloads/tech-pubs-drafts/zia-draft-articles/modifying-your-account-settings-draft-0/MMP%20email.png)
&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;