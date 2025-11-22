# About SaaS Application Tenants
Source: https://help.zscaler.com/unified/about-saas-application-tenants
PDF: https://help.zscaler.com/pdf/com/en/1493536.pdf

Zscaler Data at Rest Scanning provides visibility and security for sanctioned SaaS applications used in your organization. You can authorize sanctioned SaaS applications with Zscaler by adding them as tenants. You can see general information about each tenant, such as the authorization status and configured policies.
SaaS Application Tenants provides the following benefits and allows you to:
- Add or edit SaaS application tenants.
- View general information about each tenant.
- Manage SaaS application sites and site groups to use in DLP policies.
About the Add SaaS Application Tenant Page
On the SaaS Application Tenants page (Policies > Common Configuration > Out-of-Band CASB > SaaS Application Tenants), you can do the following:
- Go to the [Add SaaS Application Tenant](/unified/adding-saas-application-tenants) page.
- Go to the [Manage SaaS Application Components](/unified/manage-saas-application-components) page.
- [Add a SaaS application tenant](/unified/adding-saas-application-tenants).
- Search for a configured SaaS application tenant.
- View a list of all configured SaaS application tenants. For each tenant, you can see the following:
- **Application**: The type of sanctioned SaaS application (e.g., Box, Microsoft OneDrive, SharePoint, etc.).
- **Tenant Name**: The name of the SaaS application tenant that is displayed when configuring the [DLP policy](/unified/about-saas-security-api-dlp), [Malware Detection policy](/unified/about-saas-security-api-malware-detection), and [Scan Configuration](/unified/about-saas-security-api-scan-configuration).
- **Status**: The status of the SaaS application tenant. The following states appear:
- **Active**: The tenant is in use. Policies are enforced for this SaaS application.
- **Inactive**: The tenant is not in use. Policies are not enforced for this SaaS application.
- **Validation Failed**: There were issues validating the admin credentials and authorizing the SaaS application. To learn more, see [SaaS Application Validation Error Codes​​​​​](/unified/saas-application-validation-error-codes).
-
**Reauthorization Required**: Edit the tenant, and click **Reauthorize** to log in to the SaaS application and give Zscaler access to it.
[See image.](#seeimage-reauth)
If you're reauthorizing GitHub, you must revoke the existing Zscaler OAuth application authorization in the GitHub portal. To learn more, refer to the [GitHub documentation](https://docs.github.com/en/github/authenticating-to-github/reviewing-your-authorized-integrations).
- **Last Modified On**: The last time the SaaS application tenant was edited.
- **Last Modified By**: The name of the admin who last edited the SaaS application tenant.
-
**Owner**: Indicates whether the SaaS application tenant was created in Internet & SaaS or Digital Experience Monitoring. If the tenant was created in Digital Experience Monitoring, the delete functionally is removed in Internet & SaaS. Edits in Internet & SaaS for tenants created in Digital Experience Monitoring are allowed on any fields except those relating to Workflow Automation.
To learn more about adding or editing applications in Digital Experience Monitoring, see [About Applications](/unified/about-applications-0).
- **Policy Configured**: The Data at Rest Scanning policies ([DLP](/unified/about-saas-security-api-dlp) and [Malware Detection](/unified/about-saas-security-api-malware-detection)) configured for the SaaS application tenant.
-
**External Trusted Domains**: Displays the total number of added [external trusted domains](/unified/adding-saas-application-tenants). Click to view a list of the domains. This only applies to email SaaS application tenants.
[See image.](#seeimage-domains)
-
**External Trusted Users**: Displays the total number of added [external trusted users](/unified/adding-saas-application-tenants). Click to view a list of the users. This only applies to email SaaS application tenants.
[See image.](#seeimage-users)
- Edit a SaaS application tenant.
- [Modify the table and its columns](/unified/using-tables).
- Delete the SaaS application tenant.
![Screenshot highlighting the features of the SaaS Application Tenants page in the ZIA Admin Portal.](/downloads/zia/policies/saas-security-api/saas-application-tenants/about-saas-application-tenants/About%20SaaS%20Application%20page.png)
[]![Screenshot highlighting the Reauthorize link in the Edit window.](/downloads/zia/policies/saas-security-api/saas-application-tenants/about-saas-application-tenants/zia-saas-application-edit-window-reauthorize.png)
[]![Screenshot of the External Trusted Domains window.](/downloads/zia/about-saas-application-tenants/zia-external-trusted-domains-window.png)
[]![Screenshot of the External Trusted Users window.](/downloads/zia/about-saas-application-tenants/zia-external-trusted-users-window.png)