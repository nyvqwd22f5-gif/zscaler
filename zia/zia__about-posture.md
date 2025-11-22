# About Posture
Source: https://help.zscaler.com/zia/about-posture
PDF: https://help.zscaler.com/pdf/com/en/1508611.pdf

Zscaler Advanced SaaS Security Posture Management (SSPM) enables you to continuously monitor your organization’s Software as a Service (SaaS) security posture. The Posture page shows you the current state of your organization’s security posture for SaaS applications, and how it drifts with respect to Zscaler best practices and industry standards such as General Data Protection Regulation (GDPR), Payment Card Industry (PCI), etc., to ensure you stay secure and compliant.
The Posture page provides the following benefits and enables you to:
- Gain visibility and monitor your organization's risk level and how it drifted over time for a SaaS platform or across all of them.
- Check your SaaS security posture against various security compliances and Zscaler best practices.
- Analyze and strengthen your organization's SaaS security posture by mitigating threats posed by SaaS misconfigurations.
- View and change control severity levels.
- Quickly identify SaaS risks and prevent threats from compromising data and the organization.
- Maintain posture and compliance across the organization.
About the Posture Page
On the Posture page, you can do the following:
- View a high-level overview of all the managed posture controls.
- Filter the controls by tenant.
- Filter the controls by label.
- View the** Failed Controls Remediation** graph, which displays the severity and implementation complexity of failed controls. Implementation complexity is the amount of work required to fix or improve a control to address any identified issues or vulnerabilities. If you click a number, you are redirected to the list of controls filtered by their severity and complexity.
- View the **Drift over time** graph that displays the drift in posture over a period of time. You can use the filter to view the posture drift over a specific time period.
The **Drift over time **widget does not appear when the screen width is less than 1,750 pixels and the **Posture Drift** drawer displays, and when the screen width is less than 1,550 pixels and the **Posture Drift** drawer is hidden.
-
Click to view the **Posture Drift** drawer. It displays the posture drift for the controls.
[See image.](#Posture-Drift-Drawer)
- Search for controls.
- Apply filters to the controls displayed in the table.
- Export the controls report to a CSV file.
- View a list of all the controls. For each control, you can view:
- **Status**: The status of the control. The following statuses can appear:
- **Pass**: Your organization's scanned posture control is correctly configured.
- **Fail**: Your organization's scanned posture control is incorrectly configured.
- **Partial**: Not all the scanned assets have posture control configured correctly.
- **Disabled**: The control is disabled and excluded from scans.
- **Pending**: The control is not yet evaluated due to missing permissions, connector issues, rate limits, etc.
- **Control**: The name of the control. Click the control name to open the [Control Panel](/zia/about-control-panel) and further review it.
- **Tenant**: The name of the SaaS application tenant.
- **Category**: The category of the control.
- **Severity**: The severity level of the control. The control severity is determined using the MITRE technique severity score, whose calculation considers actual prevalence and risk level of associated Common Vulnerabilities and Exposures (CVEs) to evaluate the technique’s true risk. You can change the severity level. To learn more, see [Updating the Control Severity](/zia/updating-control-severity).
- **Complexity**: The complexity level of the control. It refers to the ease of implementation and the effort required to deploy and configure the control.
- **Failed Assets**: The number of assets that failed to comply with the policy vs. the total number of scanned assets.
- **Compliance**: The applicable compliance frameworks for the control.
- Enable or disable the control. By default, all the controls are enabled.
When a single tenant or multiple tenants are onboarded for Advanced SSPM, a message displays indicating that the tenants are still being processed.
![Posture Page showing the list of controls](/downloads/zia/policies/saas-security/posture-management/posture-management-advanced/about-posture/Posture_Page_Latest.png)
[]![Posture Drift Drawer showing the posture drift for controls](/downloads/tech-pubs-drafts/zia-draft-articles/about-posture-draft-doc-59906/Posture_Drift_Drawer.png)