# Configuring PingFederate SSO
Source: https://help.zscaler.com/uvm/configuring-ping-federate-sso
PDF: https://help.zscaler.com/pdf/com/en/1527916.pdf

You can configure PingFederate single sign-on (SSO) as the authentication method for the Zscaler Security Operations (SecOps) platform, allowing users to sign in through your PingFederate SSO provider, instead of using a username and password. To do this, you can specify a domain, and users with email addresses matching that domain are redirected to authenticate through PingFederate. Each user must have an account with the same email address in both the platform and PingFederate. After SSO is enabled for a domain, it becomes the only authentication method for the platform.
To configure PingFederate SSO, complete the following steps:
- [Step 1: Generate SAML Details](#generate-saml-details)
- [Step 2: Register an Application in PingFederate](#register-app-ping-federate)
- [Step 3: Share Metadata With Zscaler](#share-metadata)
[]To set up SSO account authentication, you must generate a SAML Entity ID and Reply URL within the SecOps platform. To learn more, see [Generating SAML Details](/uvm/generating-saml-details).
[]After generating SAML details (Entity ID and Reply URL), you can register a PingFederate application. The app registration process assumes you already have an IdP Adapter in place. To learn more, refer to the [PingFederate documentation](https://docs.pingidentity.com/integrations/azure/azure_ad_and_office_365_integration_guide/pf_azuread_office365_integration_create_an_idp_adapter.html).
To register a PingFederate application:
- Sign in to the PingFederate Admin console.
- Go to **Identity Provider** > **SP Connections**.
-
Click **Create Connection**.
[See image.](#create-connection-button)
-
On the **Connection Template** step, select **DO NOT USE A TEMPLATE FOR THIS CONNECTION** and click **Next**.
[See image.](#connection-template-tab)
- On the **Connection Type** step:
- Select the **BROWSER SSO PROFILES **checkbox.
- Select **SAML 2.0** from the **PROTOCOL** drop-down menu.
- Click **Next**.
[See image.](#connection-type-tab)
- On the **Connection Options **step, select the **BROWSER SSO** checkbox and click **Next**.
[See image.](#connection-options-tab)
- On the **Import Metadata** step, select **None** for **METADATA** and click **Next**.
[See image.](#import-metadata-tab)
- On the **General Info** step:
- **Partner's Entity ID**: Paste the **Entity ID** copied from Zscaler.
- **Connection Name**: Enter a name for the application.
- **Base URL**: Leave** **empty.
- Click **Next**.
- On the **Browser SSO** step, click **Configure Browser SSO**.
- On the **SAML Profiles** tab, under **Single Sign-On (SSO) Profiles**, select the **SP-INITIATED SSO **checkbox, and then click **Next**. IdP-initiated SSO is not supported.
[See image.](#browser-sso-tab)
- On the **Assertion Lifetime** tab, leave the settings as is and click **Next**.
- On the **Assertion Creation** step, click **Configure Assertion Creation**. Select **STANDARD**, and** **click **Next**.
[See image.](#assertion-creation-tab)
- On the **Attribute Contract** step, under **Extend the Contract**, enter `email`, and then click **Add**.
[See image.](#extend-contract)
- Click **Next**.
- On the **Authentication Source Mapping** step, click **Map New Adapter Instance.**
- On the **Adapter Instance** tab, select the **Adapter Instance** for this app, and click **Next**.
- On the **Mapping Method** tab, leave the settings as is and click **Next**.
- On the **Attribute Contract Fulfillment** tab, configure the Attribute Contracts: **SAML SUBJECT** and **email**. For each:
- Select **Adapter** from the **Source** drop-down menu.
- Select **Email **from the **Value **drop-down menu.
- On the **Issuance Criteria** tab, click **Next**.
- On the **Summary **tab, review your entries, and then click **Done**.
- On the **Authentication Source Mapping** step, click **Next**.
- On the **Summary** tab, review your entries, and then click **Done**.
- On the **Assertion Creation** step, click **Next**.
- On the** Protocol Settings** tab, click **Configure Protocol Settings**.
- On the **Assertion Consumer Service URL** tab, select the **Default **checkbox.
- **Binding**: Select **POST** from the drop-down menu.
- **EndpointUrl**: Paste the **Reply URL** copied from Zscaler.
- Click **Add**, and then click **Next**.
[See image.](#assertion-consumer-service-url)
-
On the **Allowable SAML Bindings** tab, select the **POST **and **REDIRECT **checkboxes and click **Next**.
[See image.](#post-redirect)
- On the **Signature Policy** tab, select **Always Sign Assertion** and click **Next**.
- On the **Encryption Policy** tab, select **None**. Click **Next**.
- On the **Summary** tab, review your entries, and then click **Done**.
- On the **Protocol Settings** tab, click **Next**.
- On the **Summary** tab, review your entries, and then click **Done**.
- On the **Browser SSO** step, click **Next**.
- On the **Credentials** step, click **Configure Credentials**, select the signature on the SAML, and click **Next**.
- On the **Summary** tab, review your entries, and then click **Done**.
- On the **Credentials** tab, click **Next**.
- On the **Activation & Summary** step, scroll to the bottom and click **Save**.
After registering the SAML app in PingFederate, you are redirected to the SP Connections page, where you can copy your application's metadata to be used in the next step.
[]**![ec51b1e6-1c63-4705-9143-3c14456ccf61.png](/downloads/uvm/account-management/sso/ping-federate-sso/ec51b1e6-1c63-4705-9143-3c14456ccf61.png)
**
[]**![9d4f6dfc-9915-4536-96c7-4f0fa2a866b0.png](/downloads/uvm/account-management/sso/ping-federate-sso/9d4f6dfc-9915-4536-96c7-4f0fa2a866b0.png)
**
[]**![fb90e12b-ef26-42f7-9b46-97cc6381660c.png](/downloads/uvm/account-management/sso/ping-federate-sso/fb90e12b-ef26-42f7-9b46-97cc6381660c.png)
**
[]**![2415f839-546c-4a2a-b43f-b4616f4668ab.png](/downloads/uvm/account-management/sso/ping-federate-sso/2415f839-546c-4a2a-b43f-b4616f4668ab.png)
**
[]**![e75ddcd5-8cf1-44f1-aee1-5e6f3f3657e8.png](/downloads/uvm/account-management/sso/ping-federate-sso/e75ddcd5-8cf1-44f1-aee1-5e6f3f3657e8.png)
**
[]![2d58fb90-3a1e-4122-90d7-ea29eb8dcf7c.png](/downloads/uvm/account-management/sso/ping-federate-sso/2d58fb90-3a1e-4122-90d7-ea29eb8dcf7c.png)
[]![b51b11ae-fe42-49da-b23f-4a9758a5464b.png](/downloads/uvm/account-management/sso/ping-federate-sso/b51b11ae-fe42-49da-b23f-4a9758a5464b.png)
[]![c12153ac-4f2a-45d0-a453-2261ada56d82.png](/downloads/uvm/account-management/sso/ping-federate-sso/c12153ac-4f2a-45d0-a453-2261ada56d82.png)
[]**![0a6ea035-14b5-42c8-b0fd-c1d439a6b613.png](/downloads/uvm/account-management/sso/ping-federate-sso/0a6ea035-14b5-42c8-b0fd-c1d439a6b613.png)
**
[]**![e7a3bec2-a48f-4b4f-ad5c-e4ead57d2ee6.png](/downloads/uvm/account-management/sso/ping-federate-sso/e7a3bec2-a48f-4b4f-ad5c-e4ead57d2ee6.png)
**
[]After registering an app in PingFederate, share XML metadata with your Zscaler Account team.
To retrieve the XML metadata:
-
On the **SP Connections **page of the application you registered, click **Select Action** > **Export Metadata**.
[See image.](#export-metadata)
- Select the signing certificate and click **Next**.
-
Scroll to the bottom of the page and click **Export**.
The signing certificate file is saved to your computer.
- Click **Done**.
To share metadata with Zscaler:
- In the SecOps platform, click the **Profile** menu on the top right of the page and select **Account Settings**.
-
In the **Authenticate** section, paste the XML metadata into the **SAML XML MetaData **field.
If the Authenticate section is not visible, share the XML metadata with your Zscaler Account team.
[See image.](#saml-xml-metadata-field)
While a metadata URL is also supported, Zscaler recommends pasting the XML metadata directly.
[]![2cc0bdea-5a17-4186-8a01-2314613260e9.png](/downloads/uvm/account-management/sso/ping-federate-sso/2cc0bdea-5a17-4186-8a01-2314613260e9.png)
[]**![SAML XML metadata field](/downloads/uvm/account-management/sso/ping-federate-sso/8de8cff5-c62f-4ece-9a98-ecc5562afb01.png)
**