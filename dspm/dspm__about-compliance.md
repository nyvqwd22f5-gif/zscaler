# About Compliance
Source: https://help.zscaler.com/dspm/about-compliance
PDF: https://help.zscaler.com/pdf/com/en/1514301.pdf

Compliance refers to the security measures and guidelines that are implemented to comply with the industry-specific security frameworks and regulations such as GDPR, HIPAA, PCI, etc. DSPM detects policies and DLP engines that fail to comply with the frameworks. This information helps you to resolve the issues and ensure your data is compliant with regulatory standards.
You can view the overall compliance status and the total number of policies that failed to comply with specific frameworks. DSPM provides remediation steps to address the compliance issues.
The Compliance page provides the following benefits and enables you to:
- View the predefined and custom compliance frameworks.
- View the summary of failed policies.
- View the compliance configuration details.
- View the resources that are noncompliant and remediate the issues.
- Add custom compliance frameworks.
About the Compliance Page
On the Compliance page (Analytics > Compliance), you can do the following:
- [Add a custom compliance framework.](/dspm/adding-custom-compliance-framework)
- Show disabled frameworks. The disabled frameworks are displayed at the end and are grayed out.
- Click the Actions (![dspm-actions-menu.jpg](/downloads/dspm/analytics/compliance/about-compliance/dspm-actions-menu.jpg)
) icon to do the following:
- [Enable or disable](/dspm/managing-compliance-frameworks) a predefined or custom framework.
-
[Edit or delete](/dspm/managing-compliance-frameworks) a custom framework.
You cannot edit or delete a predefined framework.
- View the compliance frameworks in the following format:
- [Grid](#grid-view)
- [Table](#table-view)
![The Compliance dashboard displaying the compliance frameworks and the actions available.](/downloads/dspm/analytics/compliance/about-compliance/dspm-compliance-page_0.png)
[]The compliance frameworks, the number of failed policies against the total number of policies, the type of framework (Predefined or Custom) are displayed as tiles. Click any tile to [view the compliance details](/dspm/viewing-compliance-details).
![The Compliance dashboard displaying the compliance frameworks in grid view.](/downloads/dspm/analytics/compliance/about-compliance/dspm-compliance-pag-grid.png)
[]The compliance frameworks are displayed in a table. For each framework, you can see:
- **Framework Name**: The name of the compliance framework. Click to [view the compliance details](/dspm/viewing-compliance-details).
- **Description**: The description of the framework.
- **Failed Policies**: The number of policies that failed to comply with the framework.
-
**Total Policies**: The total number of policies for the framework.
If a mapped policy is disabled on the [Policies ](/dspm/about-data-posture-policies)page, it is excluded from compliance calculations but is still included in the total policies.
If a mapped policy is deleted, it is removed from the framework and is not shown in the [policy list](/dspm/viewing-compliance-details). For example, if the total policies for a framework is 100, and 2 policies are deleted from the Policies page, then the total policy count is 98.
- **Enabled**: If the framework is enabled or disabled.
- **Type**: The type (**Predefined **or **Custom**) of framework.
![The Compliance dashboard displaying list of compliance frameworks in a table.](/downloads/dspm/analytics/compliance/about-compliance/dspm-compliance-page-table.png)