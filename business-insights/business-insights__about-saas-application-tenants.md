# About SaaS Application Tenants
Source: https://help.zscaler.com/business-insights/about-saas-application-tenants
PDF: https://help.zscaler.com/pdf/com/en/1499936.pdf

The integration of SaaS applications with Workflow Automation for the Business Insights service helps to align your organization's workflows. For example, you can integrate a ServiceNow tenant to create, manage, and track tickets for inactive users observed via [scheduled reports](/business-insights/about-scheduled-reports).
SaaS Application Tenants provides the following benefits and allows you to:
- Add or edit SaaS application tenants to integrate with Workflow Automation for the Business Insights service.
- Manage various incidents using third-party SaaS applications.
About the SaaS Application Tenants Page
On the SaaS Application Tenants page (Administration > Workflow Integration), you can do the following:
- [Add a SaaS application tenant](/business-insights/adding-saas-application-tenant-workflow-automation).
- Search for a configured SaaS application tenant.
- View a list of all configured SaaS application tenants.
- [View elements for each SaaS application tenant](#coulumn-fields)
- [Modify the table and its columns](/business-insights/using-tables-business-insights).
- [Edit a SaaS application tenant](/business-insights/editing-or-deleting-items-business-insights).
- [Delete a SaaS application tenant](/business-insights/editing-or-deleting-items-business-insights).
![SaaS Application Tenants](/downloads/business-insights/authentication-administration/about-saas-application-tenants/Business-Inisghts-SaaS-Aplication-Tenants-Page.png)
- []**Application**: The name of the SaaS application.
- **Tenant Name**: The name of the SaaS application tenant.
- **Status**: The status of the SaaS application tenant. The following statuses can appear:
- **Active**: The tenant is in use.
- **Inactive**: The tenant is not in use.
- **Validation Failed**: There were issues validating the admin credentials and authorizing the SaaS application. To learn more, see [SaaS Application Validation Error Codes​​​​​](/zia/saas-application-validation-error-codes).
- **Reauthorization Required**: Edit the tenant, and click **Reauthorize** to log in to the SaaS application and give Zscaler access to it.
- **Last Modified On**: The last time the SaaS application tenant was edited.
- **Last Modified By**: The name of the admin who last edited the SaaS application tenant.
- **Owner**: Indicates whether the SaaS application tenant was created in Zscaler Internet Access (ZIA) or Zscaler Digital Experience (ZDX).
- **Policy Configured**: The SaaS Security Data At Rest Scanning policies ([DLP](/zia/about-saas-security-api-dlp) and [Malware Detection](/zia/about-saas-security-api-malware-detection)) configured for the SaaS application tenant.
-
**External Trusted Domains**: Displays the total number of added external trusted domains. Click to view a list of the domains. This only applies to email SaaS application tenants.
[See image.](#seeimage-domains)
-
**External Trusted Users**: Displays the total number of added external trusted users. Click to view a list of the users. This only applies to email SaaS application tenants.
[See image.](#seeimage-users)
[]![Screenshot of the External Trusted Domains window.](/downloads/zia/about-saas-application-tenants/zia-external-trusted-domains-window.png)
[]![Screenshot of the External Trusted Users window.](/downloads/zia/about-saas-application-tenants/zia-external-trusted-users-window.png)