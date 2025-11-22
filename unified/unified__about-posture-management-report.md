# About Posture Management Report
Source: https://help.zscaler.com/unified/about-posture-management-report
PDF: https://help.zscaler.com/pdf/com/en/1497546.pdf

SaaS Security Posture Management (SSPM) refers to the practice of systematically assessing, monitoring, and improving the security posture of SaaS applications within an organization. It is a collection of recommended security policies that are enabled for your business requirements. The policies that are enabled for your business requirements are included in the Posture Management Report. This report provides you with the evaluation of the enabled policies against your organization's security posture. By default, all the policies are enabled. You can disable or re-enable any of the supported policies. The disabled policies are not evaluated in the subsequent scans.
To learn more about the SSPM policy statuses, see [Viewing and Managing the Supported SSPM Policies](/unified/viewing-and-managing-supported-sspm-policies).
The type of subscription you have determines the level of evaluation you can perform:
- [SSPM Essentials (without Advanced SSPM license enabled)](#sspm_essentials)
- [SSPM Advanced (with Advanced SSPM license enabled)](#advanced_sspm)
The Posture Management Report provides the following benefits and enables you to:
- Gain visibility and monitor your organization's risk level by your SaaS application's security posture.
- Check your SaaS security posture against various security compliances.
- Analyze and help you remediate your organization's SaaS security posture from potential threats by configuring SaaS applications as per the recommended policies.
[]About the Posture Management Page
On the Posture Management page (Analytics > Internet & SaaS > Analytics > SaaS Security Report > Posture Management), you can do the following:
- Download the report to a PDF file.
- Show or hide the filter options.
-
Filter the report. You can show or hide the filter option from the top right. The following filters are available:
- [Filters](#sspm-filters)
Click **Apply** to update the page with your selections. You can click **Reset** at any time.
-
**Policy Overview**: View the total number of policies for the selected application and the policy status for each. The following statuses appear:
- [Statuses](#status)
- **Compliance**: View the number of policies applicable for each compliance. Hover over the compliance bar to view the split between the passed, failed, and partially passed policies.
- **Risk Level**: View the pie chart for the total number of policies and their risk level (Low, Medium, or High). The pie chart does not show risk levels of disabled policies. You can show or hide the preceding three sections together using the arrow next to** General**.
- Export the Policies table data to an Excel file. The Excel file shows the data as per the filters applied in a preceding step.
- Search for a policy.
- **Policies**: View a list of all the policies. For each policy, you can view the following information:
- **Resource Type**: The resource type for the policy.
- **Policy**: The name of the policy. Click the policy to view the description of the policy in the drawer view shown in the following step.
- **Policy Status**: The status of the policy evaluation. The following statuses appear:
- **Passed**: Your organization's posture control scanned against the policy is correctly configured.
- **Failed**: Your organization's posture control scanned against the policy is incorrectly configured.
- **Partial**: Not all the assets scanned against the policy have posture control configured correctly. For example, your organization has 100 users and you enabled multi-factor authentication (MFA) for a subset of users.
- **Disabled**: The policy is not evaluated because it is disabled.
- **Risk Level**: The risk level if the policy is not implemented by your organization.
- **Total Assets**: The total number of assets that are scanned against the policy.
- **Failed Assets**: The number of failed assets to comply with the policy.
- **Excluded Assets**: The number of assets excluded from the SSPM report analysis.
- **Partial Assets**: The number of assets partially complying with the policy.
The Pending status in the Policy Status column appears until the first posture scan is complete when your organization is onboarded for SaaS Security Posture Control. This status can appear whenever a scan is in progress.
- Click the policy to view detailed information about the policy overview, asset summary, and remediation steps in the drawer view.
- [Drawer](#drawer)
- [Modify the table and its columns](/unified/using-tables).
![SSPM Report showing policy details](/downloads/zia/dashboard-analytics/reports/about-saas-security-posture-report/SSPM%20Report_updated1.png)
- []**Application**: View the policies for the application of your choice.
- **Tenant**: View the policies for the application tenant of your choice.
- **Resource Type**: View the policies for the resource types of your choice.
- **Compliance**: View the policies for the compliance of your choice. Irrespective of the compliance for which you want to filter the report, the Compliance widget in a following step lists all the compliances as policies can be applicable for multiple compliances.
- **Policy Status**: View policies by their status (All, Passed, Failed, Partial, or Disabled).
- **Risk Level**: View policies by their risk levels (All, High, Low, or Medium).
[]The **Actions **option is located at the top right of the drawer. You can use it to enable or disable a policy for SSPM analysis at the tenant level, or you can choose to export the information provided in the drawer to an Excel file. The drawer consists of the following three tabs:
- [Policy Overview](#overview)
- [Asset Summary](#summary)
- [Remediation Steps](#remediation-steps)
[]The Policy Overview tab displays the following information:
- **Tenant ID**: The tenant ID.
- **Tenant Name**: The name of the tenant.
- **Resource Type**: The resource type the policy falls into.
- **Policy Status**: The policy implementation status (Passed, Failed, Partial, or Disabled).
- **Failed Assets**: The number of assets from total assets that have misconfigured attributes. Click the asset number and you're redirected to the Assets Summary tab.
- **Risk Level**: The risk level if the policy is not implemented (High, Low, or Medium).
- **Description**: The description of the policy.
- **Last Scan Run**: The timestamp when the policy was last evaluated.
- **Compliance**: Displays the compliances the policy is mapped to.
[See image.](#policy-overview-img)
[]![Posture Management Page showing Policy Overview tab](/downloads/zia/dashboard-analytics/reports/about-saas-security-posture-report/Policy_Overview_Updated1.png)
[]The Asset Summary tab displays the following information:
- **Description**: The description informs why the policy failed or what was evaluated.
- Filter the Assets table by Status or State.
- Search for an asset by its name.
- View a list of all the assets. An asset can be a user or repository, depending on the type of application. For each asset, you can view the following information:
- **Status**: The policy status for the assets (Passed, Failed, or Partial).
- **Repository Name**: The name of the repository. This column is visible for source code repository applications.
- **Repo ID**: The repository ID. This column is visible for source code repository applications.
- **Email ID**: The email ID of the user. This column is not visible for source code repository applications.
- **Display Name**: The name of the user. This column is not visible for source code repository applications.
- **Visibility**: The repository visibility (Private, Public, etc.). This column is visible for source code repository applications.
-
**State**: The state of the asset appears as Excluded if the asset is excluded from the SSPM report analysis.
The column displays no information if no actions are performed.
- **Action**: The actions available for the asset.
- [Modify the table and its columns](/unified/using-tables).
- **Action**: Click **Exclude **to exclude the asset from the SSPM report analysis.
- Click the drop-down menu to view the following information:
- **General Info**: The basic information about the asset.
-
**State Log**: The logs for the changes made to the asset. The logs are populated when you perform exclude or do not exclude actions on the asset. For each log, you can view the following information:
- Timestamp
- Administrator
- Notes
You can also [modify the table and its columns](/unified/using-tables).
- **View Metadata**: Click to view the metadata highlighting the part where the configuration requires your attention to comply with the policy. You can copy the part that is displayed in the section or download the entire API response to a JSON file using the **Copy **or **Download JSON **option respectively. [See image.](#metadata-img)
![Posture Management Page showing Asset Summary tab](/downloads/zia/dashboard-analytics/reports/about-saas-security-posture-report/Asset_Summary.png)
[]![View Metadata option in the Asset Summary tab](/downloads/ZIA-6.2r-metadata-info.png)
[]The Remediation Steps tab displays the following information:
- **Steps To Remediate**: A link that redirects you to remediation steps in the application's help documentation.
- **Remediation Impact**: The information about how the user's experience changes if you remediate the misconfiguration.
- **Threat**: The information about potential security risks if the security posture is not configured as per the recommended policy.
[See image.](#remediation-steps-img)
[]![Posture Management Page showing Remediation Steps tab](/downloads/zia/dashboard-analytics/reports/about-saas-security-posture-report/Remediation_Steps_updated2.png)
- []**Failed**: The total number of failed policies.
- **Passed**: The total number of passed policies.
- **Partial**: The total number of partially successful policies.
- **Disabled**: The total number of policies that are disabled from security posture evaluation.
[]The [Posture Management Report](#posture_management_page) shows you the current state of your organization’s security posture for SaaS applications with respect to best practices recommended by Zscaler as well as based on industry standards such as GDPR, HIPAA, PCI, etc. It also allows you to see information on recommended security policies, security threats and their risk levels, and remediation activities. This serves as a starting point to decrease security risks for your organization’s SaaS applications.
Unlike Advanced SSPM, SSPM Essentials offers limited features, including security control, standalone platform reporting, polling frequency, etc.
SSPM Essentials will not have any additional features introduced, aside from security updates. If you don't have Advanced Posture Management enabled via a license, the Posture Management page (SSPM Essentials) with an upgrade banner is visible. To upgrade to Advanced SSPM, contact your Zscaler Account team.
To learn how to configure security policies as per the business requirements, see [Understanding the SaaS Security Posture Management Policy](/unified/understanding-saas-security-posture-management-policy).
[]Advanced SSPM is a comprehensive and unified solution that delivers complete security across SaaS applications and platforms, from data visibility to posture and governance. It helps to quickly identify and mitigate risky misconfigurations, control SaaS sprawl and reduce third-party access, and identify users at risk.
In contrast to SSPM Essentials, Advanced SSPM has varied offerings, such as security controls, modular polling frequency, multiple polling methods (e.g., API, Nativescripting), and integrated experience (e.g., App Governance, Posture, Identity, Data). To learn more about Advanced SSPM, see [What Is Advanced Posture Management?](/unified/what-advanced-posture-management) and [About Posture](/unified/about-posture).
If you have Advanced Posture Management enabled via a license, the Posture Management page redirects to the 3rd-Party App Governance Admin Portal. You can access the 3rd-Party App Governance Admin Portal for detailed posture reports on supported SaaS applications.