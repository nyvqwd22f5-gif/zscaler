# SaaS Security Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/saas-security-api-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1433721.pdf

This guide describes the benefits of using Saas Security and the steps necessary for configuring Zscaler Internet Access (ZIA) to add SaaS Security to your security posture.
A cloud access security broker (CASB) is a visibility and control point that sits between cloud app users and cloud services. CASB secures cloud applications by monitoring traffic and user activity, automatically blocking threats and risky sharing, and enforcing security policies (such as authentication and alerting).
Some CASB benefits include:
- Data protection
- Threat protection services
- Data Loss Prevention (DLP)
- Malware and other threat prevention
- Shadow IT discovery and control
- Regulatory compliance
Zscaler offers both inline and out-of-band CASB capabilities. The inline (proxy-based) solution is in place through ZIA using [Cloud App Control](/zscaler-deployments-operations/cloud-app-control-deployment-and-operations-guide), [Threat Protection](/zscaler-deployments-operations/threat-protection-deployment-and-operations-guide), [Sandboxing](/zscaler-deployments-operations/advanced-sandbox-deployment-and-operations-guide), [DLP](/zscaler-deployments-operations/data-loss-prevention-deployment-and-operations-guide), and [URL Filtering](/zscaler-deployments-operations/url-filtering-deployment-and-operations-guide).
Zscaler’s Software as a Service (SaaS) Security API is an out-of-band CASB solution that prevents data exposure and ensures SaaS app compliance. It also scans data repositories and retains historical data for cloud applications.
To learn more, see [SaaS Security](/zia/policies/saas-security).
Value of Deploying SaaS Security
SaaS Security provides the following benefits:
- Discovers your organization’s cloud app usage, creates reports on cloud spend, and performs risk assessments to help decide whether to block an app.
- Identifies your industry’s greatest risk factors so you can set stringent data protection policies to achieve and maintain compliance across your organization.
- Applies policies to provide [shadow IT control](/zia/about-saas-security-api-scan-configuration), [cloud DLP](/zia/about-saas-security-api-dlp), [Posture Control](/zia/configuring-saas-security-posture-control-policy), and [Malware Detection](/zia/configuring-saas-security-api-malware-detection-policy).
- Protects data at rest (i.e., out-of-band).
Deployment Phase
The deployment phase includes initially setting up and integrating ZIA solutions into an existing network infrastructure. During the deployment phase, you configure SaaS Security to meet the needs of your infrastructure. The following sections discuss the steps to deploy SaaS Security in ZIA.
Prerequisites
SaaS Security might require an additional license for your organization. Check with your Zscaler Account team to see if you have the necessary licensing requirements.
Deployment Steps
The following sections cover only the out-of-band deployment instructions:
- Identify applications that your organization wants to monitor.
- [Add a Software as a Service (SaaS) Application Tenant](/zia/adding-saas-application-tenants).
- (Optional) [Configure a SaaS Security DLP policy](/zia/configuring-saas-security-api-dlp-policy) to discover and protect sensitive data at rest in sanctioned SaaS applications:
- You must configure DLP first. To learn more, see [DLP Deployment and Operations Guide](/zscaler-deployments-operations/data-loss-prevention-deployment-and-operations-guide).
- (Optional) [Configure Zscaler Incident Receivers](/zia/configuring-zscaler-incident-receiver) to forward the transactions captured by this policy rule to an on-premises DLP incident receiver.
- (Optional) [Configure a SaaS Security Malware Detection policy](/zia/configuring-saas-security-api-malware-detection-policy) to discover and prevent threats to data at rest in sanctioned SaaS applications.
- [Configure SaaS Security scan schedules](/zia/configuring-saas-security-api-scan-schedules).
- (Optional) [Modify default SaaS security activity alerts](/zia/editing-default-saas-security-activity-alerts) and [create custom alerts](/zia/adding-alerts).
Considerations
Review the following considerations:
- You can configure [out-of-band CASB scanning exceptions](/zia/configuring-saas-security-api-scanning-exceptions) for sensitive locations or other reasons as needed.
- For DLP or Malware Detection rules, decide whether to only report incidents or to take immediate action (e.g., removing shareable links or quarantining malware) when a rule violation is detected.
- You can view additional info in the SaaS Security [Report](/zia/saas-security-report), [Insights](/zia/saas-security-insights), and [Logs](/zia/saas-security-insights-logs).
- To fully leverage SaaS Security capabilities, you might need to use an admin account with sufficient administrative privileges. To learn more about the requirements for individual SaaS applications, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
- To learn more about adding additional object types for ServiceNow tenants, see [Adding Object Types for ServiceNow Tenants](/zia/adding-object-types-servicenow-tenants).
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. During the operations phase, you can monitor and tune SaaS Security to meet your infrastructure needs.
Common Troubleshooting Items
If [Security Exceptions](/zia/configuring-saas-security-api-dlp-policy-exceptions) are not working as expected (e.g., excluded folders still appear in the logs), it’s possible that the username assigned in ZIA does not match the username of the scanned folder in the SaaS tenant. For example, the ZIA policy exception uses joe.blogs@xyz.com, while the SaaS tenant uses joe.blogs@abc.com. Usernames must be consistent across the policies and tenants for the exceptions to work.
To learn more, see [SaaS Application Validation Error Codes](/zia/saas-application-validation-error-codes).
Deployment Checklist
Zscaler recommends downloading the [SaaS Security Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/saas-security-api-deployment-and-operations-guide/SaaS-Security-API-Deployment-Operations-Checklist.pdf) to help plan and implement SaaS Security: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/saas-security-api-deployment-and-operations-guide/SaaS-Security-API-Deployment-Operations-Checklist.pdf)
Additional Information
For more SaaS Security information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com/).