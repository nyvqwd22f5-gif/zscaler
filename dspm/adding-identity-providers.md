# Adding Identity Providers
Source: https://help.zscaler.com/zia/adding-identity-providers
PDF: https://help.zscaler.com/pdf/com/en/1401371.pdf

Adding an identity provider (IdP) in the ZIA Admin Portal is one of the tasks you must complete when configuring SAML Single Sign-On (SSO). To learn more, see [Configuring SAML](/zia/configuring-saml).
The Zscaler service can support up to 64 different SAML IdPs per organization. To add multiple IdPs, you must disable **Enable SAML Auto-Provisioning** for your existing IdP or change the **User Repository Type** to **Hosted DB** on the [Authentication Profile page](/zia/about-authentication-profile).
To add an IdP and configure the Zscaler service as the service provider (SP) for SAML:
- Go to **Administration **>** Authentication Settings**.
- Click the **Identity Providers** tab.
- Click **Add IdP**.
If you have an existing IdP configuration, the **What do you want to do?** window appears. Click **Add another SAML IdP for a subset of users or locations** and then **Next**.
[See image.](#seeimage-3)
The **Add IdP** window appears.
-
[]In the **Add IdP** window:
- **Name**: Enter a name for the IdP.
- **Status**: **Enable** or **Disable** the IdP.
- **SAML Portal URL**: Enter the SSO URL of the SAML portal to which users are sent for authentication. Ensure that it is publicly resolvable if you want users to authenticate from the internet. Additionally, ensure that it's protected using HTTPS. This information is in the XML metadata of the IdP or obtained during the configuration:
-
Active Directory Federation Services (AD FS): Enter the SAML SSO URL from the `Location` attribute in the AD FS XML metadata:
`<SingleSignOnService Binding="safemarch:SAML:2.0:bindings:HTTP-POST" Location="https://adfs.safemarch.com/adfs/ls/"/>`
- Microsoft Entra ID (formerly Azure Active Directory): Enter the **Login URL **you copied in [SAML & SCIM Configuration Guide for Microsoft Entra ID](/zia/saml-scim-configuration-guide-azure-active-directory#adding-zscaler-cloud-application).
- CA Single Sign-On (CA SSO): Enter the `redirectURL` from the script configured in [SAML Configuration Guide for CA Single Sign-On](/zia/saml-configuration-guide-ca-single-sign-on#ca-siteminder).
- Google Apps: Enter the **SSO URL** you copied in [SAML Configuration Guide for Google Apps](/zia/saml-configuration-guide-google-apps#google-apps).
- Okta: Enter the **Sign on URL** you obtained in [SAML & SCIM Configuration Guide for Okta](/zia/saml-scim-configuration-guide-okta#conf-zscaler).
- OneLogin: Enter the **SAML Endpoints URL** you copied in [SAML Configuration Guide for OneLogin](/zia/saml-configuration-guide-onelogin#adding-zscaler-service-application).
- **Login Name Attribute**: Enter the SAML attribute that maps to the login name that users enter when they authenticate to the Zscaler service. Typically, it's `NameID`, which is entered as one word, with no spaces. This field is case-sensitive.
- **Entity ID**: The entity ID is the globally unique name for this SAML entity.
- **Org-Specific Entity ID**: Enable if you have more than one organization instance on the same Zscaler cloud. For example, if you have two organization instances on the same Zscaler cloud and must authenticate both instances against the same Microsoft Entra ID account, you can't use the same entity ID for multiple apps in Microsoft Entra ID. For this situation, you must enable this setting for both instances to generate a unique organization-specific entity ID.
-
**IdP SAML Certificate**: Upload the SAML certificate that is used to verify the digital signature of the IdP. This is the certificate you downloaded from your IdP. The certificate must be in base-64 encoded PEM format. The file extension must be .pem and have no other periods (.) in the file name.
[See image.](#seeimage40)
- **IdP SAML Certificate Expiration Date**: Displays the expiration date for the SAML certificate of the IdP. You see this field if the certificate is about to expire or has expired. A **Caution **icon appears if the certificate expires within 30 days.
- **Vendor**: Choose the vendor of the IdP.
- **Default IdP**: Displays if this IdP is **Enabled** or **Disabled** as the default IdP. You can only have one default IdP. The first IdP added becomes the default IdP. Any additional IdPs will be **Disabled** as the default, and you won't be able to modify this field. To change the default IdP, see [About Identity Providers](/zia/about-identity-providers).
- **Locations**: Select the [locations](/zia/about-locations) to map to this IdP. You can also search for a location. Any unselected locations are mapped to the default IdP. This field is set to **Any** for the default IdP, and you can't modify it.
- **Authentication Domains**: Select the domains to map to this IdP. This allows the Zscaler service to display the correct IdP to authenticate an incoming user. Any unselected domains will be mapped to the default IdP. This field is set to **Any** for the default IdP, and you can't modify it. Apart from the default IdP, any additional IdPs must be mapped to at least one domain.
- **Sign SAML Request**: Enable if the IdP expects the SAML request to be signed. The following fields appear:
- **Signature Algorithm**: Choose whether to sign the SAML request with a **SHA-1 (160-bit)** hashing algorithm or with a **SHA-2 (256-bit)** hashing algorithm. If you are reconfiguring SAML because the certificate expired, Zscaler recommends that you select the certificate with the later expiration date.
- **Request Signing SAML Certificate**: Choose which certificate you want to use for signing SAML requests. Zscaler recommends choosing the one with the longest validation period.
- **SP SAML Certificate Expiration Date**: Displays the expiration date for the SAML certificate of Zscaler, your SP. You see this field if the certificate is about to expire or has expired. A **Caution** icon appears if the certificate expires within 30 days.
- []**SP SAML Certificate**: Download the Zscaler certificate that you are going to upload to your IdP when you configure it.
- []**SP Metadata**: Download the metadata of the Zscaler service. The metadata advertises the Zscaler SAML capabilities and is used for auto-configuration. Some IdPs require importing the metadata to configure the Zscaler service as a SP.
-
**Enable SAML Auto-Provisioning**: Enable SAML for provisioning users on the Zscaler service. If you're using Active Directory or OpenLDAP user repositories, SAML auto-provisioning is supported for only one IdP. After enabling SAML auto-provisioning, the following fields appear:
- **User Display Name Attribute**: Enter the SAML attribute that maps to the username. Typically, it's `displayName`. This is case-sensitive.
- **Group Name Attribute**:** **Enter the SAML attribute that maps to the group name. Typically, it's `memberOf`. This is case-sensitive.
- **Department Name Attribute**: Enter the SAML attribute that maps to the department name. Typically, it's `department`. This is case-sensitive.
Zscaler recommends using SCIM to provision users. If you want to use SCIM-based provisioning, disable this option and select **Enable SCIM Provisioning**.
- **Enable SCIM Provisioning**: You can't enable this setting at this time. To enable SCIM-based provisioning for users, you must add this IdP to establish its unique ID or identifier. The ID or identifier is included in the SCIM base URL. To learn more, see [Configuring SCIM](/zia/configuring-scim).
- **Device Trust Attribute**: Enter the SAML attribute that maps to the trust attribute defined on your IdP. This is used for identifying managed devices. This field is case-sensitive.
- **Device Trust Attribute Value**: Enter the SAML attribute value that maps to the trust attribute value defined on your IdP for managed devices. This field is case-sensitive.
[See image.](#seeimage-4)
- Click **Save** to exit the window.
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![The Add another SAML IdP for a subset of users or locations in the What do you want to do? window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/adding-identity-providers/ZIA-What-do-you-want-to-do-window.png?1623972772)
[]![Screenshot highlighting the Upload button in the IdP SAML Certificate window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/adding-identity-providers/ZIA-IdP-SAML-Certificate-window-6_1.png)
[]![Screenshot of the configured Add Identity Provider window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/adding-identity-providers-draft/Identity%20Provider%20Configuration.png)