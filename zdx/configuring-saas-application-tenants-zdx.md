# Configuring SaaS Application Tenants for ZDX
Source: https://help.zscaler.com/zdx/configuring-saas-application-tenants-zdx
PDF: https://help.zscaler.com/pdf/com/en/1499826.pdf

You can onboard SaaS application tenants in ZDX to use when integrating with Workflow Automation. Tenant onboarding allows you to be alerted to SaaS application incidents, and ZDX integration with ServiceNow specifically creates individual tickets for Data Loss Prevention (DLP) and alerts, based on Workflow Automation mapping criteria. To learn more, see [About Integrations](/zdx/about-integrations) and [Step-by-Step Configuration Guide for Workflow Automation](/workflow-automation/step-step-configuration-guide-workflow-automation).
Prerequisites
Before you configure a SaaS application tenant, ensure your subscription level supports Workflow Automation. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
Configuring a SaaS Application Tenant
To configure a SaaS application tenant for ZDX:
- Go to **Administration **> **Integrations **> **SaaS App Tenants**. A table appears that consolidates current ZDX tenants.
The table provides the following information:
- **Name**: The name of the application tenant.
- **Vendor**: The name of the provider.
- **Last Modified On**: The day and time when the tenant was last edited or added.
- **Status**: The current state of the tenant.
- **Actions**: The options to either edit or delete a ZDX tenant.
[See image.](#tenant-table)
- Click **Add New Integration**.
- Under **Workflow Automation Applications**, select the ServiceNow application, and then click **Next**.
[See image.](#select-provider)
- [Adding a ServiceNow Tenant](#select-servicenow)
[]To add a new tenant for ServiceNow:
- Enter a unique **Tenant Name**.
- Enter the **ServiceNow Admin Email**. This is the admin email used to log in to your ServiceNow instance.
- Click **Next**.
[See image.](#snow-details)
- Enter the OAuth details from ServiceNow to allow Zscaler access.
[See image.](#snow-authorize)
- Click **Authorize**. The **Add **button is enabled if the authorization is successful.
- Click **Add **to add the new tenant.
Editing a Tenant
You can edit ZDX tenants for the following applications:
- [ServiceNow](#edit-servicenow)
[]To edit a ZDX tenant for ServiceNow:
- Go to **Administration **> **Integrations **> **SaaS App Tenants**.
- Click the **Edit **icon within the table for the tenant you want to edit.
- On the **Select a SaaS application Provider** page, click **Next**.
- Under **General**, you can:
- Update the **Tenant Name** to a different unique name.
- Update the **Status**. Click **Enable **or **Disable**.
- Click **Next**.
- On the **Authorize SaaS Application** page, you can edit the OAuth details from ServiceNow.
- Click **Validate **to confirm your updates.
- [Activate your changes](/zdx/saving-and-activating-changes-admin-portal).
Deleting a Tenant
To delete a ZDX tenant:
- Go to **Administration **> **Integrations **> **SaaS App Tenants**.
- Click the **Delete **icon within the table for the tenant you want to delete.
- In the dialog window, confirm you want to delete the tenant.
- [Activate your change](/zdx/saving-and-activating-changes-admin-portal).
[]![Table of SaaS application tenants](/downloads/zdx/configuration/tenant-integrations/configuring-saas-application-tenants-zdx/zdx-saas-integration-tenant-table2.png)
[]![Select a SaaS application provider](/downloads/zdx/configuration/tenant-integrations/configuring-saas-application-tenants-zdx/zdx-saas-integration-select-provider2.png)
[]![SaaS App Details page for ServiceNow](/downloads/zdx/configuration/tenant-integrations/configuring-saas-application-tenants-zdx/zdx-saas-integration-snow-details2.png)
[]![Authorize ServiceNow](/downloads/zdx/configuration/tenant-integrations/configuring-saas-application-tenants-zdx/zdx-saas-integration-snow-authorize2.png)