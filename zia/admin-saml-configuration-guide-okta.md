# Admin SAML Configuration Guide for Okta
Source: https://help.zscaler.com/zia/admin-saml-configuration-guide-okta
PDF: https://help.zscaler.com/pdf/com/en/1399701.pdf

This guide illustrates how to configure Okta as the identity provider for the Zscaler service and use [SAML single sign-on (SSO) for admins](/zia/about-saml-single-sign-admins). Refer to the Okta documentation for additional information about the steps in the guide.
Prerequisites
Ensure you have the following before configuring Okta:
- Okta account with admin privileges
- Admin accounts created for your organization's admins. To learn more, see [Adding Admins](/zia/adding-admins).
Configuring Admin SAML SSO in Okta
To configure Okta as the IdP for the Zscaler service and use SAML SSO for admins:
- Go the **Applications** tab and click **Add Application**.
- Enter** SAML Service Provider** in the **Search** field, and then click **Add**.
[See image.](#seeimage2)
- In **General Settings**, specify the display name for the Zscaler service in **Application Label **and click **Next**.
[See image.](#seeimage3)
- In **Sign-On Options**, click **View Setup Instructions**.
[See image.](#seeimage4)
- From the dialog that opens, download** **the** Identity Provider Certificate **by clicking the provided link.
[See image.](#seeimage5)
- The file downloaded will be named "okta.cert". Rename the certificate to "okta.cer".
- In **Assign SAML Service Provider to People**, enter the admin's name (Person) and email address (Username), and click **Done**.
[See image.](#seeimage7)
The admin can now access the ZIA Admin Portal through Okta by clicking on the configured Zscaler application for Admin SAML.
[See image.](#seeimage0)
[]![Screenshot illustrating how to add the SAML Service Provider app](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/configuring-okta-admin-saml-single-sign/add_saml_service_provider.png)
[]![Screenshot of the General Settings tab with name added in the Application label](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/configuring-okta-admin-saml-single-sign/choose_display_name_in_application_label.png)
[]![Screenshot of the Sign-On Options page with the View Setup Instructions highlighted in a red box](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/configuring-okta-admin-saml-single-sign/view_setup_instructions.png)
[]![Screenshot of dialogue box with the link to download the Identity Provider Certificate highlighted](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/configuring-okta-admin-saml-single-sign/download_the_identity_provider_certificate.png)
[]![Screenshot of the Assign SAML Service Provider to People tab with Done button highlighted in a red box](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/configuring-okta-admin-saml-single-sign/assign_saml_service_provider_to_people.png)
[]![Screenshot of the Okta app with the admin SAML app now available](/downloads/zia/documentation-knowledgebase/managing-admins/about-saml-single-sign-sso-admins/configuring-okta-admin-saml-single-sign/admin_saml_available_on_okta.png)