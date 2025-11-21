# Configuring Microsoft Entra ID SSO
Source: https://help.zscaler.com/uvm/configuring-entra-id-sso
PDF: https://help.zscaler.com/pdf/com/en/1527931.pdf

You can configure Microsoft Entra ID (formerly Azure AD) single sign-on (SSO) as the authentication method for the Zscaler Security Operations (SecOps) platform, allowing users to sign in through the Microsoft Entra ID SSO provider, instead of using a username and password. To do this, you can specify a domain, and users with email addresses matching that domain are redirected to authenticate through Microsoft Entra ID. Each user must have an account with the same email address in both the platform and Microsoft Entra ID. After SSO is enabled for a domain, it becomes the only authentication method for the platform.
To configure Microsoft Entra ID SSO, complete the following steps:
- [Step 1: Generate SAML Details](#generate-saml-details)
- [Step 2: Register an Application in Microsoft Entra ID](#register-app-azure-ad)
- [Step 3: Share Metadata With Zscaler](#share-metadata)
[]To set up SSO account authentication, you must generate a SAML Entity ID and Reply URL within the SecOps platform. To learn more, see [Generating SAML Details](/uvm/generating-saml-details).
[]After generating SAML details (Entity ID and Reply URL), you can proceed to registering a Microsoft Entra ID application and assigning users to the new application.
To register a Microsoft Entra ID application:
- Sign in to the Azure portal.
- Select the **Microsoft Entra ID **service.
- In the left-side navigation, go to **Manage** > **Enterprise applications**.
- Click **New application**.
-
On the **Browse Microsoft Entra Gallery** page, click** Create your own application**.
The **Create your own application** drawer appears.
- In the **Create your own application** drawer:
- **Name**: Enter a name for the application.
- **What are you looking to do with your application?**: Select **Integrate any other application you don’t find in the gallery (Non-gallery)**.
- Click **Create** to complete the initial app registration.
- The app registration's **Overview** page appears.
-
In the **Getting Started** section, locate the** Set up single sign on** tile and click **Get Started**.
The **Single sign-on** page appears.
-
On the **Single sign-on** page, select **SAML **as the single sign-on method.
The **SAML-based Sign-on** page appears.
- On the **Basic SAML Configuration** tile, click **Edit**.
[See image.](#edit-basic-saml-config)
- In the **Basic SAML Configuration** drawer:
- **Identifier (Entity ID)**: Click **Add Identifier** and paste the **Entity ID** copied from Zscaler.
- **Reply URL (Assertion Consumer Service URL)**: Click **Add reply URL** and paste the **Reply URL** copied from Zscaler.
- **Sign on URL**: (Optional) Enter `https://app.avalor.io`.
[See image.](#basic-saml-config-drawer)
- Click **Save**.
- On the **Attributes & Claims** tile, click **Edit**.
- Click **Add a group claim**.
- In the **Group Claims** drawer:
- Select **Groups assigned to the application**.
- **Source Attribute**: Select **Group ID **from the drop-down menu.
[See image.](#group-claims-drawer)
- Click **Save**.
- Close the** Attributes & Claims** page to return to the **Set up Single Sign-on with SAML **page.
After registering the Microsoft Entra ID application, you can assign users to the new app.
To assign users to the app:
- In the left-side navigation, click **Users and groups.**
[See image.](#users-and-groups)
- Click **Add user/group**.
- Add the relevant user in your organization.
- Click **Assign**.
[]**![9f1558a7-a7f2-4ccf-b5a7-6815230b2bd2.png](/downloads/uvm/account-management/sso/azure-ad-sso/9f1558a7-a7f2-4ccf-b5a7-6815230b2bd2.png)
**
[]**![34e443fe-e480-4d6e-97bd-15e25d74f345.png](/downloads/uvm/account-management/sso/azure-ad-sso/34e443fe-e480-4d6e-97bd-15e25d74f345.png)
**
[]**![b1b4984e-7382-4585-9531-78950c025152.png](/downloads/uvm/account-management/sso/azure-ad-sso/b1b4984e-7382-4585-9531-78950c025152.png)
**
[]**![74f74bb3-912f-498f-a99f-2716b37c4e44.png](/downloads/uvm/account-management/sso/azure-ad-sso/74f74bb3-912f-498f-a99f-2716b37c4e44.png)
**
[]After creating a Microsoft Entra ID app, share XML metadata with your Zscaler Account team.
To retrieve the XML metadata:
- Sign in to the Azure portal, and select the **Microsoft Entra ID **service.
- Open the application you created.
-
In the left-side navigation, select **Single sign-on**.
[See image.](#single-sign-on-left-nav)
-
Scroll down to the **SAML Signing Certificate** section and copy the **App Federation Metadata URL**.
[See image.](#app-federation-metadata-url)
To share metadata with Zscaler:
- In the SecOps platform, click the **Profile** menu on the top right of the page and select **Account Settings**.
-
In the **Authenticate** section, paste the XML metadata into the **SAML XML MetaData **field.
If the Authenticate section is not visible, share the XML metadata with your Zscaler Account team.
[See image.](#saml-xml-metadata-field)
While a metadata URL is also supported, Zscaler recommends pasting the XML metadata directly.
[]**![4251fe2c-050b-49c0-9956-2cfacaf22920.png](/downloads/uvm/account-management/sso/azure-ad-sso/4251fe2c-050b-49c0-9956-2cfacaf22920.png)
**
[]**![88ecd39c-252c-4c01-a34d-76d1adcf67d2.png](/downloads/uvm/account-management/sso/azure-ad-sso/88ecd39c-252c-4c01-a34d-76d1adcf67d2.png)
**
[]**![09fe16a3-2f70-4499-bd30-e06e4571bac7.png](/downloads/uvm/account-management/sso/azure-ad-sso/09fe16a3-2f70-4499-bd30-e06e4571bac7.png)
**