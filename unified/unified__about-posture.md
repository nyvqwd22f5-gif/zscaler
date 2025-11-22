# About Posture
Source: https://help.zscaler.com/unified/about-posture
PDF: https://help.zscaler.com/pdf/com/en/1514851.pdf

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
- View the drift in posture control. The **Drift over time** graph displays the drift in posture over a period of time. You can use the filter to view the posture drift over a specific time period.
- Search for controls.
- Apply filters to the controls displayed in the table.
- Export the controls report to a CSV file.
- View a list of all the controls. For each control, you can view:
- **Status**: The status of the control. The following statuses can appear:
- **Pass**: Your organization's scanned posture control is correctly configured.
- **Fail**: Your organization's scanned posture control is incorrectly configured.
- **Partial**: Not all the scanned assets have posture control configured correctly.
- **Disabled**: The control is disabled and excluded from scans.
- **Control**: The name of the control. Click the control name to open the [Control Panel](/unified/about-control-panel) and further review it.
- **Tenant**: The name of the SaaS application tenant.
- **Category**: The category of the control.
- **Severity**: The severity level of the control. You can change the severity level. To learn more, see [Updating the Control Severity](/unified/updating-control-severity).
- **Failed assets**: The number of assets that failed to comply with the policy vs. the total number of scanned assets.
- **Compliance**: The applicable compliance frameworks for the control.
- Enable or disable the control. By default, all the controls are enabled.
If the status of a policy is pending, the policy is not displayed on the Posture page. When a single tenant or multiple tenants are onboarded for Advanced SSPM, a message displays indicating that the tenants are still being processed.
![Screenshot of Posture Page](/downloads/tech-pubs-drafts/zia-draft-articles/about-posture-draft-doc-55475/Posture_NewFilter.png)