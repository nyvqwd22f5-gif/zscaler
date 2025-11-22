# Configuring Microsoft Teams Call Quality for ZDX
Source: https://help.zscaler.com/zdx/configuring-microsoft-teams-call-quality-zdx
PDF: https://help.zscaler.com/pdf/com/en/1386186.pdf

You can configure Microsoft Teams Call Quality to monitor audio calls among two or more users. Call Quality can help you pinpoint issues that are unique to a device or the network by working in parallel with its Cloud Path probe. When onboarding a Microsoft Teams Call Quality tenant for the first time, a ZDX Autosense Cloud Path probe is automatically generated that detects the destination IP address. To learn more, see [Understanding Microsoft Teams Call Quality for ZDX](/zdx/understanding-microsoft-teams-call-quality-zdx).
If your organization does not use an email ID to access Microsoft Teams Call Quality, log in with your Zscaler Client Connector Login ID to ensure successful alignment between Microsoft and Zscaler service.
Prerequisites
Verify the following before onboarding a Microsoft Teams Call Quality tenant:
- You're running the required versions of Zscaler Client Connector and ZDX Module to configure a ZDX Autosense probe. To learn more, see [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility#ZDXAutosenseZoom).
- Your ZDX subscription level supports ZDX Autosense. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- You've enabled the Windows Filtering Platform (WFP) driver installation setting for ZDX Autosense in the Zscaler Client Connector Portal. To learn more, see [Configuring Zscaler Client Connector App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles).
- You've enabled the setting to collect device hostname information in the Zscaler Client Connector Portal. To learn more, see [Configuring Zscaler Client Connector to Collect Hostnames](/client-connector/configuring-zscaler-client-connector-collect-hostnames).
Adding a Tenant
In the ZDX Admin Portal:
- Go to **Configuration > Applications**.
[See image.](#predefined-apps)
- Under **Microsoft Teams Call Quality** in the** **Predefined Applications list, click **Authenticate**.
[See image.](#add-tenant)
- Sign in and enter your password. Verify your identity if multi-factor authentication is required.
[See image.](#ms-credentials)
To authenticate O365 for application integration, you must be a Global Administrator in the Azure Active Directory (AD). To learn more, refer to the [Azure AD documentation](https://docs.microsoft.com/en-us/azure/active-directory/roles/permissions-reference).
- Accept the resource permissions from Microsoft.
[See image.](#ms-permission)
A **Teams Meetings Tenant** is automatically added under **Microsoft Teams Call Quality**.
To manually add another tenant:
- Click **Add New Tenant**.
- In the **Add New Microsoft Teams Call Quality Tenant** window, enter the tenant name and configure the **Status **to **Enable**.
[See image.](#tenant-modal)
- In the Monitoring Criteria section, use the filters to gather Call Quality metrics for selected ZDX users. Meetings are monitored only for these users. Selections among the filters are cumulative, whereas selections within a single filter are not cumulative. For example, if you select DevTest and Service Admin in the User Groups filter, and then select Engineering and IT in the Departments filter, you can then identify users who belong to the DevTest or Service Admin user group *and *the Engineering or IT department.
Meetings are monitored and displayed only for your selected ZDX users in Monitoring Criteria.
[See image.](#monitor-criteria)
- In the Authentication section, click **Microsoft Office 365 Authentication**.
You must authenticate with Microsoft before you can save the new tenant. You must also reauthenticate whenever you update the Monitoring Criteria settings.
- Click **Save**.
- (Optional) Select the tenant name and click **Validate **within the dialog window to verify your setup with Microsoft was successful.
[See image.](#validate-button)
Adding a Probe
To manually add a new probe for Microsoft Teams Call Quality after a tenant has been onboarded:
When onboarding a tenant for the first time, a ZDX Autosense Cloud Path probe is automatically added under **Microsoft Teams Call Quality**.
- Go to **Configuration > Applications**.
- Under **Microsoft Teams Call Quality **in the** **Predefined Applications list, click **Add New Probe**.
[See image.](#add-probe)
- In the **Add New Probe** window, enter a probe name, and select your probe type as either **Cloud Path **or **Autosense Cloud Path**. Then click **Next**:
[See image.](#add-probe-popup)
- [Adding the Cloud Path Probe Type](#cp-probe-type)
- [Adding the Autosense Cloud Path Probe Type](#acp-probe-type)
[]To add the Cloud Path Probe Type:
- Verify or configure the fields under **Probing Criteria** and **Exclusion Criteria**. To learn more, see [Configuring a Probe](/zdx/configuring-probe).
- Click **Next**.
- On the **Additional Parameters** tab, verify the **Cloud Path Host** was automatically created as `worldaz.tr.teams.microsoft.com`. This field is for a fully qualified domain name.
[See image.](#additional-parameters)
- Click **Next**.
- On the **Review **tab, confirm your configuration, and click **Submit**.
[]To add the Autosense Cloud Path Probe Type:
A WFP driver installation is required within the Zscaler Client Connector Portal. To learn more, see [Configuring Zscaler Client Connector App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles).
[See image.](#cp-host-auto-caution)
- Verify or configure the fields under **Probing Criteria** and **Exclusion Criteria**. To learn more, see [Configuring a Probe](/zdx/configuring-probe).
- Click **Next**.
- On the **Additional Parameters** tab, verify the **Cloud Path Host** was automatically discovered via ZDX Autosense.
[See image.](#cp-host-auto)
- Click **Next**.
- On the **Review **tab, confirm your configuration, and click **Submit**.
Disabling the Tenant
To disable the Microsoft Teams Call Quality tenant:
- Go to **Configuration > Applications**.
- Under **Microsoft Teams** **Call Quality** in the** **Predefined Applications list, click the **Edit **icon for the tenant or select the tenant name in the table.
- In the dialog window, configure the **Status** to **Disable**.
- Click **Save**.
Deleting the Tenant
To delete the Microsoft Teams Call Quality tenant:
- Go to **Configuration > Applications**.
- Under **Microsoft Teams Call Quality** in the** **Predefined Applications list, click the **Delete **icon for the tenant.
- In the dialog window, confirm you want to delete the tenant.
[]![Microsoft Teams Call Quality shown in Predefined Applications](/downloads/zdx/configuration/applications/configuring-microsoft-teams-call-quality-zdx/zdx-msteams-cqm-predefined-apps3.png)
[]![Authenticate Microsoft Teams Call Quality](/downloads/zdx/configuration/applications/configuring-microsoft-teams-call-quality-zdx/zdx-autosense-teams-authenticate.png)
[]![Add tenant for Microsoft Teams Call Quality](/downloads/zdx/configuration/applications/configuring-microsoft-teams-call-quality-zdx/zdx-msteams-cqm-add-tenant4.png)
[]![Pop-up to filter monitoring criteria](/downloads/zdx/configuration/applications/configuring-microsoft-teams-call-quality-zdx/zdx-msteams-cqm-select-filter4.png)
[]![Microsoft sign-in screen](/downloads/zdx/analytics/configuring-microsoft-teams-call-quality-zdx/ZDX-msteams-cqm-ms-credentials.png)
[]![Screen to accept Microsoft permissions](/downloads/zdx/analytics/configuring-microsoft-teams-call-quality-zdx/ZDX-msteams-cqm-accept-app-terms4_0.png)
[]![Button to validate authentication](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-microsoft-teams-call-quality-zdx-draft-b/zdx-msteams-cqm-validate.png)
[]![Link to Add New Probe](/downloads/zdx/configuration/applications/configuring-microsoft-teams-call-quality-zdx/zdx-autosense-teams-add-new-probe.png)
[]![Pop-up window to Add Probe Type](/downloads/zdx/configuration/applications/configuring-microsoft-teams-call-quality-zdx/zdx-autosense-teams-probe-type.png)
[]![Enter Cloud Path Host on Additional Parameters tab](/downloads/zdx/configuration/applications/configuring-microsoft-teams-call-quality-zdx/zdx-autosense-teams-cp-host.png)
[]![Autosense Cloud Path Host](/downloads/zdx/configuration/applications/configuring-microsoft-teams-call-quality-zdx/zdx-autosense-teams-cp-host-auto.png)
[]![Caution shown when adding a ZDX Autosense Probe Type](/downloads/zdx/configuration/applications/configuring-microsoft-teams-call-quality-zdx/zdx-autosense-teams-cp-host-auto-caution.png)