# Onboarding SaaS Apps for Business Insights
Source: https://help.zscaler.com/business-insights/onboarding-saas-apps-business-insights
PDF: https://help.zscaler.com/pdf/com/en/1473186.pdf

Business Insights receives signals and data from 4 data sources: the Zscaler Internet Access (ZIA) service, identity providers (IdPs), direct SaaS application connector integrations, and custom application signatures. To pull usage information directly from the app and view accurate insights that overextend other data sources, Zscaler recommends configuring a direct SaaS application connector (requires admin access to the app) for the supported apps. However, you can view Business Insights metrics even when you're unable to configure a connector for a specific app with the help of ZIA and IdP-sourced data by simply specifying the plan information. This article explains how to configure discovered and connector-supported apps for Business Insights computation.
To onboard a SaaS application:
- Add the application using one of the following options:
-
Go to** Application **> **Application Insights **>** Add App**.
[See image.](#connect-app-img)
The **Configuration** page appears.
The page shows the list of applications for which the Business Insights service supports connector integration. Hence, the Business Insights service assumes that you want to configure an application connector from one of the connector-supported apps and doesn't show the second choice in [Step 3](#step3-skip).
If you want to skip the connector configuration for a connector-supported app and set up a ZIA or IdP gathered insights mechanism, click the **Add** icon for the application from the [All Applications](/business-insights/about-all-applications) page or the [Top 10 Discovered Applications](/business-insights/about-application-inventory#top-ten) table.
-
Go to **Application **> **Application Insights **>** Discovered Apps**.** **Click the **Add** icon for an application from the [Top 10 Discovered Applications](/business-insights/about-application-inventory#top-ten) table.
[See image.](#add-app-img)
- Go to **Application **>** All Applications**.** **Click the **Add** icon for an application.
-
Go to **Application **> **Application Insights **>** Cost Savings**.** **Click the **Add** icon for an application.
[See image.](#add-app-cost-img)
If you click the **Add** icon for an application that has connector integration support, the Business Insights service skips [Step 2](#step-2-choose). If you click the **Add** icon for an application that doesn't have connector integration support, the Business Insights service skips the first choice in [Step 3](#step3-skip).
-
[]Under **Choose SaaS Application**, select the SaaS applications you want to configure.
[See image.](#choose-app-connect)
- Configure a connector for the app and then provide the licensing information. You can also skip the connector configuration and just provide the licensing information if you don't have admin access to the app, or don't want to configure the connector.
- [Create a new configuration (requires admin access)](#connector)
- [Skip Connector configuration (use IdP/ZIA usage stats only)](#idp-zia-stats)
[]Follow the steps for the application that you selected to set up a connector configuration:
- [Box](#box)
- [GitHub](#github)
- [Google Workspace](#google-workspace)
- [Microsoft 365](#M365)
- [Okta](#okta)
- [Salesforce](#salesforce)
- [ServiceNow](#servicenow)
- [Slack](#slack)
[][]Follow the steps if you want to skip the connector configuration for a supported app and set up a ZIA or IdP gathered insights mechanism, or if you don't have the admin access to set up the connector:
- Under** Tenant Name**, enter a name for the SaaS application tenant.
- Click **Next**.
- Complete the following fields:
- **Purchased Seats**: The number of seats purchased as part of the subscription.
- **Assigned Seats**: The number of seats assigned to the users from the purchased seats.
- **Per User License Cost**: The cost incurred to buy one seat per month.
- **Contract Start Date**: The start date of the subscription.
- **Contract End Date**: The end date of the subscription.
- Click **Complete**.
The application is successfully onboarded.
[]To configure Box:
- Under** Tenant Name**, enter a name for the application tenant.
- Click **Next**.
-
Copy the information from the **Zscaler SaaS Connector **field. You need it for [Step i](#step-i-box) when adding a custom application for Box.
[See image.](#saas-connector)
-
Click **Provide Admin Credentials**.
[See image.](#provide-box-cred)
The Box portal appears.
-
Log in to Box with your admin credentials.
You are redirected to the Box Admin console.
-
Go to **Apps**.
[See image.](#seeimagebox-e)
-
Click the **Custom Apps Manager** tab.
[See image.](#seeimagebox-f)
-
Click **Add App**.
[See image.](#seeimagebox-g)
The **Add App **window appears.
- []In the **Add App** window:
-
**Client ID**: Enter the Zscaler** **SaaS Connector value you copied in [Step c](#step-c-box).
[See image.](#seeimagebox-h-i)
- Click **Next**.
-
Review the permissions requested by the Business Insights service to access Box, then click **Authorize **and **Okay**.
[See image.](#authorize-box)
-
In the Box Admin console, go to **Account & Billing**.
[See image.](#seeimagebox-i)
-
Under **Account Information**, copy the **Enterprise ID**.
[See image.](#seeimagebox-j)
-
In the Business Insights Admin Portal, under** Box Enterprise ID**, enter the enterprise ID you copied from the Box portal in the previous step. This ID is used to identify the tenant.
[See image.](#seeimagebox-k)
-
Click **Next**.
The Business Insights service begins to retrieve your subscription details and establish an API connection. This might take a few minutes or hours. After the connector is configured successfully for the application, you can enter the subscription details.
You can navigate away from the page while the Business Insights service establishes the connection; you're notified after the connector is configured successfully.
- Complete the following subscription fields:
- **Purchased Seats**: The number of seats purchased as part of the subscription.
- **Assigned Seats**: The number of seats assigned to the users from the purchased seats.
- **Per User License Cost**: The cost incurred to buy one seat per month.
- **Contract Start Date**: The start date of the subscription.
- **Contract End Date**: The end date of the subscription.
- Click **Complete**.
The application is successfully onboarded.
[]![Screenshot of the Apps menu in the Box Admin Console.](/downloads/zia/adding-saas-application-tenants/Box%20left%20nav.png)
[]![Zscaler SaaS Connector](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-Box-copy-connector.png)
[]![Provide Admin Credentials to Box](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-Box-provide-access_0.png)
[]![Screenshot of the Custom Apps tab in the Apps menu.](/downloads/zia/adding-saas-application-tenants/Box%20custom%20apps.png)
[]![Screenshot of the Authorize New App button under Custom Apps.](/downloads/zia/adding-saas-application-tenants/Box%20new%20app.png)
[]![Screenshot of the Client ID field in the App Authorization window.](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Box-App-Authorization-Client-ID.png)
[]![Authorize Box App](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Box-App-Authorization-app_0.png)
[]![Screenshot of the Account & Billing menu in the Box Admin Console.](/downloads/zia/adding-saas-application-tenants/Box%20left%20nav%20billing.png)
[]![Screenshot of the Enterprise ID in the Account Information section.](/downloads/zia/adding-saas-application-tenants/Box%20Enterprise%20ID.png)
[]![Screenshot of the Box Enterprise ID field in the Enter the Box Enterprise ID section.](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/ZIA-Enter-Box-Enterprise-ID-6_1.png)
[]To configure GitHub:
- Under** Tenant Name**, enter a name for the application tenant.
-
Click **Next**,** **then **Provide Admin Credentials**.
[See image.](#seeimagegithub-c)
The GitHub portal appears.
- Log in to GitHub with an admin account.
- A confirmation page appears with the permissions that the connector requires. Click **Allow**.
-
In the Business Insights Admin Portal, under** GitHub Admin Email ID**, enter your GitHub admin email ID.
[See image.](#github-adminm-id)
-
Click **Next**.
The Business Insights service begins to retrieve your subscription details and establish an API connection. This might take a few minutes or hours. After the connector is configured successfully for the application, you can enter the subscription details.
You can navigate away from the page while the Business Insights service establishes the connection; you're notified after the connector is configured successfully.
- Complete the following subscription fields:
- **Purchased Seats**: The number of seats purchased as part of the subscription.
- **Assigned Seats**: The number of seats assigned to the users from the purchased seats.
- **Per User License Cost**: The cost incurred to buy one seat per month.
- **Contract Start Date**: The start date of the subscription.
- **Contract End Date**: The end date of the subscription.
- Click **Complete**.
The application is successfully onboarded.
[]![Screenshot highlighting the Provide Admin Credentials button in the Authorize the SaaS Application section.](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-github-provide-access.png)
[]![GitHub Amdin Email ID](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-github-ID.png)
[]To configure Google Workspace:
- Under** Tenant Name**, enter a name for the application tenant.
- Click **Next**.
-
[]Copy the information from the **Zscaler SaaS Connector** and **Google Workspace Scope **fields. You need it for [Step i](#step-i-gspace) when adding an API client for Google Workspace.
[See image.](#copy-connector-google)
-
Click **Provide Admin Credentials**.
[See image.](#provide-admin-google)
The Google Workspace portal appears.
-
Log in to Google Workspace with your admin credentials.
You're redirected to the Google Admin console.
-
Go to **Security **> **Access and data control** > **API controls**.
[See image.](#api-control)
-
Under **Domain wide delegation**, click **MANAGE DOMAIN WIDE DELEGATION**.
[See image.](#manage-domain-delegation)
-
Click **Add new**.
[See image.](#add-new-client)
The **Add a new client ID** window appears.
- []In the **Add a new client ID** window:
- **Client ID**: Enter the Zscaler SaaS Connector value you copied in [Step c](#step-c-gspace).
- **Overwrite existing client ID**: Deselect this checkbox.
-
**OAuth scopes (comma-delimited)**: Enter the Google Workspace scope you copied in [Step c](#step-c-gspace). This OAuth scope grants read-only access to the usage reporting API.
[See image.](#add-new-client-id)
-
Click **Authorize**.
The Zscaler Connector App is added as an API client.
-
In the Business Insights Admin Portal, under **Google Admin Email ID**, enter your admin email ID used to log in to the Google Admin console.
[See image.](#admin-id-google)
-
Click **Next**.
The Business Insights service begins to retrieve your subscription details and establish an API connection. This might take a few minutes or hours. After the connector is configured successfully for the application, you can enter the subscription details.
You can navigate away from the page while the Business Insights service establishes the connection; you're notified after the connector is configured successfully.
- Click **Next**.
- Complete the following subscription fields:
- **Purchased Seats**: The number of seats purchased as part of the subscription.
- **Assigned Seats**: The number of seats assigned to the users from the purchased seats.
- **Per User License Cost**: The cost incurred to buy one seat per month.
- **Contract Start Date**: The start date of the subscription.
- **Contract End Date**: The end date of the subscription.
- Click **Complete**.
The application is successfully onboarded.
[]![Copy SaaS Connector for Google](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-google-copy-connector.png)
[]![Provide Admin Credentials for Google Workspace](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-google-provide-access.png)
[]![Screenshot highlighting the Security menu in the Google Admin console.](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Google-Security-menu-6_1.png)
[]![Screenshot highlighting the MANAGE DOMAIN WIDE DELEGATION button in the Domain wide delegation section.](/downloads/zia/adding-saas-application-tenants/Google-Manage-Domain-wide-delegation-button.png)
[]![Screenshot highlighting the Add new button for API clients.](/downloads/zia/adding-saas-application-tenants/Google-API-clients-Add-new-button.png)
[]![Screenshot of the configured Add a new client ID window.](/downloads/zia/adding-saas-application-tenants/Google-Add-new-client-ID-window-6_1.png)
[]![Screenshot of the Google Admin Email ID field in the Enter the Google Admin Email ID section.](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-google-ID_0.png)
[]To configure Microsoft 365:
- Under** Tenant Name**, enter a name for the application tenant.
-
Click **Next**, then **Provide Admin Credentials**.
[See image.](#provide-access-m365)
The Microsoft 365 portal appears.
-
Log in to Microsoft 365 with your admin credentials.
A confirmation page appears requesting the permissions required to configure the connector.
-
Review the permissions for the Business Insights service to access the Microsoft account, and click **Accept**.
[See image.](#m365-permissions)
The Business Insights service begins to retrieve your subscription details and establish an API connection. This might take a few minutes or hours. After the connector is configured successfully for the application, you can enter the subscription details.
You can navigate away from the page while the Business Insights service establishes the connection; you're notified after the connector is configured successfully.
- Click **Next**.
- Complete the following subscription fields:
- **Purchased Seats**: The number of seats purchased as part of the subscription.
- **Assigned Seats**: The number of seats assigned to the users from the purchased seats.
- **Per User License Cost**: The cost incurred to buy one seat per month.
- **Contract Start Date**: The start date of the subscription.
- **Contract End Date**: The end date of the subscription.
- Click **Complete**.
The application is successfully onboarded.
[]![Provide Admin Credentials For M365 button](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-m365-provide-access.png)
[]![Microsoft Permission Request Page](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-m365-permissions.png)
[]To configure Okta:
- [a. Create app integration for Business Insights in Okta.](#create-app-okta)
- [b. Assign your Okta Admin account to the Business Insights app.](#assign-okta-admin)
- [c. Copy the necessary information from Okta.](#copy-client)
- [d. Configure the connector for Okta in the Business Insights Admin Portal.](#connector-okta)
[]Register Business Insights with Okta by creating an app integration in the Okta Admin console.
To integrate the application:
- Log in to the [Okta Admin console](https://login.okta.com/).
- From the Okta Admin console, go to **Applications **> **Applications**.
-
Click **Create App Integration**.
[See image.](#create-app-okta-img)
The **Create a new app integration** window appears
- In the **Create a new app integration** window:
- Select **OIDC - OpenID Connect** as the **Sign-in method**.
-
Select **Web Application** as **Application type**.
[See image.](#oidc-okta-web)
-
Click **Next**.
The **New Web App Integration** window appears.
-
In the **New Web App Integration** window:
- **App integration name**: Enter `Business Insights`. In this article, we use `okta-connector-test` as an example.
- **Grant type**: Select the **Authorization Code** and **Refresh Token** checkboxes.
-
**Sign-in redirect URIs**: Enter `https://admin.zscaleranalytics.net/admin/onboarding-wizard`
[See image.](#new-app-name-img)
-
**Controlled access**: Select **Skip group assignment for now**.
[See image.](#assigment-okta)
- Skip the other fields and click **Save**.
You're redirected to the Business Insights app configuration page in Okta.
- On the app configuration page, click the **Okta API Scopes** tab.
-
Click **Grant **for the following API Scopes:
- okta.apps.read
- okta.logs.read
- okta.userTypes.read
- okta.users.read
[See image.](#scopes-okta)
The app is successfully integrated with Business Insights.
[]After the app is successfully integrated, assign your Okta Admin account to the Business Insights app.
To assign the admin account:
- From the Okta Admin console, go to the **Applications **> **Applications**.
- Search and click on the Business Insights app integration.
- Go to the **Assignments **tab.
- Click **Assign** > **Assign to People**.
- Search for your Okta Admin account.
-
Click **Assign**, then **Save and Go Back**.
[See image.](#assign-okta)
- Click **Done**.
[]Copy the following information from the **General** tab of the Business Insights app configuration page in your Okta Admin console:
- Client ID
- Client Secret
[See image.](#general-tab-okta)
[]In the Business Insights Admin Portal:
- Under** Tenant Name**, enter a name for the application tenant.
- Click **Next**.
-
Under **Register the Oauth Application**:
- **Client ID**: Paste the Client ID that you copied from Okta Admin console.
- **Client Secret**: Paste the Client ID that you copied from Okta Admin console.
- **Okta Domain**: Enter your organization's Okta domain URL.
[See image.](#okta-oauth)
-
Click **Authorize**.
The Okta authentication page appears.
-
Authenticate with your Okta Admin credentials and click **Next**.
The Business Insights service begins to retrieve your subscription details and establish an API connection. This might take a few minutes or hours. After the connector is configured successfully for the application, you can enter the subscription details.
You can navigate away from the page while the Business Insights service establishes the connection; you're notified after the connector is configured successfully.
- Complete the following subscription fields:
- **Purchased Seats**: The number of seats purchased as part of the subscription.
- **Assigned Seats**: The number of seats assigned to the users from the purchased seats.
- **Per User License Cost**: The cost incurred to buy one seat per month.
- **Contract Start Date**: The start date of the subscription.
- **Contract End Date**: The end date of the subscription.
- Click **Complete**.
The application is successfully onboarded.
[]![Enter OAuth Application information](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-okta-oauth.png)
[]![Create app Integration button in Okta](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/saas_okta_01_createapp%20(1).png)
[]![Assigments page in Okta](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/saas_okta_04_assignments_0.png)
[]![Okta API Scopes tab in Okta](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/saas_okta_05_oktascope_0.png)
[]![Assign People option in Okta](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-okta-assign-people.png)
[]![New app configuration page in Okta](/downloads/business-insights/application-insights/application-settings/onboarding-saas-apps-business-insights/saas_okta_03_nameURI_0.png)
[]![Create an app integration window](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/saas_okta_02_appintegration_1.png)
[]![General tab in Okta](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/saas_okta_06_id2_2.png)
[]To configure Salesforce:
- [a. Install the ZscalerBIPackage.](#salesforce-install-zpackage)
- [b. Create a permission set.](#salesforce-create-permission-set)
- [c. Assign the permission set.](#salesforce-assign-permission-set)
- [d. Configure the Salesforce CRM content settings.](#salesforce-crm-content-settings)
- [e. Configure the application connector.](#salesforce-configure-connector-app)
[]You must install the ZscalerBIPackage, which contains the information for the connector configuration.
To install the ZscalerBIPackage for Salesforce:
-
Click the URL in the email from the Salesforce team.
You're redirected to the** Install ZscalerBIPackage** page.
- On the **Install ZscalerBIPackage** page:
- Ensure the **Install for Admins Only** checkbox is selected.
- Select the **I acknowledge that I’m installing a Non-Salesforce Application that is not authorized for distribution as part of Salesforce’s AppExchange Partner Program **checkbox.
- Click **Install**.
-
After installation is complete, click **Done**.
[See image.](#seeimagesalesforce-av)
[]
[]![Screenshot highlightingthe Done button on the Install zscalerPackage page.](/downloads/zia/adding-saas-application-tenants/Salesforce-Install-zscalerPackage-Done-button.png)
[]Create a permission set to assign to your user account and the application connector.
To create a permission set:
- Log in to the [Salesforce](https://login.salesforce.com/) portal.
-
From the left-side navigation, go to **Users** > **Permission Sets**.
[See image.](#seeimagesalesforce-bi)
-
Click **New**.
[See image.](#seeimagesalesforce-bii)
The **Permission Set Create** window appears.
-
In the **Permission Set Create** window:
- **Label**: Enter a label for the permission set. In this example, it's `Zscaler SaaS Connector User`.
- **API Name**: This field populates based on the label you enter.
- **License**: Select **Salesforce**.
[See image.](#seeimagesalesforce-biii)
- Click **Save**.
-
In the **Apps **section, click **App Permissions**.
[See image.](#seeimagesalesforce-bv)
-
Click **Edit**.
[See image.](#seeimagesalesforce-bvi)
-
In the **Content** section, select the following **Permission Name** checkboxes:
- **Manage record types and layouts for Files**
- **Manage Salesforce CRM Content**
- **Query All Files**
[See image.](#seeimagesalesforce-bvii)
- Click **Save** and then **Save** again to confirm.
[]![Screenshot highlighting the Permission Sets menu.](/downloads/zia/adding-saas-application-tenants/Salesforce-Permission-Sets-menu.png)
[]![Screenshot highlighting the New button on the Permission Sets page.](/downloads/zia/adding-saas-application-tenants/Salesforce-Permission-Sets-New-button.png)
[]![Screenshot of the configured Permission Set Create window.](/downloads/zia/adding-saas-application-tenants/Salesforce-Permission-Set-Create-window.png)
[]![Screenshot highlighting the App Permissions option in the Apps section.](/downloads/zia/adding-saas-application-tenants/Salesforce-Zscaler-SaaS-Connector-User-App-Permissions-Setting.png)
[]![Screenshot highlighting the Edit button for App Permissions.](/downloads/zia/adding-saas-application-tenants/Salesforce-App-Permissions-Edit-button.png)
[]![Screenshot of the selected permissions in the Content section.](/downloads/zia/adding-saas-application-tenants/Salesforce-Permission-Sets-Content-section.png)
[]Assign the permission set you created to your Salesforce user account.
To assign the permission set to your user account:
-
In the left-side navigation, go to **Users** > **Users**.
[See image.](#seeimagesalesforce-ci)
-
In the **Full Name** column, click on your admin name.
[See image.](#seeimagesalesforce-cii)
-
In the **User Details** section, select the **Salesforce CRM Content User** checkbox.
[See image.](#seeimagesalesforce-ciii)
-
In the **Permission Set Assignments **section, click **Edit Assignments**.
[See image.](#seeimagesalesforce-civ)
The **Permission Sets** window appears.
-
In the **Permission Sets** window, under **Available Permission Sets**, select the permission set you configured in [Step b](#salesforce-create-permission-set), and click **Add**. In this example, it's Zscaler SaaS Connector User.
[See image.](#seeimagesalesforce-cv)
- Click **Save**.
[]![Screenshot highlighting the Users menu.](/downloads/zia/adding-saas-application-tenants/Salesforce-Users-Menu.png)
[]![Screenshot highlighting the name of the user in the Full Name column.](/downloads/zia/adding-saas-application-tenants/Salesforce-All-Users-Full-Name-Column.png)
[]![The Salsforce CRM Content User option in the User Details section.](/downloads/zia/adding-saas-application-tenants/Salesforce-User-Details-Salesforce-CRM-Content-User.png)
[]![Screenshot highlighting the Edit Assignments button in the Permission Set Assignments section.](/downloads/zia/adding-saas-application-tenants/Salesforce-Permission-Set-Assignments.png)
[]![Screenshot of the Zscaler SaaS Connector User permission set added in the Enabled Permission Sets section.](/downloads/zia/adding-saas-application-tenants/Salesforce-User-Permission-Set-Assignments.png)
[]To configure the Salesforce CRM Content settings:
-
In the left-side navigation, go to **Feature Settings** > **Salesforce Files** > **Salesforce CRM Content**.
[See image.](#seeimagesalesforce-di)
-
Select the following Salesforce CRM Content checkboxes:
- **Enable Salesforce CRM Content**
- **Autoassign feature licenses to existing and new users**
- **Files user interface allows sharing files with libraries**
[See image.](#seeimagesalesforce-dii)
- Click **Save**.
[]![The Salesforce CRM Content menu.](/downloads/zia/adding-saas-application-tenants/Salesforce-CRM-Content-Menu.png)
[]![The configured settings on the Salesforce CRM Content page](/downloads/zia/adding-saas-application-tenants/Salesforce-CRM-Content-Page.png)
[]To configure the application connector:
-
In the left-side navigation, go to **Apps** > **App Manager**.
[See image.](#seeimagesalesforce-ei)
-
Click the down arrow icon for the Zscaler SaaS Connector application.
[See image.](#seeimagesalesforce-eii)
-
Click **Manage**.
[See image.](#seeimagesalesforce-eiii)
-
Click **Edit Policies**.
[See image.](#seeimagesalesforce-eiv)
The **Connected App Edit** window appears.
-
In the **Connected App Edit** window:
- **Permitted Users**: Select **Admin approved users are pre-authorized**.
- **IP Relaxation**: Select **Relax IP restrictions**.
- **Refresh Token Policy**: Ensure **Refresh token is valid until revoked** is selected.
[See image.](#seeimagesalesforce-ev)
- Click **Save**.
-
In the **Profiles **section, click **Manage Profiles**.
[See image.](#seeimagesalesforce-evii)
The **Application Profile Assignment** window appears.
-
In the **Application Profile Assignment** window, select the **System Administrator** checkbox.
[See image.](#seeimagesalesforce-eviii)
- Click **Save**.
-
In the **Permission Sets **section, click **Manage Permission Sets**.
[See image.](#seeimagesalesforce-ex)
The **Application Permission Set Assignment** window appears.
-
In the **Application Permission Set Assignment** window, select the permission set you configured in [Step b](#salesforce-create-permission-set). In this example, it's Zscaler SaaS Connector User.
[See image.](#seeimagesalesforce-exi)
- Click **Save**.
- In the Business Insights Admin Portal, under** Tenant Name**, enter a name for the application tenant.
- Click **Next**.
-
Under **Tenant Type**, select the appropriate tenant type based on your deployment:
- **Sandbox Account**: This option allows you to access Salesforce from the [test.salesforce.com](http://test.salesforce.com) URL, where you can test your changes without affecting your customers until you move it to your production environment.
- **Production Account**: This option allows you to access Salesforce from the [login.salesforce.com](login.salesforce.com) URL, where your changes affect your customers directly as they are applied to your production environment.
You can add both tenant types separately, but you can't change from a sandbox tenant type to production, or vice versa.
-
Under **Salesforce Admin Email ID**, enter your admin email ID used to log in to the Salesforce portal.
[See image.](#seeimagesalesforce-exiii)
-
Click **Next**.
The Business Insights service begins to retrieve your subscription details and establish an API connection. This might take a few minutes or hours. After the connector is configured successfully for the application, you can enter the subscription details.
You can navigate away from the page while the Business Insights service establishes the connection; you're notified after the connector is configured successfully.
- Complete the following subscription fields:
- **Purchased Seats**: The number of seats purchased as part of the subscription.
- **Assigned Seats**: The number of seats assigned to the users from the purchased seats.
- **Per User License Cost**: The cost incurred to buy one seat per month.
- **Contract Start Date**: The start date of the subscription.
- **Contract End Date**: The end date of the subscription.
- Click **Complete**.
[]![Screenshot highlighting the App Manager menu](/downloads/zia/adding-saas-application-tenants/Salesforce-App-Manager-menu.png)
[]![Screenshot highlighting the down arrow icon for ZscalerSaaSConnectorZSBeta01.](/downloads/zia/adding-saas-application-tenants/Salesforce-Lightning-Experience-App-Manager-Down-Arrow-Icon.png)
[]![Screenshot of the Manage option for ZscalerSaaSConnectorZSBeta01.](/downloads/zia/adding-saas-application-tenants/Salesforce-Manage-Option.png)
[]![Screenshot highlighting the Edit Policies button on the App Manager page.](/downloads/zia/adding-saas-application-tenants/Salesforce-ZscalerSaaSConnector-Edit-Policies.png)
[]![Screenshot of the configured Connected App Edit window.](/downloads/zia/adding-saas-application-tenants/Salesforce-Connected-App-Edit-window.png)
[]![Screenshot highlighting the Manage Profiles button in the Profiles section.](/downloads/zia/adding-saas-application-tenants/Salesforce-ZscalerSaaSConnector-Manage-Profiles.png)
[]![Screenshot highlighting the System Administrator profile in the Application Profile Assignment window.](/downloads/zia/adding-saas-application-tenants/Salesforce-Application-Profile-Asssignment-System-Administrator.png)
[]![Screenshot highlighting the Manage Permission Sets button in the Permission Sets section.](/downloads/zia/adding-saas-application-tenants/Salesforce-ZscalerSaaSConnector-Manage-Permission-Sets.png)
[]![Screenshot of the Zscaler SaaS Connector User permission set in the Application Permission Set Assignment window.](/downloads/zia/adding-saas-application-tenants/Salesforce-Application-Permission-Set-Asssignment-window.png)
[]![Screenshot of the Salesforce Admin Email ID field in the Enter the Salesforce Admin Email ID section.](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-SF-ID.png)
[]To configure ServiceNow:
- [a. Verify the OAuth 2.0 plugin is active.](#verify-oauth-plugin-active)
- [b. Verify the OAuth property is active.](#verify-oauth-property-active)
- [c. Configure an OAuth client application.](#configure-oauth-application)
- [d. Configure ServiceNow in Business Insights.](#add-servicenow-tenant)
The application is successfully onboarded. To learn more about the steps in ServiceNow, refer to the [ServiceNow documentation](https://docs.servicenow.com/).
[]To verify the the OAuth 2.0 plugin is installed and active:
- Log in to your ServiceNow instance.
-
Go to **System Applications** > **All Available Applications** > **All**.
[See image.](#seeimageservicenow-aii)
-
Enter `OAuth 2.0` in the search field. The OAuth 2.0 plugin appears. Ensure it's installed.
[See image.](#seeimageservicenow-aiii)
If the plugin isn't installed, click **Install** and then **Activate**.
[]![The All menu under System Applications in the ServiceNow portal.](/downloads/zia/adding-saas-application-tenants/ServiceNow-All-Menu.png)
[]![The OAuth 2.0 plugin is installed in ServiceNow.](/downloads/zia/adding-saas-application-tenants/ServiceNow-OAuth-2_0-Plugin-Installed.png)
[]To verify that the OAuth property is active:
-
In the **Filter navigator**, search for `sys_properties.list` and press **Enter** on your keyboard.
[See image.](#seeimageservicenow-bi)
-
On the **System Properties** page, enter `com.snc.platform.security.oauth.is.active` in the search bar and press **Enter** on your keyboard.
[See image.](#seeimageservicenow-bii)
-
Ensure that the **Value** column for the **com.snc.platform.security.oauth.is.active** property is **true**.
[See image.](#seeimageservicenow-biii-0)
If it's not, in the **Name** column, click **com.snc.platform.security.oauth.is.active**, enter `true` in the **Value **field, and then click **Update**.
[See image.](#seeimageservicenow-biii-1)
[]![sys_properties.list entered in the ServiceNow Filter navigator.](/downloads/zia/adding-saas-application-tenants/ServiceNow-sys_properties_list-menu.png)
[]![com.snc.platform.security.oauth.is.active property entered in the search bar on the System Properties page.](/downloads/zia/adding-saas-application-tenants/ServiceNow-System-Properties-Search-Bar.png)
[]![true highlighted in the Value column for the com.snc.platform.security.oauth.is.active property.](/downloads/zia/adding-saas-application-tenants/ServiceNow-System-Properties-Value-Column.png)
[]![The Value field highlighted in the System Property window. ](/downloads/zia/adding-saas-application-tenants/ServiceNow-System-Property-Value-Field.png)
[]To configure an OAuth client application:
-
Go to **System OAuth** > **Application Registry**.
[See image.](#seeimageservicenow-ci)
-
Click **New**.
[See image.](#seeimageservicenow-cii)
-
Click **Create an OAuth API endpoint for external clients**.
[See image.](#seeimageservicenow-ciii)
The **Application Registries New Record** window appears.
-
[]In the **Application Registries New Record** window:
- **Name**: Enter a name for the OAuth client application. In this example, it's Zscaler SaaS Application Tenant.
- **Client ID**: Copy the client ID of the application. You need it for Step ii of [d. Add ServiceNow as a Tenant](#servicenow-step-dii).
- **Client Secret**: The shared secret of the application, which the ServiceNow instance and the OAuth client application use to authorize their communication. The secret generates after you submit this application registry.
- **Refresh Token Lifespan**: The default lifespan is 8,640,000 seconds (100 days). Zscaler recommends changing it to a larger value, such as 157,700,000 seconds (5 years) because you'll need to configure ServiceNow as a new tenant after the refresh token expires.
- **Access Token Lifespan**: The default value is 1,800 seconds (30 minutes). Zscaler recommends changing it to a larger value, such as 86,400 seconds (24 hours).
[See image.](#seeimageservicenow-civ)
- Click **Submit**.
-
On the **Application Registries** page, in the **Name** column, click the name of the configured OAuth client application. In this example, it's Zscaler SaaS Application Tenant.
[See image.](#seeimageservicenow-cvi)
The **Application Registries** window appears.
-
In the **Application Registries** window, click the **Lock** icon for **Client Secret**.
[See image.](#seeimageservicenow-cvii)
-
[]Copy the value from the **Client Secret** field. You need it for Step iii of [d. Add ServiceNow as a Tenant](#servicenow-step-dii).
[See image.](#seeimageservicenow-cviii)
[]![The Application Registry menu in the ServiceNow portal.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registry-Menu.png)
[]![The New button on the Application Registries page.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registries-New-Button.png)
[]![The Create an OAuth API endpoint for external clients option on the OAuth application page.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Create-an-OAuth-API-Endpoint-for-External-Clients.png)
[]![The configured Application Registries New Record window.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registries-New-Record-Window.png)
[]![The OAuth client application name in the Name column on the Application Registries page.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registries-Name-Column.png)
[]![The Lock icon for the Client Secret in the Application Registries window of the OAuth client application.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registries-Client-Secret-Lock-Icon.png)
[]![The visible Client Secret on the Application Registries window of the OAuth client application.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Client-Secret.png)
[]To configure ServiceNow:
- In the Business Insights Admin Portal, under** Tenant Name**, enter a name for the SaaS application tenant.
- Click **Next**.
- []Complete the following fields:
- **Client ID**: Enter the client ID you copied in [c. Configure an OAuth Client Application](#servicenow-step-civ).
- **Client Secret**: Enter the client secret you copied in [c. Configure an OAuth Client Application](#servicenow-step-cviii).
- **Instance URL**: Enter the URL used to log in to your ServiceNow instance.
- **User ID**: Enter the user ID of the user account used to configure the OAuth client application.
- **User Password**: Enter the password of the user account used to configure the OAuth client application.
-
**ServiceNow Admin Email ID:** Enter the admin email ID used to log in to your ServiceNow instance.
[See image.](#sn-info)
-
Click **Authorize**.
The Business Insights service begins to retrieve your subscription details and establish an API connection. This might take a few minutes or hours. After the connector is configured successfully for the application, you can enter the subscription details.
You can navigate away from the page while the Business Insights service establishes the connection; you're notified after the connector is configured successfully.
- Complete the following subscription fields:
- **Purchased Seats**: The number of seats purchased as part of the subscription.
- **Assigned Seats**: The number of seats assigned to the users from the purchased seats.
- **Per User License Cost**: The cost incurred to buy one seat per month.
- **Contract Start Date**: The start date of the subscription.
- **Contract End Date**: The end date of the subscription.
- Click **Complete**.
[]![OAut client application details](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Bussiness-Insights-oauth.png)
[]To configure Slack:
- Under** Tenant Name**, enter a name for the application tenant.
-
Click **Next, **then **Provide Admin Credentials**.
[See image.](#slack-provide-access)
The Slack portal appears.
-
Log in to Slack.
You are redirected to a permissions page.
-
From the top right drop-down menu, select the workspace of your organization. Ensure you are not selecting the workspace under the **Your organizations** section, and instead select from the **Other workspaces** section.
[See image.](#slack-workspace)
-
Review the required permissions for the Business Insights service to access Slack, then click **Allow**.
[See image.](#slack-permissions)
-
In the Business Insights Admin Portal, under **Slack Admin Email ID**, enter the admin email ID used to log in to the Slack portal.
[See image.](#slack-admin-email)
-
Click **Next**.
The Business Insights service begins to retrieve your subscription details and establish an API connection. This might take a few minutes or hours. After the connector is configured successfully for the application, you can enter the subscription details.
You can navigate away from the page while the Business Insights service establishes the connection; you're notified after the connector is configured successfully.
- Complete the following subscription fields:
- **Purchased Seats**: The number of seats purchased as part of the subscription.
- **Assigned Seats**: The number of seats assigned to the users from the purchased seats.
- **Per User License Cost**: The cost incurred to buy one seat per month.
- **Contract Start Date**: The start date of the subscription.
- **Contract End Date**: The end date of the subscription.
- Click **Complete**.
The application is successfully onboarded.
[]![The Tenant Name field in the Name the SaaS Application Tenant section.](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-slack-provide-admin-access.png)
[]![Select Slack Workspace](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-slack-workspace.png)
[]![The Permissions pagein Slack](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-slack-permissions.png)
[]![The Provide Admin Email ID field](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Business-Insights-slack-ID.png)
[]![Connect App Button](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Bussiness-insights-connect-appe.png)
[]![Add App Icon](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Bussiness-insights-add-app.png)
[]![Add app icon](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Bussiness-insights-add-app-cost-saving.png)
[]![Choose SaaS Application page](/downloads/zia/dashboard-analytics/adding-saas-application-tenants-zbi/Bussiness-insights-select-connect-apppng.png)