# Viewing and Managing the Supported SSPM Policies
Source: https://help.zscaler.com/unified/viewing-and-managing-supported-sspm-policies
PDF: https://help.zscaler.com/pdf/com/en/1493611.pdf

The SaaS Security Posture Management (SSPM) page allows you to view or manage the supported policies for each application.
If you have Advanced Posture Management enabled via a license, the Posture Management page redirects to the 3rd-Party App Governance Admin Portal. Access the 3rd-Party App Governance Admin Portal for detailed posture reports on supported SaaS applications. To learn more, see [What is Advanced Posture Management?](/unified/what-advanced-posture-management) and [About Posture](/unified/about-posture).
To view the list of supported SSPM policies for each tenant and to manage the status of the policies:
- Go to **Policies **>** Data Protection **>** Policy **>** SaaS Security Posture Management**.
-
From the **Application **drop-down menu, choose the SaaS application you want to view the recommended security policies for.
[See image.](#sspm-application-filter)
- From the **Tenant **drop-down menu, choose the application tenant you want to view the recommended security policies for.
-
Click the **Add **icon (**+**) to further filter the policies by **Compliance Check**, **Risk Level**, and **Status**. Click **Reset **to reset the filters back to the application and tenant.
[See image.](#sspm-policy-table-filters)
-
The policy table displays the list of policies based on the set filters. The following columns appear for each policy in the policy table:
-
**Policy**: The name of the policy. You can sort this column. Click a policy name to view the **Policy Details** drawer. The **Policy Details** drawer displays general information about the selected policy including the resource type, the risk level, the description, the potential threat if the policy is not implemented, and the applicable compliance.
[See image.](#sspm-policy-details-widow)
- **Resource Type**: The resource type of the policy. You can sort this column.
- **Compliance**: The applicable compliance type of the policy. The SSPM policies support FFIEC, GDPR, HIPAA, PCI DSS v3.2, ISO 27001:2013, SOC2 AICPA TSC 2017, NIST 800-53 Rev.5, CIS Microsoft 365 v1.4, CIS Microsoft 365 v3.0, and CIS Google Workspace V1.0.0 compliance types based on the selected tenant.
- **Risk Level**: The risk level (High, Medium, Low) of the policy. You can sort this column.
-
**Policy Status**: The status of the policy. By default, all the policies are enabled. Disable or re-enable any policy based on your organization's required security posture using the toggle button.
- If enabled, the Zscaler SSPM evaluates the policy for the selected SaaS application and the tenant, and displays the policy’s current status (Pass, Fail, Partial) in the [Posture Management Report](/unified/about-posture-management-report) page.
- If disabled, the Zscaler SSPM does not evaluate the policy for the selected SaaS application and the tenant, and displays the Disabled status for the policy in the [Posture Management Report](/unified/about-posture-management-report) page.
[See image.](#sspm-policy-status)
To learn more about policy statuses, see [About Posture Management Report](/unified/about-posture-management-report).
[See image.](#sspm-policy-table)
- Click **Save** after disabling or re-enabling the policy status and [activate the change](/unified/saving-and-activating-changes-admin-portal).
[]![The SaaS Security Posture Report](/downloads/unified/policies/internet-saas/data-protection/saas-security/posture-management/posture-management-essentials/viewing-and-managing-supported-sspm-policies/ZIA-SaaS-Security-Posture-Control-Policy.png)
[]![The SSPM Policy details page displays the details of the selected policy.](/downloads/zia/policies/saas-security/posture-management/posture-management-essentials/viewing-and-managing-supported-sspm-policies/SSPM%20Policy%20Details%20Window.png)
[]![SSPM Policy Status](/downloads/zia/policies/saas-security/posture-management/posture-management-essentials/viewing-and-managing-supported-sspm-policies/SSPM%20Policy%20Status.png)
[]![SSPM Application Filter](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-posture-management/viewing-and-managing-supported-sspm-policies/SSPM-Applications.png)
[]![SSPM Policy Table Filters](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-posture-management/viewing-and-managing-supported-sspm-policies/SSPM-Additional%20Filters.png)