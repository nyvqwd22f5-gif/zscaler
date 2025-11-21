# Configuring Okta SSO
Source: https://help.zscaler.com/uvm/configuring-okta-sso
PDF: https://help.zscaler.com/pdf/com/en/1527936.pdf

You can configure Okta single sign-on (SSO) as the authentication method for the Zscaler Security Operations (SecOps) platform, allowing users to sign in through your Okta SSO provider, instead of using a username and password. To do this, you can specify a domain, and users with email addresses matching that domain are redirected to authenticate through Okta. Each user must have an account with the same email address in both the platform and in Okta. After SSO is enabled for a domain, it becomes the only authentication method for the platform.
To configure Okta SSO, complete the following steps:
- [Step 1: Generate SAML Details](#generate-saml-details)
- [Step 2: Create a Bookmark App](#create-bookmark-app)
- [Step 3: Create an App Integration](#create-app-integration)
- [Step 4: Share Metadata With Zscaler](#share-metadata)
[]To set up SSO account authentication, you must generate a SAML Entity ID and Reply URL within the SecOps platform. To learn more, see [Generating SAML Details](/uvm/generating-saml-details).
[]The SecOps platform doesn't natively support identity provider (IdP)-initiated login. Instead, implement the following process using a Bookmark app that redirects to app.avalor.io.
To configure a Bookmark app:
- Sign in to the Okta Admin Center.
- Go to the **Applications** page and click **Browse App Catalog.**
-
Search for and add **Bookmark App**.
[See image.](#search-bookmark-app)
- In the **General Settings **section:
- **Application label**: Enter a name for the Bookmark app.
- **URL**: Enter `https://app.avalor.io?domain=``<Your Org Domain>`, replacing `<Your Org Domain>` with your actual organization domain.
-
**Application Visibility**: Leave the checkbox unselected so the **Bookmark **app isn't hidden.
[See image.](#general-settings-app-visibility)
- Click **Done**.
-
Click the **Edit** icon on the logo to add Zscaler's logo: [Download Logo](/downloads/uvm/administration/account-management/admin-configuration-and-deployment/configuring-okta-sso/LOGO.png)
[See image.](#add-zscaler-logo)
- Click **Done**.
[]**![5688aac9-d9ce-490c-a036-8102b5a13c7b.png](/downloads/uvm/account-management/sso/okta-sso/5688aac9-d9ce-490c-a036-8102b5a13c7b.png)
**
[]**![1531bf87-3140-459c-8848-9c1299c93916.png](/downloads/uvm/account-management/sso/okta-sso/1531bf87-3140-459c-8848-9c1299c93916.png)
**
[]**![5ed6b43a-a684-4309-a10f-e1932f135380.png](/downloads/uvm/account-management/sso/okta-sso/5ed6b43a-a684-4309-a10f-e1932f135380.png)
**
[]To enable SAML-based authentication with Okta, you need to create and configure a new app integration.
To create an app integration:
- Sign in to the Okta Admin Console.
- In the navigation menu, expand **Applications**, and then select **Applications**.
- Click **Create App Integration**.
-
In the **Create a New Application Integration** window, select **SAML 2.0 **as the **Sign on method**, and then click **Create**.
[See image.](#create-new-app-integration-saml2)
- On the **Create SAML Integration** page:
- On the **General Settings **tab:
- **App name**: Enter a name for the app integration.
- **App Visibility**: Select **Do not display application icon to users**.
- Click **Next**.
- On the **Configure SAML **tab:
- **Single sign on URL**: Paste the **Reply URL** copied from Zscaler.
- **Audience URI (SP Entity ID)**: Paste the **Entity ID** copied from Zscaler.
- **Name ID format**: Enter `EmailAddress`.
- **Application username**: Select **Okta username**.
- In the **Attribute Statements (optional)** section:
- **Name:** Enter `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress`.
- **Value**: Enter `user.email`.
[See image.](#attribute-statements)
- Click **Next**.
- On the **Feedback** tab, select **I'm an Okta customer adding an internal app**.
[See image.](#feedback-tab)
- Click **Finish**.
- Assign users or groups to authenticate using Okta:
- Go to the **Assignments** tab of the application you added.
- Click **Assign**.
- Select **Assign to People **or **Assign to Groups**.
- Enter the people or groups that you want to authenticate with the Okta IdP.
- Click **Assign**.
- Verify the attributes, and click **Save and Go Back**.
- Click **Done**.
[]**![29040f2a-a2e5-4452-8299-eb1854ab5d11.png](/downloads/uvm/account-management/sso/okta-sso/29040f2a-a2e5-4452-8299-eb1854ab5d11.png)
**
[]![0a6687e5-c58c-4421-b8a0-fb827a66a6b6.png](/downloads/uvm/account-management/sso/okta-sso/0a6687e5-c58c-4421-b8a0-fb827a66a6b6.png)
[]![006eb831-b275-436b-876f-e516d92c308e.png](/downloads/uvm/account-management/sso/okta-sso/006eb831-b275-436b-876f-e516d92c308e.png)
[]After creating a Bookmark App and an app integration, share XML metadata with your Zscaler Account team. To learn more, refer to the [Okta documentation](https://support.okta.com/help/s/article/Location-to-download-Okta-IDP-XML-metadata-for-a-SAML-app-in-the-new-Admin-User-Interface?language=en_US).
To retrieve the XML metadata:
- In the Okta console, click the **Sign On** tab of the SAML application.
- Scroll down and click **View SAML setup instructions**.
In the new tab that opens, all the required values are displayed.
-
Copy the metadata from the **Optional** section.
[See image.](#okta-metadata-xml)
To share metadata with Zscaler:
- In the SecOps platform, click the **Profile** menu on the top right of the page and select **Account Settings**.
-
In the **Authenticate** section, paste the XML metadata into the **SAML XML MetaData **field.
If the Authenticate section is not visible, share the XML metadata with your Zscaler Account team.
[See image.](#saml-xml-metadata-field)
While a metadata URL is also supported, Zscaler recommends pasting the XML metadata directly.
![Okta Metadata XML](/downloads/uvm/administration/account-management/admin-configuration-and-deployment/configuring-ping-federate-sso/okta%20metadata%20xml.png)
[]
[]**![SAML XML Metadata field](/downloads/uvm/account-management/sso/okta-sso/mceclip0.png)
**