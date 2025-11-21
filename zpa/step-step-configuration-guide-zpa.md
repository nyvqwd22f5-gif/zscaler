# Step-by-Step Configuration Guide for ZPA
Source: https://help.zscaler.com/zpa/step-step-configuration-guide-zpa
PDF: https://help.zscaler.com/pdf/com/en/1483446.pdf

This guide takes you through the configuration steps that you must complete to begin using Zscaler Private Access (ZPA) for your organization.
Before you begin configuring ZPA, Zscaler recommends reading the following articles:
- [What is Zscaler Private Access?](/zpa/getting-started/what-zscaler-private-access)
- [About the ZPA Admin Portal](/zpa/getting-started/introduction-zpa-admin-portal), including:
- [About the Applications Dashboard](/zpa/about-dashboard/appsDashboard)
- [About the Users Dashboard](/zpa/about-dashboard/usersDashboard)
- [About the Health Dashboard](/zpa/about-dashboard/health)
- [About Audit Logs](/zpa/about-audit-logs)
Configuring ZPA
To configure ZPA, you must complete the following steps:
- [Step 1: Update Company and Administrator Information](#UpdateCompanyAdminInfo)
- [Step 2: Configure Your Certificates](#ConfigureCertificates)
- [Step 3: Configure Single Sign-On Authentication](#ConfigureSSO)
- [Step 4: Configure the Zscaler Client Connector](#ConfigureZscalerApp)
- [Step 5: Configure Your App Connectors](#ConfigureConnectors)
- [Step 6: Configure Your Applications](#ConfigureApplications)
- [Step 7: Configure Your SAML Attributes](#ConfigureSAMLAttrs)
- [Step 8: Configure Your Policies](#ConfigurePolicies)
- [Step 9: Configure Log Streaming](#ConfigureLSS)
- [Step 10: Configure Your User Portals](#ConfigureUserPortals)
[]To update your company information and configure administrators as applicable, see the following articles:
- [Configuring the Company Profile](/zpa/about-company)
- [About Administrators](/zpa/about-users)
- [Configuring ZPA Administrators](/zpa/about-user/new)
- [About Roles](/zpa/about-roles)
- [Configuring Administrator Roles](/zpa/about-role/new)
To learn more, see [Administration](/zpa/documentation-knowledgebase/administration).
[]ZPA uses certificates to authenticate the App Connector and the user's device before each connection as well as provide access to web applications via internet browser. To configure your certificates, see the following articles:
- [About Certificates](/zpa/about-certificatesIntro)
- [About Enrollment (CA) Certificates](/zpa/about-EnrollmentCertificates)
- [About Browser Access (Web Server) Certificates](/zpa/about-BrowserAccessCertificates)
To learn more, see [Certificate Management](/zpa/documentation-knowledgebase/certificate-management).
[]ZPA supports single sign-on (SSO) via SAML so that your remote users can access enterprise applications without having to log in separately to ZPA. To configure SSO for ZPA, see the following articles:
- [About IdP Configuration](/zpa/about-idps)
- [Configuring an IdP for Single Sign-On](/zpa/about-idp/new)
To learn more, see [Authentication](/zpa/documentation-knowledgebase/authentication).
[]Installed on the user's device, the Zscaler Client Connector connects to the ZPA cloud to enable granular, policy-based access to your organization’s internal resources.
To configure the Zscaler Client Connector for your organization, see the following articles:
- [What is the Zscaler Client Connector?](/z-app/what-zscaler-app)
- [Step-by-Step Configuration Guide for Zscaler Client Connector](/z-app/zscaler-app-step-step-configuration-guide)
Also refer to the following platform-specific Zscaler Client Connector articles:
- [Using Zscaler Client Connector for Windows](/z-app/using-zscaler-app-windows)
- [Using Zscaler Client Connector for macOS](/z-app/using-zscaler-app-macos)
[]App Connectors are lightweight virtual machines (VM) that you must configure in the data centers or virtual private clouds (VPC) that host your application servers. Once the App Connectors are configured, they can connect to the ZPA cloud to provide users with access to applications. To configure your App Connectors, see the following articles:
- [About App Connectors](/zpa/about-connectors)
- [Configuring App Connectors](/zpa/about-connectorprovisioningwizard)
- [About Deploying App Connectors](/zpa/about-deploying-connectors)
- [App Connector Deployment Guides for Supported Platforms](/knowledge-base-categories/supported-platforms-connectors)
To learn more, see [App Connector Management](/zpa/documentation-knowledgebase/connector-management).
[]You must configure the applications you want to make accessible to your users via ZPA. To configure applications, see the following articles:
- [About Applications](/zpa/about-applications)
- [Configuring Application Segments](/zpa/about-application/onboard)
To learn more, see [Application Management](/zpa/documentation-knowledgebase/application-management).
[]You can configure SAML attributes that you can then use when configuring policies. To configure your SAML attributes, see the following articles:
- [About SAML Attributes](/zpa/about-samlattributes)
- [Manually Adding SAML attributes](/zpa/about-samlattribute/new)
- [Importing SAML Attributes](/zpa/about-importSamlAttributes)
To learn more, see [SAML Attributes](/zpa/documentation-knowledgebase/authentication/saml-attributes).
[]Your users cannot access applications until you configure policies for them. To configure access and timeout policies, see the following articles:
- [About Policies](/zpa/about-policies)
- [About Access Policy](/zpa/about-accesspolicy)
- [Configuring Access Policies](/zpa/about-accesspolicy/new)
- [About Timeout Policy](/zpa/about-reauthPolicy)
- [Configuring Timeout Policies](/zpa/about-reauthPolicy/new)
- [About Client Forwarding Policy](/zpa/about-client-forwarding-policy)
- [Configuring Client Forwarding Policies](/zpa/configuring-client-forwarding-policies)
To learn more, see [Policies](/zpa/documentation-knowledgebase/access-timeout-policies).
[]The Log Streaming Service (LSS) provides a better understanding of the information coming from the ZPA service, by allowing you to create log receivers that obtain information about App Connectors and users. To configure your log receivers, see the following articles:
- [About the Log Streaming Service](/zpa/about-log-streaming)
- [Configuring a Log Receiver](/zpa/configuring-log-receiver)
To learn more, see [Log Streaming Service](/zpa/documentation-knowledgebase/log-streaming-service).
[]You can configure user portals for your organization, that display links to applications that your users are allowed to access. To configure user portals, see the following articles:
- [About User Portals](/zpa/about-user-portals)
- [Configuring User Portals](/zpa/configuring-user-portals)
- [About User Portal Links](/zpa/about-user-portal-links)
- [Configuring Application Links for User Portals](/zpa/configuring-application-links-user-portals)
- [About Zscaler Client Connector Download Links](/zpa/about-zscaler-app-download-links)
- [About User Portal Acceptable Use Policy](/zpa/about-user-portal-acceptable-use-policy)
To learn more, see [User Portal](/zpa/user-portal).