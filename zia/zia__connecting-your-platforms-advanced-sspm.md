# Connecting Your Platforms to Advanced SSPM
Source: https://help.zscaler.com/zia/connecting-your-platforms-advanced-sspm
PDF: https://help.zscaler.com/pdf/com/en/1517116.pdf

You can connect your platforms to Zscaler [Advanced SaaS Security Posture Management (SSPM)](/zia/what-advanced-posture-management) to continuously monitor and correct Software as a Service (SaaS) security posture and ensure regulatory compliance is maintained across the organization.
Connecting your platform to Advanced SSPM is dependent on your license. If you have questions regarding the license, contact your Zscaler Account team.
To connect a platform to Advanced SSPM:
-
[Sign in to the Zscaler 3rd-Party App Governance Admin Portal](/zia/accessing-and-navigating-3rd-party-app-governance-admin-portal) and click the **Connect** icon.
[See image.](#Connect-Button)
The **Integrations** window appears.
-
In the **Integrations** window, click **Add **next to the platform you want to connect to Advanced SSPM.
[See image.](#Integrations-Window)
- Select the **Identity Provider** from the drop-down menu. You can select **Okta** or **Microsoft**.
- Enter the username and password associated with your account.
- Enter the** **time-based one-time password (TOTP) Key and login URL.
- (Optional) Enter the tenant name.
- Click **Connect**.
[See image.](#Add-Integration)
For onboarding API-based platforms, you are redirected to the **Add SaaS Application Tenant** page in the ZIA Admin Portal. To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
After connection is achieved, it might take a while to pull and ingest all relevant application data depending on the size of your tenant. During this time, a message displays indicating that the integration is still being processed. After integration is completed, a success message appears, and the number of integrations, integration status, first connected time, and last synced time are updated. If the connection fails, an error message appears displaying the reason for the failure. Contact Zscaler Support if you require further assistance.
You can connect the following platforms to Advanced SSPM:
- Asana
- AuthO
- Calendly
- ClickUp
- Databricks
- JFrog
- Miro
- monday
- MuleSoft
- OneLogin
- Smartsheet
- Snowflake
- Zendesk
[]![The Integrations Window allows you to connect new platforms to Advanced SSPM](/downloads/zia/policies/saas-security/posture-management/posture-management-advanced/connecting-your-platforms-advanced-sspm/Integrations_Add_Redirect.png)
[]![Adding authentication credentials in Integrations Window](/downloads/tech-pubs-drafts/zia-draft-articles/connecting-your-platforms-advanced-sspm-draft-doc-58249/Add_Integration_Credentials_New.png)
[]![Connect Icon allows you to add new integrations](/downloads/zia/policies/saas-security/posture-management/posture-management-advanced/connecting-your-platforms-advanced-sspm/Connect_Button.png)