# Step-by-Step Configuration Guide for ZPC
Source: https://help.zscaler.com/zpc/step-step-configuration-guide-zpc
PDF: https://help.zscaler.com/pdf/com/en/1392396.pdf

This guide takes you through the configuration steps you need to complete to begin using Zscaler Posture Control (ZPC) for your organization.
Before you begin configuring ZPC, Zscaler recommends reading the following articles:
- [What is Zscaler Posture Control?](/zpc/what-zscaler-posture-control)
- [Accepting the End User Subscription Agreement (EUSA)](/zpc/about-zpc-admin-portal#eusa)
- [Using the Zscaler Help Browser](/zpc/using-zscaler-help-browser)
Configuring ZPC
To configure ZPC, complete the following steps:
- [Step 1: Log in to ZPC Admin Portal](#activate)
- [Step 2: Onboard Cloud Accounts](#onboard)
- [Step 3: Configure Administrators & Roles](#admin)
- [Step 4: Configure Single-Sign-On Authentication](#sso)
- [Step 6: Configure Alerts Rules](#alerts)
- [Step 7: Manage Security Policies](#policies)
- [Step 8: Configure 3rd-Party Integrations](#integration)
- [Step 9: Configure Scheduled Reports](#reports)
- [Step 10: Configure IaC Integrations](#iac)
- [Step 11: Configure Vulnerability Integrations](#vulnerability)
[]After your organization is provisioned for ZPC, you will receive an email with a link to create your password. Click the link to set the password. Log in to the ZPC Admin Portal with your registered email ID and the newly created password.
[]ZPC supports single-sign-on (SSO) via SAML 2.0 so that users can access ZPC directly from the IdP portal. To learn more, see [Configuring SAML for SSO](/zpc/configuring-saml-sso).
[]You can onboard multiple cloud accounts from different cloud service providers (CSPs) into ZPC. When onboarded, ZPC monitors your cloud accounts for any vulnerabilities and threats, and provides comprehensive data of your cloud deployment's security posture. To learn more, see [Onboarding Cloud Accounts](/zpc/onboarding-cloud-accounts).
[]ZPC implements role-based access control (RBAC) and enables you to delegate roles to users and granularly control their level of access to specific cloud accounts in your organization. You can add users, [groups](/zpc/about-groups), [business units](/zpc/about-business-units), and assign [predefined or custom roles](/zpc/about-roles-and-permissions) as applicable. To learn more, see [About Administrators](/zpc/about-administrators).
[]The Infrastructure as Code (IaC) feature is available based on your ZPC subscription. The IaC feature enables you to apply security controls on your IaC infrastructure across various continuous integration (CI) and continuous deployment/delivery (CD) tools, and integrated development environments (IDEs) before deployment. To learn more, see [About IaC Integrations](/zpc/about-iac-integrations).
[]The Vulnerability Integration feature is available based on your ZPC subscription. You can use this feature to scan your cloud workloads and container registries for vulnerabilities, remediate issues, secure your cloud assets, and thereby protect your organization from cyber threats. To learn more, see [About Vulnerability Integrations](/zpc/about-vulnerability-integrations).
[] ZPC integrates with your cloud storage services, such as Amazon S3 buckets, Azure Blob Storage, Splunk, or Amazon Security Lake, and sends data logs (alerts) to these storage services. To learn more, see [About Third-Party Integrations](/zpc/about-third-party-integrations).
ZPC offers incident management by integrating with [ITSM tools](/zpc/adding-itsm-integrations), [cloud storage services](/zpc/adding-cloud-storage-integrations), and [ChatOps tools](/zpc/integrating-zpc-slack). You can send alert data to these tools for further investigation and remediation. To learn more, see [About Third-Party Integrations](/zpc/about-third-party-integrations).
[]ZPC enables you to configure and manage alert rules and notifications, so individuals in your organization can receive email notifications for any security policy violations that occur in your cloud environment. To learn more, see [About Alerts](/zpc/about-alerts).
[]ZPC allows you to schedule custom compliance reports for regular distribution to specific recipients. To learn more, see [About Scheduled Reports](/zpc/about-scheduled-reports).
[]ZPC enables you to create and manage custom security policies to cater to your cloud deployment's compliance requirements. ZPC offers over 400 security policies across multiple cloud service providers (CSPs), including Amazon Web Services, Microsoft Azure, and Google Cloud Platform. To learn more, see [About Security Policies](/zpc/about-security-policies).