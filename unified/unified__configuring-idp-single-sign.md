# Configuring an IdP for Single Sign-On
Source: https://help.zscaler.com/unified/configuring-idp-single-sign
PDF: https://help.zscaler.com/pdf/com/en/1491106.pdf

Within the Admin Portal, you can add up to 10 IdP configurations for single sign-on (SSO). For a complete list of ranges and limitations per feature, see [Ranges & Limitations](/unified/ranges-limitations#private-applications).
To specify Private Applications as a service provider (SP) for your identity provider (IdP):
- [][][1. Set up your IdP and specify Private Applications as the SP.](#Collapse1)
- [][][][2. Add an IdP configuration in the Admin Portal.](#Collapse2)
- []3. Verify that your IdP configuration is working properly.
- [Import SAML Attributes from the IdP to ZPA](#VerifyIdP_UserSSO)
- [Verify Admin SSO into ZPA](#VerifyIdP_AdminSSO)
[]Before you can add an IdP configuration using the Admin Portal, you must have the IdP in place for your organization.
The following configuration guides provide instructions on how to configure specific IdPs for SSO, but any IdP is supported. If you don't see your IdP listed below, refer to these guides as examples:
- [Configuration Guide for Gemalto SafeNet Authentication Manager](/unified/configuration-guide-gemalto-safenet-authentication-manager)
- [Configuration Guide for Microsoft Active Directory Federation Services (ADFS) 2.0 and 3.0](/unified/configuration-guide-microsoft-adfs-2-0-and-3-0)
- [Configuration Guide for Microsoft Azure Active Directory (AD)](/unified/configuration-guide-microsoft-azure-ad)
- [Configuration Guide for Okta](/unified/configuration-guide-okta)
- [Configuration Guide for Onelogin](/unified/configuration-guide-onelogin)
- [Configuration Guide for Ping Identity PingOne](/unified/configuration-guide-ping-identity-pingone)
Prior to configuring your IdP, Zscaler recommends reading [IdP Configuration Best Practices](/unified/idp-configuration-best-practices).
[]If you want to use the same IdP for both admin and user SSO, you must add a configuration for each. You can also use different IdPs for admin and user SSO, if desired. If you plan to use the IdP for [SCIM](/unified/about-scim) too, SCIM is only available for user SSO.
The SP metadata and certificate information is specific to your IdP and the **Single Sign-On** selection made in [step 2c](#IdP_BothSSO). When you upload the files, or manually add the metadata to your IdP, it parses the information.
If you update an IdP certificate, this change triggers an Authentication Error message in the Zscaler Client Connector for users and prevents access to your apps. Your users need to reauthenticate in Zscaler Client Connector to regain access to the apps.
Zscaler recommends disabling this setting only after SAML attributes are removed as policy criteria in a rule. If this setting is disabled and a policy rule has SAML attribute criteria, the policy rule might not be evaluated. To learn more, see [Configuring Access Policies](/unified/configuring-access-policies#samlscimattribute), [Configuring Timeout Policies](/unified/configuring-client-forwarding-policies#samlscimattribute), and [Configuring Timeout Policies](/unified/configuring-timeout-policies#samlscimattribute).
- Go to **Administration **>** Identity **> **Private Access **> **IDP Configuration**.
The IdP Configuration page is hidden if you are subscribed to ZIdentity and have this feature enabled for your tenant. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
-
Click **Add IdP Configuration**.
IdP configurations that are managed by Zscaler are read only and cannot be configured, edited, or deleted.
- In the **Add IdP Configuration** window, on the **IdP Information** tab:
- **Name**: Enter a name for your organization's IdP. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- []**Single Sign-On**: Select **User** or **Admin**.
- **Use with Arbitrary Domains**: Enabling arbitrary domains allows third-party users to access single sign-on to use any authentication domain without needing to add it to the list of selected domains. This is helpful for third-party users with clientless access. Clientless access allows users secure access via browser-based access, Privileged Remote Access, and Cloud Browser Isolation. **Single Sign-On** must be set to **User** for this option to appear. If an arbitrary domain-enabled IdP configuration already exists, then this option is not available unless you delete or disable the existing arbitrary domain-enabled IdP configuration. This option does not work with Zscaler Client Connector.
Zscaler recommends you be aware of the following conditions when configuring an IdP with arbitrary domains:
- You cannot enable **Use with Arbitrary Domains** with Zscaler Client Connector. If a single IdP is created without a domain selected and **Use with Arbitrary Domains** is enabled, the Zscaler Client Connector login fails. A domain must be configured to at least one IdP in the account to use this feature.
- If a single IdP is created in the ZPA Admin Portal, the **Use with Arbitrary Domains** option is not available for some tenants. To enable **Use with Arbitrary Domains**, you need to configure more than one IdP.
- The **Use with Arbitrary Domains** option cannot be disabled on an IdP if the IdP is configured for [emergency access](/unified/configuring-emergency-access).
- **Domains**: Choose the authentication domains that you want to associate to this IdP, and click **Done**. The domains shown here are the [primary and secondary authentication domains](/unified/configuring-authentication-settings) configured for your organization. A domain can only be associated to one IdP. Click **Select All** to include all domains, or **Clear All** to remove any selections.
[See image.](#IdPConfig_Step1)
- Click **Next**.
- On the** SP Metadata** tab, to complete provisioning for SSO on your IdP:
- If your IdP provides an option to upload an SP metadata file, under **Service Provider Metadata**, click **Download Metadata**. If your IdP does not provide the option to upload a metadata file, or if you prefer to configure this manually, click the **Copy** icon next to **Service Provider URL** and **Service Provider Entity ID**.
- Under **Service Provider Certificate**, click **Download Certificate**.
[See image.](#IdPConfig_Step2)
- Click **Next**. []You can click **Pause **if you need to upload or manually add the SP information to your IdP before continuing. If you click **Pause**, you can click the **Resume **icon (![Resume Button within ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/midp-about-idp-new/zpa-resumebutton.png)
) on the **IdP Configuration** page to continue.
- On the** Create IdP** tab:
- **General Information**:
- **Name**: This is the name you entered in [step 2c](#IdP_BothSSO).
- **Use with Arbitrary Domains**: This is the option mentioned in [step 2c](#IdP_BothSSO).
- **Authentication Domains**: These are the authentication domains you chose in [step 2c](#IdP_BothSSO).
- **SAML Configuration**:
- If your IdP provides a metadata file, click **Select File** next to **IdP Metadata File** to upload it. After uploading the metadata file, the window auto-populates with the proper information. If your IdP does not provide a metadata file, or if you prefer to add this information manually, make sure that the following fields are completed:
- **Single Sign-On URL**: Enter the URL of the IdP portal to which users are directed for authentication. If you want users to authenticate from the internet, ensure that it is publicly resolvable. Additionally, ensure that it is protected using HTTPS.
- **IdP Entity ID**: Enter the entity ID for your IdP.
- **IdP Certificate**: You must download this certificate from your IdP, and it must be uploaded in base-64 encoded PEM format. Click **Select File** next to **IdP Certificate** to upload it. After uploading the certificate, ZPA automatically reads the file and the field auto-populates within the window. IdP certificate information such as **Common Name**, **Serial Number**, **Created On**, and **Expired On** are displayed. This information is also displayed on the **IdP Configuration** page.
- **Status**: Make sure that the IdP configuration is **Enabled**. After saving, you can change the status to **Disabled** at any time by [editing the configuration](/unified/editing-idp-configuration).
- **ZPA (SP) SAML Request**: Select whether you want the SP to send a **Signed **or **Unsigned **SAML request towards the IdP.
- **HTTP-Redirect**: If you need to send the SAML response as an HTTP redirect, make sure that this is set to **Enabled**.
- **Force Authentication**: Enable this option, if you want users for that specific IdP to re-enter their login credentials at the time of reauthentication, regardless of any session state/cookie for SAML IdP. The default is set to **Disabled**.
- **Login Hint**: When enabled, the username of the admin or user is sent in the authentication request to the IdP and can be prepopulated on the sign-in page of the external IdP. By default, Enabled is selected.
- **User IdP Certificate Rotation**: (Optional) Select a different service provider certificate to use with the IdP. You might also need to update the configuration of the IdP. To learn more, see [Managing a Service Provider Certificate Rotation](/unified/managing-service-provider-certificate-rotation).
This field might also show as **Admin IdP Certificate Rotation** if you selected **Admin** for **Single Sign-On** in [step 2c](#IdP_BothSSO).
When [editing an IdP](/unified/editing-idp-configuration), this field might show as **IdP Certificate Rotation** if the original IdP was configured to use **Both** (i.e., admin and user SSO) when that option was available.
- **SAML Attributes for Policy**: Select whether you want to allow SAML attributes from this IdP to be used when configuring [Access Policies](/unified/configuring-access-policies), [Client Forwarding Policies](/unified/configuring-client-forwarding-policies), and [Timeout Policies](/unified/configuring-timeout-policies). You must enable this setting to process SAML attributes in policy rules.
- []**SCIM Configuration**:
- **SCIM Sync**: Enabling [SCIM](/unified/about-scim) allows you to quickly remove users when a user is disabled or deleted in your user directory and to enforce policies based on SCIM attributes and SCIM groups. Zscaler recommends not enabling SCIM at this point when setting up an IdP. To complete the SCIM enablement process, see [Enabling SCIM for Identity Management](/unified/enabling-scim-identity-management).
- **SCIM Attributes for Policy**: Select whether you want to allow SCIM attributes and SCIM groups from this IdP to be used when configuring [Access Policies](/unified/configuring-access-policies), [Client Forwarding Policies](/unified/configuring-client-forwarding-policies), and [Timeout Policies](/unified/configuring-timeout-policies). You must enable this setting to process SCIM attributes and SCIM groups in policy rules. This setting only applies if **SCIM Sync** is set to enabled as well.
After you first enable **SAML Attributes for Policy**, a user is required to reauthenticate in Zscaler Client Connector. Only policies with SCIM criteria are evaluated for this user after the user successfully reauthenticates.
Zscaler recommends disabling this setting only after SCIM attributes and SCIM groups are removed as policy criteria in a rule. If this setting is disabled and a policy rule has SCIM attribute or SCIM group criteria, the policy rule might not be evaluated. To learn more, see [Configuring Access Policies](/unified/configuring-access-policies#samlscimattribute), [Configuring Timeout Policies](/unified/configuring-client-forwarding-policies#samlscimattribute), and [Configuring Timeout Policies](/unified/configuring-timeout-policies#samlscimattribute).
- Click **Save**.
[See image.](#IdPConfig_Step3)
[]To verify the IdP configuration for user SSO, try [importing your SAML attributes](/unified/importing-saml-attributes):
- Go to **Administration **>** Identity **> **Private Access **> **IDP Configuration**
- On the **IdP Configuration** page, expand the configuration for the IdP you want to import SAML attributes from.
- Click **Import**.
![Expanded IdP Configuration with Import SAML Attributes Option](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/configuring-idp-single-sign/Import%20update.png)
If Private Applications was correctly configured as your SP, the link redirects you to the SSO login page provided by your IdP.
To test IdP access outside of the Admin Portal, enter the following URL into a browser, where `<domain name>` is the authentication domain:
https://samlsp.private.zscaler.com/auth/v2/login?domain=<domain name>&ssotype=test
For example:
https://samlsp.private.zscaler.com/auth/v2/login?domain=mockcompany.com&ssotype=test
[]To verify the IdP configuration for admin SSO:
- Go to **Administration **>** Private Access **>** Identity **> **IDP Configuration **> **IDP Configuration**.
- On the **IdP Configuration** page, expand the IdP configuration you want to test. For the IdP, make sure that the NameID in the SAML assertion is set to the username of the admin.
- Under **Verify Single Sign-On**, choose the authentication domains you want to verify the account on. These are the **Domains** you specified in [step 2c](#IdP_BothSSO).
- Click **Verify**.
![Expanded IdP Configuration with Verify Single Sign-On Option](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/midp-about-idp-new/zpa-verifyssobutton.png)
If Zscaler was correctly configured as your SP, the link redirects you to the SSO login page provided by your IdP.
To test IdP access outside of the Admin Portal, enter the following URL into a browser, where `<domain name>` is the authentication domain:
https://adminsamlsp.private.zscaler.com/auth/v2/login?domain=<domain name>&ssotype=test
For example:
https://adminsamlsp.private.zscaler.com/auth/v2/login?domain=mockcompany.com&ssotype=test
[]![Add IdP Configuration window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/configuring-idp-single-sign/Configuring%20an%20IdP%20for%20Single%20Sign%20On.png)
[]![Add IdP Configuration window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/midp-about-idp-new/zpa-addidp-step2_0.png)
[]![Add IdP Configuration window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/configuring-idp-single-sign/zpa-add-idp-configuration-window.png)