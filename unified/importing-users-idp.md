# Importing Users from Your Identity Provider
Source: https://help.zscaler.com/unified/importing-users-idp
PDF: https://help.zscaler.com/pdf/com/en/1486911.pdf

If you manage users with an identity provider (IdP), Zscaler can import those users directly. You'll need to make sure your IdP is set up for SAML authentication and SCIM provisioning. You can also [import users from a CSV file](/unified/uploading-users-csv-file) and [add users manually](/unified/adding-users-manually).
To import users from your IdP:
-
On the Users page, click **Connect IdP** at the top of the page.
[See image.](#connect-idp-image)
-
Under **Select Identity Provider**, select your IdP and click **Next**.
Commonly used IdPs are shown at the top, or you can select one from the drop-down menu.
- Under **Link Your <**IdP Name>** Identities**, enter the following under **General Details**:
- **Name**: A unique name for this IdP connection (e.g., "Corp IdP Connection").
- **Domain**: Select the domain associated with the tenant for this connection from the drop-down list. This list is generated from the domains associated with your ZIdentity account.
- **Login Id Attribute**: Enter the attribute from your IdP that will be used as the ZIdentity login ID.
- Select the protocol for your IdP, either **OIDC **or **SAML** then complete the information to retrieve the metadata:
- [OIDC Connection](#oidc)
- [SAML Connection](#saml)
- Click **Fetch **next to the **Metadata URL** box. Zscaler retrieves the metadata information required to connect your users. Depending on your protocol:
- [OIDC Connection](#oidc-meta)
- [SAML Connection](#saml-meta)
- Under **Provisioning**, click **Generate Token** to generate a bearer token, which is used by the IdP to connect to Zscaler. Click the toggle if you want to skip this step and disable SCIM provisioning. To learn more about SCIM provisioning, see* *[Enabling SCIM for Identity Management](/unified/enabling-scim-identity-management).
- Click **Finish** to link to your IdP and import your users.
- When users are successfully imported, the **Users **page appears. From this page, you can add more users manually, edit them, or assign them to different roles. To learn more, see [Editing Newly Onboarded Users](/unified/editing-newly-onboarded-users).
If you want to remove all imported users from Zscaler, click the **Disconnect **<IdP Name> link at the top of the page. This action cannot be undone.
To learn more about SAML and OIDC configurations, see [IdP Configuration](/unified/administration/zidentity/idp-configuration).
[]
- **Redirect URI**: Filled in automatically. Your unique URI to log into Zscaler.
- **Client ID**: Enter ID to log in to the IdP.
- **Client Secret**: Enter the secret associated with the client ID.
- **Metadata URL**: Enter the URL to retrieve metadata on your IdP.
[]
- **SP Entity ID**: Filled in automatically. Your unique entity identifier on Zscaler as the service provider.
- **SP URL:** Filled in automatically. Your unique URL to access Zscaler as the service provider.
- **Metadata URL**: Enter the URL to retrieve metadata on your IdP.
[]
Click **Next **to continue.
[]
The following IdP information is displayed:
- **IdP Entity URL**: The unique URL for this IdP entity.
- **IdP Single Sign-On URL**: The SSO URL to which users are sent for authentication for this IdP.
- **IdP Certificate**: The certificate used to verify the digital signature of the IdP.
Review the information and click **Next **to continue.
[]![Devices Discovered widget on the Networking dashboard](/downloads/unified/getting-started-zscaler/importing-users-from-idp/connect-idp.png)