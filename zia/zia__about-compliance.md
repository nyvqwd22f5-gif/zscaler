# About Compliance
Source: https://help.zscaler.com/zia/about-compliance
PDF: https://help.zscaler.com/pdf/com/en/1514296.pdf

Zscaler Advanced SaaS Security Posture Management (SSPM) enables organizations to monitor their Software as a Service (SaaS) applications’ security posture against various compliance frameworks such as GDPR, NIST, etc. The Compliance page provides a complete mapping of controls within various compliance frameworks and helps to verify whether they are enforced according to the security checks.
If you subscribed to the Advanced SSPM service, you can access the Compliance page. To learn more, see [What Is Advanced Posture Management?](/zia/what-advanced-posture-management)
The Compliance page provides the following benefits and enables you to:
- View information on the overall compliance status across SaaS apps, and the compliance status by framework or platform.
- Check your SaaS application's security posture against various security compliances to report misconfigurations and policy violations, and to automate remediation.
- Quickly identify non-compliant apps and controls that impact the compliance status.
- Understand the compliance progress over time.
**About the Compliance Page**
On the Compliance page, you can do the following:
- View the overall compliance status for the security checks.
- View the compliance status by frameworks or platforms.
- **Frameworks**: Expand each framework to view a list of associated platforms and the number of failed controls for each platform. Additionally, expand each platform to view a list of associated tenants and the number of failed controls for each tenant.
- **Platforms**: Expand each platform to view a list of associated frameworks and the number of failed controls for each framework. Additionally, expand each framework to view a list of associated tenants and the number of failed controls for each tenant.
- Search for a framework by its name.
- Filter the framework by its name.
- View a list of all the compliance frameworks. For each framework, you can view:
- **Framework**: The name of the framework. Expand the framework name to view a list of security checks associated with that framework. Click a security check to open the [control panel](/zia/about-control-panel) and further review it.
- **Control**: The compliance control that is scanned against the framework.
- **Security checks**: The number of security checks for the framework.
- **Status**: The status of the framework. The status can be one of the following:
- **Failed**: The controls failed the security checks.
- **Partial**: The controls partially passed the security checks.
- **Success**: The controls passed all the security checks.
- **Tenant**: The name of the SaaS application tenant.
When a single tenant or multiple tenants are onboarded for Advanced SSPM, a message displays indicating that the tenants are still being processed.
![Compliance page in Advanced SSPM showing the list of compliance frameworks](/downloads/tech-pubs-drafts/zia-draft-articles/about-compliance-draft-doc-55418/Compliance_New.png)