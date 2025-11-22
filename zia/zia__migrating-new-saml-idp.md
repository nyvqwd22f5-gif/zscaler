# Migrating to a New SAML IdP
Source: https://help.zscaler.com/zia/migrating-new-saml-idp
PDF: https://help.zscaler.com/pdf/com/en/1402196.pdf

This guide contains information on how to migrate from one identity provider (IdP) to another in the ZIA Admin Portal. Zscaler recommends editing the existing [identity provider](/zia/about-identity-providers) (IdP) to migrate to a new IdP. Adding a new IdP for migration can duplicate groups and departments, and your existing policies might no longer apply.
Prerequisites
Make sure the following prerequisites are met:
- Ensure that the same user data (groups, users, and departments) are present in both IdPs.
- Ensure that SAML and SCIM mapping attributes match in both IdPs.
-
For SAML, ensure that the NameID mapping is defined the same way in both IdPs. If you define NameID with the email or UPN attribute, ensure that the expression is the same in both IdPs. For example, see the following SAML assertion:
`<saml:Attribute Name="NameID" Format="urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress">
<saml:AttributeValue>user@example.com</saml:AttributeValue>
</saml:Attribute>`
-
For SCIM, ensure that the userName mapping is defined the same way in both IdPs. If you define userName with the email or UPN attribute, ensure that the expression is the same in both IdPs. For example, see the following payload:
`json
{
"schemas": ["urn:ietf:params:scim:schemas:core:2.0:User"],
"userName": "user@example.com",
...
}`
Migrating to a New IdP
To migrate to a new IdP:
- Go to **Administration **>** Authentication Settings**.
- Click the **Identity Providers** tab.
-
Click **Add IdP**.
The **What do you want to do?** window appears.
-
In the **What do you want to do?** window:
- Choose **Migrate to a new SAML IdP**.
- For **Choose the SAML IdP to Migrate**, choose the existing SAML IdP you want to migrate to a new IdP.
- Click **Next**.
[See image.](#seeimage-1)
The **Add IdP** window appears.
-
In the **Add IdP** window:
- **SAML Portal URL**: Enter the new SSO URL of the SAML portal to which users are sent for authentication.
- **IdP SAML Certificate**: Upload the new SAML certificate that is used to verify the digital signature of the IdP. This is the certificate you downloaded from your IdP. The certificate must be in base-64 encoded PEM format. The file extension must be .pem and have no other periods (.) in the file name.
- **Vendor**: Choose the new vendor of the IdP.
[See image.](#seeimage-2)
To learn more about these fields, see [Adding Identity Providers](/zia/adding-identity-providers).
- Click **Save** to exit the window.
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
- [Configure SAML](/zia/configuring-saml#configuretheidp) and enable SCIM on the new IdP.
Verify that values for users, groups, and departments are the same in both IdPs to avoid any effects on ZIA policies based on users, groups, or departments.
-
Start SCIM provisioning on your new IdP to sync all user data from the new IdP to Zscaler.
Ensure that the new IdP is running without error before disabling the old IdP.
Validating Migration
To validate that the IdP migration is successful:
- Verify that users are able to authenticate by having them log out and back in to Zscaler Client Connector.
- Verify that existing policies configured with users, groups, and departments are working.
Reverting to the Previous IdP
To revert to a previously configured IdP:
- Edit the IdP you have configured in the ZIA Admin Portal and enter the details for the previously configured IdP.
- Perform a SCIM sync in the IdP.
- Verify that users can log in and that policies are working as expected.
[]![Image of the What do you want to do? window](/downloads/tech-pubs-drafts/zia-draft-articles/idp-migration-guide-doc-51791/ZIA-IdP-What-do-you-want-to-do-Window.png)
[]![Image of the Edit IdP window](/downloads/tech-pubs-drafts/zia-draft-articles/idp-migration-guide-doc-51791/ZIA-Edit-IdP-Migration.png)