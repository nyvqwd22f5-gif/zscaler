# Adding a SaaS Application Tenant for Workflow Automation
Source: https://help.zscaler.com/business-insights/adding-saas-application-tenant-workflow-automation
PDF: https://help.zscaler.com/pdf/com/en/1500016.pdf

You can integrate SaaS applications with Workflow Automation for the Business Insights service by adding them as tenants.
To add a SaaS application tenant:
- Go to **Administration **> **Workflow Integration**.
-
Click **Add SaaS Application Tenant**.
The **Add SaaS Application Tenant** page appears.
-
Under **Choose the SaaS Application Provider**, search for or choose from one of the SaaS applications you want to integrate for Workflow Automation.
[See image.](#seeimage3)
- Under **Name the SaaS Application Tenant**, enter a name for the SaaS application tenant. It must be unique.
-
Under **Onboard SaaS Application for**, select **Workflow Automation**.
[See image.](#enable-workflow)
- Complete the specific configuration steps for your chosen application:
- [ServiceNow](#servicenow)
- Click **Save**.
[]![Add SaaS Application Tenant page](/downloads/business-insights/authentication-administration/about-saas-application-tenants/adding-saas-tenants.png)
[]To configure ServiceNow as a tenant, you must have a ServiceNow user account with an admin role.
To configure ServiceNow:
- [a. Verify the OAuth 2.0 plugin is active.](#verify-oauth-plugin-active)
- [b. Verify the OAuth property is active.](#verify-oauth-property-active)
- [c. Configure an OAuth client application.](#configure-oauth-application)
- [d. Add ServiceNow as a tenant.](#add-servicenow-tenant)
To learn more about the steps in ServiceNow, refer to the [ServiceNow documentation](https://docs.servicenow.com/).
To learn more about adding additional object types for ServiceNow tenants, see [Adding Object Types for ServiceNow Tenants](/zia/adding-object-types-servicenow-tenants).
[]To verify the OAuth 2.0 plugin is installed and active:
- Log in to your ServiceNow instance.
-
Go to **System Application** > **All Available Applications** > **All**.
[See image.](#seeimageservicenow-aii)
-
Enter `OAuth 2.0` in the search bar. The OAuth 2.0 plugin appears. Ensure it's **Installed**.
[See image.](#seeimageservicenow-aiii)
If the plugin isn't installed, click **Install** and then **Activate**.
[]![The All menu under System Applications in the ServiceNow portal.](/downloads/zia/adding-saas-application-tenants/ServiceNow-All-Menu.png)
[]![The OAuth 2.0 plugin is installed in ServiceNow.](/downloads/zia/adding-saas-application-tenants/ServiceNow-OAuth-2_0-Plugin-Installed.png)
[]To verify that the OAuth property is active:
-
In the **Filter navigator**, enter `sys_properties.list` and press `Enter` on your keyboard.
[See image.](#seeimageservicenow-bi)
- On the **System Properties** page, enter the following property in the search bar and press `Enter` on your keyboard:
com.snc.platform.security.oauth.is.active
[See image.](#seeimageservicenow-bii)
-
Ensure that the **Value** column for the **com.snc.platform.security.oauth.is.active** property is **true**.
[See image.](#seeimageservicenow-biii-0)
If it's not, in the **Name** column, click **com.snc.platform.security.oauth.is.active**, enter `true` for the **Value**, and then click **Update**.
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
- **Name**: Enter a name for the OAuth client application. In this example, it's `Zscaler SaaS Application Tenant`.
- **Client ID**: Copy the client ID of the application. You need it for [a later step](#servicenow-step-dii).
- **Client Secret**: The shared secret of the application, which the ServiceNow instance and the OAuth client application use to authorize their communication. The secret generates after you submit this application registry.
- **Refresh Token Lifespan**: The default lifespan is 8,640,000 seconds (100 days). Zscaler recommends changing it to a larger value, such as 157,700,000 seconds (5 years) because you'll need to configure ServiceNow as a new tenant after the refresh token expires.
- **Access Token Lifespan**: The default value is 1,800 seconds (30 minutes). Zscaler recommends changing it to a larger value, such as 86,400 seconds (24 hours).
[See image.](#seeimageservicenow-civ)
- Click **Submit**.
-
On the **Application Registries** page, in the **Name** column, click the name of the configured OAuth client application. In this example, it's **Zscaler SaaS Application Tenant**.
[See image.](#seeimageservicenow-cvi)
The **Application Registries** window appears.
-
In the **Application Registries** window, click the **Lock** icon for **Client Secret**.
[See image.](#seeimageservicenow-cvii)
-
[]Copy the client secret. You need it for [a later step](#servicenow-step-dii).
[See image.](#seeimageservicenow-cviii)
[]![The Application Registry menu in the ServiceNow portal.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registry-Menu.png)
[]![The New button on the Application Registries page.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registries-New-Button.png)
[]![The Create an OAuth API endpoint for external clients option on the OAuth application page.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Create-an-OAuth-API-Endpoint-for-External-Clients.png)
[]![The configured Application Registries New Record window.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registries-New-Record-Window.png)
[]![The OAuth client application name in the Name column on the Application Registries page.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registries-Name-Column.png)
[]![The Lock icon for the Client Secret in the Application Registries window of the OAuth client application.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registries-Client-Secret-Lock-Icon.png)
[]![The visible Client Secret on the Application Registries window of the OAuth client application.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Client-Secret.png)
[]To add ServiceNow as a SaaS application tenant:
-
[]Under **Register the OAuth Application**:
- **Client ID**: Enter the client ID that [you previously copied](#servicenow-step-civ).
- **Client Secret**: Enter the Client Secret that [you previously copied](#servicenow-step-cviii).
- **Instance URL**: Enter the URL used to log in to your ServiceNow instance.
- **User ID**: Enter the user ID of the user account used to configure the OAuth client application.
- **User Password**: Enter the password of the user account used to configure the OAuth client application.
[See image.](#seeimageservicenow-dii)
-
Under **Enter the ServiceNow Admin Email ID**, enter the admin email ID used to log in to your ServiceNow instance.
[See image.](#seeimageservicenow-diii)
-
Under **Authorize the SaaS Application**, click **Authorize**.
[See image.](#seeimageservicenow-div)
[]![The Register the OAuth Application section on the Add SaaS Application Tenant page.](/downloads/zia/adding-saas-application-tenants/ZIA-Register-the-OAuth-Application.png)
[]![The ServiceNow Admin Email ID field in the Enter the ServiceNow Admin Email ID section.](/downloads/zia/adding-saas-application-tenants/ZIA-Enter-ServiceNow-Admin-Email-ID.png)
[]![The Authorize button in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Authorize-ServiceNow.png)
[]![Enable Workflow Automation Option](/downloads/business-insights/authentication-administration/adding-saas-application-tenant-workflow-automation/Business-Insights-enable-workflow-automation_0.png)