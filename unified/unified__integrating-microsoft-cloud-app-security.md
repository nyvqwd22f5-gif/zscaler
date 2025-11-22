# Integrating with Microsoft Cloud App Security
Source: https://help.zscaler.com/unified/integrating-microsoft-cloud-app-security
PDF: https://help.zscaler.com/pdf/com/en/1494616.pdf

This article provides configuration steps and examples for integrating Zscaler and Microsoft Cloud App Security (MCAS) (i.e., Microsoft Defender for Cloud Apps).
With MCAS, you can sanction or unsanction applications for use in your organization. When you integrate MCAS and Zscaler, Zscaler syncs unsanctioned application URLs to a custom URL category called "MS Defender Unsanctioned Apps". The integration enables you to discover unsanctioned applications and automatically update the custom URL category based on your organization’s web transaction logs streaming from the Internet & SaaS through the Nanolog Streaming Service (NSS) to MCAS.
Integrating with MCAS using OAuth 2.0-Based Authentication
The integration supports secure OAuth 2.0-based authentication. In contrast to token-based authentication in which a key is generated based on the user’s security context, the OAuth 2.0 method grants access based on the application’s context. Permissions are set at the application level and not inherited by the user, whose roles and permissions in Azure can change over time. To learn more about accessing MCAS with application context, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/defender-cloud-apps/api-authentication-application).
To integrate with MCAS using OAuth 2.0-based authentication:
- [1. Create a Microsoft Entra application.](#create-entra-application)
- [2. Configure an MCAS partner integration.](#configure-mcas-partner-integration)
- [3. Enable automatic log uploads to MCAS.](#enabled-automatic-log-uploads)
- [Verifying Your Integration](#verifying)
- [Troubleshooting](#troubleshooting)
Support for Existing Token-Based Integrations
If you have an existing MCAS partner integration using token-based authentication, your integration remains supported for backward compatibility. On the Partner Integrations page in the Admin Portal, you see the **Select Authentication Method** setting with the **Token** option enabled.
[See image.](#img-zia-mcas-integration-token)
You cannot make any configuration changes to your existing integration or create a new token-based integration. Zscaler recommends converting your existing integration to the OAuth 2.0-based authentication method for improved security. After you convert your integration, the token method is no longer available as an option.
If you do not have an existing integration using token-based authentication, the token method is not available as an option in the portal at all.
[]To access MCAS with application context, create an application in Microsoft Entra ID (previously Microsoft Active Directory) and assign it with the permissions required to access MCAS. In creating the application, you generate the values of the parameters (e.g., client ID, client secret, etc.) required for OAuth 2.0-based authentication. You later provide the values when configuring the integration on the Partner Integrations page in the Admin Portal.
To create an application:
- [a. Register an application.](#register-app)
- [b. Add a client secret.](#add-client-secret)
- [c. Add permissions.](#add-permissions)
[]To register an application:
- Log in to [Microsoft Azure](https://azure.microsoft.com/).
- Under **Azure services**, go to **Microsoft Entra ID**.
-
In the left-side navigation, go to **App Registrations** and then click **New registration**.
[See image.](#img-entra-new-app-registration)
The **Register an application** window appears.
-
In the window:
- **Name**: Enter a name for the application.
- **Supported account types**: Ensure that this option is set to **Accounts in this organizational directory only (****<tenant>**** only - Single tenant)**.
[See image.](#img-entra-register-app)
-
Click **Register**.
The application is registered, and its **Overview** page is displayed.
-
On the application’s **Overview** page, copy the **Application (client) ID** and **Directory (tenant) ID** values and save them for later use.
[See image.](#img-entra-app-id-tenant-id)
[]To add a client secret to the application:
-
On the left side-navigation of the application, go to **Certificates & secrets** and then click **New client secret**.
[See image.](#img-entra-new-client-secret)
The **Add a client secret** pane appears.
-
In the pane:
- **Description**: Add a description.
- **Expiration**: Add an expiration.
[See image.](#img-entra-add-client-secret)
-
Click **Add**.
The client secret value is generated and displayed.
-
Copy the generated secret value immediately and save it for later use.
The client secret value is displayed only once and cannot be retrieved after you navigate away from the page.
[See image.](#img-entra-client-secret-value)
[]To add the required MCAS permissions to the application:
-
In the left side-navigation of the application, go to **API Permissions** and click **Add a permission**.
[See image.](#img-entra-add-permission)
The **Request API permissions **pane appears.
-
In the pane, click the **APIs my organization uses** tab and then enter `Microsoft Cloud App Security` in the search bar.
[See image.](#img-entra-request-permissions)
-
Copy the **Application (client) ID** value for MCAS and save it for later use.
This value is used for the Scope parameter when configuring the partner integration in the Admin Portal.
[See image.](#img-entra-mcas-app-id-scope)
-
Select **Microsoft Cloud App Security** in the search results and then select **Application permissions**.
[See image.](#img-entra-mcas-app-permissions)
-
Select the **discovery.manage** permission, which is required to upload data and generate block scripts.
[See image.](#img-entra-select-permissions)
- Click **Add permissions**.
-
Click **Grant admin consent for ****<Tenant>** under the **Configured permissions** section and then click **Yes** when prompted.
[See image.](#img-entra-grant-consent)
[]After creating the application, use the generated values (e.g., client ID, client secret, etc.) to configure the integration on the Partner Integrations page in the Admin Portal. This step of the integration also requires:
- An active NSS web log subscription or trial
- A healthy NSS web server enabled
- An MCAS NSS feed configured for the enabled NSS web server
After you complete and validate the configuration on the Partner Integrations page, the OAuth 2.0-based authentication parameters are pushed to the MCAS NSS feed configuration (in the backend only). The feed configuration is pushed to the Zscaler Central Authority (CA). The Zscaler CA then pushes the feed configuration to NSS.
To configure an MCAS partner integration:
- Log in to the Admin Portal.
- Go to **Policies **> **Data Protection** > **Common Resources** > **Microsoft Defender for Cloud App**.
- On the **Microsoft Cloud App Security** page:
- Under **Microsoft Cloud App Security (MCAS) Authentication Setup**, configure the following parameters and then click **Test**:
- **Client ID**: Enter the Application (client) ID for the application that you created in Azure (e.g., `97b9XXXX-beXX-48XX-b5XX-8792cdXXXXXX`).
- **Client Secret**: Enter the application’s client secret value that you generated in Azure. Ensure that you provide the client secret *value*, not the client secret ID.
- **Scope:** Enter the scope (i.e., the resource identifier) for the MCAS API, appended with the `/.default` suffix (e.g., `05a65629-4c1b-48c1-a78b-804c4abdd4af/.default`). To ensure you have the current scope for MCAS, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/defender-cloud-apps/api-authentication-application#create-an-app).
- **Authentication URL**: Enter the authentication URL with your Directory (tenant) ID in Azure: `https://login.microsoftonline.com/``<Tenant ID>``/oauth2/v2.0/token`. For example: `https://login.microsoftonline.com/``9fe3XXXX-d6XX-46XX-a9XX-d8907dXXXXXX``/oauth2/v2.0/token`
-
**API URL**: Enter the API URL for your tenant (e.g., `https://``safemarch``.``us3``.portal.cloudappsecurity.com`). To find your API URL, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/defender-cloud-apps/api-introduction#api-url-structure).
[See image.](#img-zia-mcas-partner-integration-auth-setup)
Zscaler verifies if the configuration is valid. If the configuration is valid, the integration proceeds to the next step and Zscaler attempts to sync your unsanctioned Cloud App URLs. If the configuration is not valid, the reason for the failure appears on the page. In the following example, the API URL is not valid.
[See image.](#img-zia-mcas-partner-integration-error)
The invalid configuration and the reason for the failure is also logged in the [audit logs](/unified/about-internet-saas-audit-logs) (Administration > Admin Management > Audit Logs > Internet & SaaS).
[See image.](#img-zia-mcas-partner-integration-error-audit-logs)
To clear the existing configuration, click **Clear Config** and then **OK** when prompted.
Clearing the configuration stops the syncing of unsanctioned Cloud App URLs from MCAS to your **MS Defender Unsanctioned Apps **URL category. This existing category is not removed by this action, as it might be in use as part of your configured policies.
- Under **NSS Subscription**, ensure that you have:
- An active NSS web log subscription or trial. If you do not have an active subscription, submit a Zscaler Support ticket.
- A healthy NSS web server enabled. You must have an NSS web server configured and deployed to complete this integration. To learn more, see [Deploying NSS Virtual Appliances](/unified/deploying-nss-virtual-appliances) and [Adding NSS Servers](/unified/adding-nss-servers). For the list of ports/domains/IP addresses you need to allow for NSS to communicate with the MCAS service, refer to the [Microsoft documentation](https://docs.microsoft.com/en-us/cloud-app-security/network-requirements#access-and-session-controls). If your enabled NSS web server is not in a healthy state, see [Troubleshooting Deployed NSS Servers](/unified/troubleshooting-deployed-nss-servers).
-
An MCAS NSS feed configured for the enabled NSS web server. To learn more, see [Adding MCAS NSS Feeds](/unified/adding-mcas-nss-feeds).
[See image.](#img-zia-mcas-partner-integration-nss-subscription)
In order for your MCAS NSS feed to perform optimally, the VM deployed for the NSS web server requires a minimum of 8 GB of RAM. To learn more, see [Deploying NSS Virtual Appliances](/unified/deploying-nss-virtual-appliances) and [Adding MCAS NSS Feeds](/unified/adding-mcas-nss-feeds).
- Under **Unsanctioned Cloud App URLs Sync**, note that after your MCAS integration is configured, the first unsanctioned Cloud App URL sync occurs within two hours. Syncs to this custom URL category occur every two hours after the initial sync.
After your integration is configured, this page updates automatically, showing the number of URLs that are successfully synced. If you exceed the [maximum custom category limit](/unified/ranges-limitations#internet-saas) that is set for your organization, then the sync fails. To learn more, see the [Troubleshooting section](/unified/integrating-microsoft-cloud-app-security#troubleshooting) of this article.
[]After you configure the MCAS partner integration in the Admin Portal, you configure and enable automatic log uploads from NSS to MCAS. This involves adding a data source for NSS in the MCAS (i.e., Microsoft Defender) portal, and from your NSS VM, starting the NSS service in OAuth 2.0 mode.
To configure and enable automatic log uploads:
- [a. Add a data source for NSS.](#add-data-source)
- [b. Start the NSS service in OAuth 2.0 mode.](#start-zbridge-nss-services)
-
[]In the [MCAS portal](https://security.microsoft.com/), go to **Settings **and then click **Cloud Apps**.
[See image.](#img-mcas-settings-cloud-apps)
-
Under **Cloud Discovery**, click **Automatic log upload**.
[See image.](#img-mcas-cloud-apps-auto-log-upload)
-
On the **Data sources** tab, click **Add data source**.
[See image.](#img-mcas-auto-log-upload-add-data-source)
-
On the **Add Data Source** page:
- **Name**: Enter `NSS`.
- **Source**: Select** Zscaler QRadar LEEF**.
- **Receiver type**: Select **Syslog - UDP**.
[See image.](#img-mcas-add-data-source-nss)
You must configure the fields as documented in the [Microsoft documentation](https://docs.microsoft.com/en-us/cloud-app-security/zscaler-integration), otherwise NSS and MCAS cannot communicate.
- Click **Add**.
[]The NSS gets the logs from the Zscaler Nanolog, converts the logs per the MCAS NSS feed output format (i.e., LEEF), and sends the logs for uploading to MCAS.
To start the NSS service in OAuth 2.0 mode:
- Log in to the [NSS VM for your platform](/zia/deploying-nss-virtual-appliances) (i.e., VMware vSphere, Amazon Web Services, or Azure).
-
Run the following command:
sudo nss configure-mcas2
The command `sudo nss configure-mcas` used for token-based integrations does not work for OAuth 2.0-based integrations.
-
Restart the NSS service by running the following command:
sudo nss restart
[]To verify your MCAS partner integration:
- In the Admin Portal, go to **Policies** > **Access Control** > **Internet & SaaS** > **URL Categories**.
-
After the initial URL sync, verify that the **User-Defined** category called **MS Defender Unsanctioned Apps** is shown in the table on the page.
[See image.](#img-zia-url-categories-ms-defender-unsanctioned)
To verify automatic log uploads:
- In the MCAS portal, go to the **Automatic log upload** page (**Settings** > **Cloud Apps** > **Cloud Discovery**).
-
On the **Data sources **tab, make sure that the NSS data source you set up for Zscaler is receiving data.
[See image.](#img-mcas-uploaded-logs-verified)
To verify the connection with MCAS, run the following cURL command, replacing the authentication parameters in red with the values from your configuration:
curl -X POST
"https://login.microsoftonline.com/<Tenant ID>/oauth2/token" -d
"resource=<Scope>" -d
"client_id=<Client ID>" -d
"client_secret=<Client Secret Value>" -d
"grant_type=client_credentials" -H
"Content-Type: application/x-www-form-urlencoded"
The value of `resource` (e.g., `05a65629-4c1b-48c1-a78b-804c4abdd4af`) is also used in the **Scope** parameter when configuring the partner integration in the Admin Portal.
The following example of a valid connection shows the bearer token and its expiration in the output.
[See image.](#img-nss-cli-mcas-connection-verified)
- []You must assign the **MS Defender Unsanctioned Apps **URL category to a URL filtering rule to block the traffic to those destinations. Zscaler recommends that SSL inspection is enabled for that category in case some sanctioned applications are uniquely identified by a full URL rather than just a domain name. To learn more, see [Configuring the URL Filtering Policy](/unified/configuring-url-filtering-policy) and [Configuring SSL Inspection Policy](/unified/configuring-ssl-inspection-policy).
- If the unsanctioned Cloud App URL sync to your custom URL category is not occurring every two hours, contact Zscaler Support.
- If you encounter an MCAS authentication validation error on a valid and verified configuration, make sure that you have at least one application categorized as unsanctioned within the MCAS portal. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-discovery).
[]![Token-based Partner Integration](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/mcas-integration-token-method.png)
[]![New registration button in Microsoft Entra](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/microsoft-entra-new-registration.png)
[]![Register an app window in Microsoft Entra](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/microsoft-entra-register-application.png)
[]![Microsoft Entra application's client ID and tenant ID ](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/microsoft-entra-app-id-tenant-id.png)
[]![New client secret button in Microsoft Entra ](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/microsoft-entra-new-client-secret.png)
[]![Add a client secret window in Microsoft Entra](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/microsoft-entra-add-client-secret.png)
[]![Microsoft Entra application's client secret value](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/microsoft-entra-client-secret-value.png)
[]![Add a permission button in Microsoft Entra](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/microsoft-entra-add-permission.png)
[]![ Request API permissions page in Microsoft Entra](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/microsoft-entra-request-api-permissions-mcas.png)
[]![ MCAS Application permissions page in Microsoft Entra](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/microsoft-entra-application-permissions.png)
[]![MCAS Application (client) ID in Microsoft Entra](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/microsoft-entra-mcas-app-id.png)
[]![Select permissions page in Microsoft Entra](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/microsoft-entra-select-permissions.png)
[]![Grant admin consent button in Microsoft Entra](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/microsoft-entra-grant-admin-consent.png)
[]![OAuth 2.0-based MCAS Partner Integration in the ZIA Admin Portal](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/zia-mcas-partner-integration-authentication.png)
[]![Authentication error](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/zia-mcas-partner-integration-authentication-error.png)
[]![Authentication error in the Audit Logs](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/zia-authentication-error-audit-logs.png)
[]![ NSS Subscription section of Partner Integration page](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/zia-mcas-partner-integration-nss-subscription.png)
[]![Settings menu in Microsoft Defender for Cloud Apps](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/mcas-settings-cloud-apps.png)
[]![Automatic log upload in Microsoft Defender for Cloud Apps ](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/mcas-automatic-log-upload.png)
[]![Add data source button in Microsoft Defender for Cloud Apps](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/mcas-add-data-source.png)
[]![Add data source window in Microsoft Defender for Cloud Apps](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/mcas-data-source-nss.png)
[]![MS Defender Unsanctioned Apps URL category ](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/zia-url-categories-ms-defender-unsanctioned.png)
[]![Uploaded logs in Microsoft Defender for Cloud Apps](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/mcas-data-source-nss-verified.png)
[]![Verified MCAS connection in NSS VM CLI](/sites/default/files/downloads/zia/partner-integrations/configuring-mcas-integration/mcas-connection-verified.png)