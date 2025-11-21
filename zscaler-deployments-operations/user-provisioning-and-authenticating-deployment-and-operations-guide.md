# User Provisioning and Authentication Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/user-provisioning-and-authenticating-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417946.pdf

This guide describes the benefits of using User Provisioning and Authentication and the steps necessary for configuring Zscaler Private Access (ZPA) to add User Provisioning and Authentication to your security posture.
ZPA uses Zero Trust network access, which allows users to connect to only the specific applications they need. End users are never actually placed onto the destination network, removing any possibility of lateral movement of malicious software or actors on the network to attack or infect other resources.
This guide focuses on ZPA user management best practices. The ZPA Admin Portal can provision users directly from your identity provider (IdP) using a System for Cross-domain Identity Management (SCIM) or Security Assertion Markup Language (SAML).
To learn more, see [Authentication](/zpa/authentication).
Value of Deploying User Provisioning and Authentication
User Provisioning and Authentication provides the following benefits:
- Granular user- and group-based Zero Trust network access policy control.
- The ability to automatically manage application access via ZPA from your IdP.
Deployment Phase
The deployment phase initially sets up and integrates ZPA solutions into an existing network infrastructure. During the deployment phase, you configure User Provisioning and Authentication to meet the needs of your infrastructure. The following sections discuss steps to deploy User Provisioning and Authentication.
Prerequisites
For User Provisioning and Authentication deployment, complete the following prerequisites:
- Closely coordinate with the ZPA Admin Portal and IdP management team when deploying User Provisioning and Authentication.
- Configure the authentication domains to allow users to log in.
- Configure the service provider information in the IdP using the service provider (SP) certificates, SP URL, and SP metadata.
- Gather the IdP certificates to authenticate users.
- You can use SAML auto-provisioning to provision users and associated attributes into ZPA every time a new user authenticates into Zscaler Client Connector.
- You can use SCIM to directly push the users and attributes from the IdP to the ZPA user database.
- Zscaler supports only SCIM version 2.0 and SAML version 2.0 and later.
Deployment Steps
The following steps explain how to deploy User Provisioning and Authentication:
- Contact Zscaler Support to add authentication domains by submitting a provisioning ticket with [Zscaler Support](/submit-ticket-links).
- Zscaler can check for authentication domains and other settings from the ZPA Admin Portal on the [Settings](/zpa/about-authSettings) page.
- Single Sign-On (SSO) deployment using SAML:
- ZPA supports SSO via SAML so that your remote users can access enterprise applications without having to log in to ZPA separately. To learn more about configuring SSO for ZPA, see [About IdP Configuration](/zpa/about-idps).
- Configure the [IdP in the ZPA Admin Portal](/zpa/about-idp/new) and download the SP information.
To learn more, see [Authentication](/zpa/authentication).
- SCIM deployment:
- Setting up SCIM requires an IdP partnered with Zscaler and [ZPA Admin Portal configuration](/zpa/enabling-scim-identity-management).
- The following IdP partners work with Zscaler:
- [SCIM Configuration Guide for Microsoft Azure AD](/zpa/scim-configuration-guide-microsoft-azure-ad)
- [SCIM Configuration Guide for Okta](/zpa/scim-configuration-guide-okta)
- [PingFederate integration with ZPA](https://docs.pingidentity.com/bundle/integrations/page/exl1587060854790.html)
- Verify the configuration. When deployed, [check the user status](/zscaler-client-connector/viewing-information-about-private-access-zscaler-client-connector) in the Zscaler Client Connector to see if the authentication was successful.
Considerations
Review the following considerations:
- Review the [IdP Configuration Best Practices](/zpa/idp-configuration-best-practices) before deployment.
- Review the [Ranges & Limitations](/zpa/ranges-limitations) for Authentication configuration.
- Before choosing between SAML or SCIM, review the application information and best practices. To learn more, see [About SCIM](/zpa/about-scim) and [Understanding SAML](/zia/understanding-saml).
- Take care if you decide to switch from SAML to SCIM. When you enable SCIM for the first time (or toggle the SCIM provisioning option), the SCIM database is synchronized. Database synchronization might impact authentication until all the users are synced from the customer IdP to the Zscaler database.
Operations Phase
This section describes standard practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune User Provisioning and Authentication in ZPA during operations to meet your infrastructure needs.
To configure your SAML attributes, see the following articles:
- [About SAML Attributes](/zpa/about-samlattributes).
- [Manually Adding SAML attributes](/zpa/about-samlattribute/new).
- [Importing SAML Attributes](/zpa/about-importSamlAttributes). To learn more, see [SAML Attributes](/zpa/documentation-knowledgebase/authentication/saml-attributes).
- Zscaler supports SCIM APIs and provides [SCIM API Examples](/zpa/scim-api-examples).
- To learn more about the list of users and groups synced using SCIM, see [About SCIM Users and Groups](/zpa/about-scim-users-and-groups).
Common Troubleshooting Items
The following list describes common issues related to User Provisioning and Authentication operation:
- Authentication fails: Check the user status logs for any failures in authentication from the [diagnostics](/zpa/about-user-authentication-diagnostics).
- Authentication errors on Zscaler Client Connector: Review the list of [Zscaler Client Connector error codes](/client-connector/zscaler-client-connector-zpa-authentication-errors) with reasons for the error and resolution details.
- Users might encounter a Zscaler Client Connector connection error when enabling SCIM sync with Okta. Okta does not sync users to ZPA in the Okta IdP before you enable SCIM. As a result, users do not initially appear in the SCIM user database when SCIM is enabled in ZPA. To learn more, see [How to avoid ZPA Connector Error when enabling SCIM sync with Okta](https://community.zscaler.com/s/question/0D54u00009evlQxCAI/how-to-avoid-zpa-connection-error-when-enabling-scim-sync-with-okta).
- If SCIM sync fails, review the information [About SCIM Sync Logs](/zpa/about-scim-sync-logs) in the ZPA Admin Portal. If you do not see the logs, look for errors in the SCIM provisioning logs from the configured IdP.
Deployment Checklist
Zscaler recommends downloading the [User Provisioning and Authentication Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zpa-deployments-operations/user-provisioning-and-authenticating-deployment-and-operations-guide/User-Provisioning-Authentication-Deployment-Operations-Checklist.pdf) to help plan and implement User Provisioning and Authentication: [Download PDF](/downloads/zscaler-deployments-operations/zpa-deployments-operations/user-provisioning-and-authenticating-deployment-and-operations-guide/User-Provisioning-Authentication-Deployment-Operations-Checklist.pdf)
Additional Information
For more User Provisioning and Authentication information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](https://community.zscaler.com/).