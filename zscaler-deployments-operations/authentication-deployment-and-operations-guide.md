# Authentication Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/authentication-deployment-and-operations-guide
PDF: https://help.zscaler.us/pdf/com/en/1420096.pdf

This guide describes the benefits of enforcing authentication and the steps necessary for configuring Zscaler Internet Access (ZIA) to add authentication to your security posture.
ZIA enforces web and firewall policies by location, department, group, and user. It also tracks internet usage by location, department, and user.
You must provision and authenticate users to enforce granular authentication policies and reporting capabilities for ZIA. Provisioning involves uploading users, groups, and departments to the service database. Enabling authentication allows ZIA to:
- Identify received traffic.
- Enforce the location, department, group, and user policies.
- Provide user and department logging and reporting.
To learn more, see [About Provisioning and Authentication Users](/zia/about-provisioning-authenticating-users).
Value of Enforcing Authentication
Enforcing authentication provides the following benefits:
- Enforces policies based on user criteria.
- Maps transactions to individual users and increases the reporting detail.
Deployment Phase
The deployment phase initially sets up and integrates ZIA solutions into an existing network infrastructure. During the deployment phase, you configure authentication in ZIA to meet the needs of your infrastructure. The following sections discuss steps to enable authentication.
Prerequisites
For authentication deployment, verify and complete the following prerequisites:
- Provision the authentication domain needed to identify the organization (by raising a [Zscaler Support ticket](/submit-ticket-links)).
- Identify the users and groups that use ZIA.
- Identify what identity provider (IdP) certificate, login URLs, and metadata must be available.
Deployment Steps
The following steps explain how to enable authentication:
- Configure a provisioning method based on the instructions and information provided in [Choosing Provisioning and Authentication Methods](/zia/choosing-provisioning-authentication-methods). Zscaler recommends [SCIM-based provisioning](/zia/configuring-scim) to allow for real-time synchronization.
- Configure an authentication method based on the instructions and information provided in [Choosing Provisioning and Authentication Methods](/zia/choosing-provisioning-authentication-methods). Zscaler recommends using an [Identity Federation using SAML](/zia/understanding-saml).
- If using a [Zscaler Authentication Bridge (ZAB)](/zia/about-zscaler-authentication-bridge), [deploy the ZAB](/zia/deploying-zscaler-authentication-bridge).
- Add [authentication bypasses](/zia/exempting-urls-cloud-apps-authentication) for the IdP authentication URLs to authenticate end users. You might need to exempt IdP URLs from being forwarded to ZIA for remote users and forward them via a direct path instead.
- (Optional) If you use Zscaler Client Connector for authentication, [deploy Zscaler Client Connector](/zia/policies/mobile-security/zscaler-client-connector-deployment) to end users’ devices.
- Enable [Enforce Authentication](/zia/configuring-locations) on locations where it is needed.
- If using Kerberos, enable [Kerberos Authentication](/zia/configuring-locations) on locations where Kerberos authentication is needed.
- (Optional) To map users to device IP addresses, enable [IP Surrogate](/zia/about-surrogate-ip). This is not required for Zscaler Client Connector.
- (Optional) If you enabled IP Surrogate and you want to skip authentication for a specific time duration, enable [Surrogate IP for Known Browsers](/zia/configuring-locations).
Considerations
Review the following considerations:
- If you don’t use Zscaler Client Connector, Zscaler uses cookie-based authentication for most traffic. To learn more, see [About Zscaler Cookies](/zia/about-zscaler-cookies).
- If you use cookie-based authentication, you must enable SSL inspection for TLS-encrypted destinations. If SSL inspection isn’t used, use [IP Surrogacy](/zia/about-surrogate-ip) to map transactions to the previously authenticated user.
- Applications that cannot perform cookie-based authentication either hit Zscaler as unauthenticated traffic or, if [IP Surrogacy is enabled](/zia/about-surrogate-ip), map to the last authenticated user associated with this IP.
- IP Surrogacy maps the private IP address to a new user if a different user logs in to the Zscaler service from the same private IP address. If the mapping changes more than three times in a minute (e.g., three different users log in and surf the internet from the same private IP address within a minute), the service stops mapping users to the private IP address for 5 minutes and applies the location policies to the transactions that do not support authentication during these 5 minutes. Zscaler discourages the use of IP Surrogacy on shared hosts.
- Users who try to authenticate from a known location are automatically forwarded to the associated IdP. If the user is not coming from a known location, they must provide their user ID to get forwarded to the correct IdP.
- URL Filtering policies assume an implicit Allow All rule as a last resort choice if no other URL filtering rule applies to the traffic. This means that unauthenticated traffic is allowed by default. To restrict unauthenticated traffic, you must add specific URL filtering rules. To learn more, see [Configuring Policies for Unauthenticated Traffic](/zia/configuring-policies-for-unauthenticated-traffic).
- The refresh time for the revalidation of IP Surrogacy must be shorter than the DHCP lease time. Otherwise, ZIA might apply the wrong user policies. Zscaler recommends setting the Refresh Time for re-validation of Surrogacy to a period shorter than what you specified for Idle Time to Disassociation. To learn more, see [Configuring Locations](/zia/configuring-locations) and [Configuring Sub-Locations](/zia/about-sub-locations#addsubloc).
Operations Phase
This section describes common practices used to operate ZIA solutions when integrated with your environment. You can monitor and tune authentication during the operations phase to meet your infrastructure needs.
Prerequisites
For authentication operation, complete the following prerequisites:
- Store relevant IdP certificates and login URLs in a secure place, and make them available to relevant stakeholders for troubleshooting and backup purposes.
- Store SCIM Bearer Tokens in a secure place.
- Formulate an Incident Response Plan for situations where your IdP is unavailable.
Common Troubleshooting Items
The following list describes common issues related to authentication operation:
- User and group synchronization is not happening with SAML auto provisioning: SAML auto provisioning doesn’t support real-time synchronization, so you must manually synchronize new groups if the users or their group mapping recently changed. Users must reauthenticate to make updated information available.
- User and group synchronization not happening with SCIM provisioning:
- Check the IdP event logs to see if the IdP triggered a SCIM sync.
- Check the ZIA Admin Portal event logs to see if Zscaler successfully validated the SCIM sync.
- Check if the users and groups that needed synchronization to Zscaler are within the scope of entities synced on the IdP.
- Users are not receiving an authentication prompt, or traffic is not being authenticated:
- Check if SSL inspection is enabled for the destination.
- Check if authentication is enforced on the location from which the users are accessing the destination.
- Check if the browser or application is a supported agent and supports cookie-based authentication.
- Users are not correctly mapped in [Insights](/zia/about-insights) and [Interactive Reports](/zia/about-interactive-reports)): Check if [IP Surrogacy](/zia/about-surrogate-ip) is enabled and if multiple users try to authenticate using the same private IP.
Deployment and Operations Checklist
Zscaler recommends downloading the [Authentication Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/authentication-deployment-and-operations-guide/Authentication-Deployment-Operations-Checklist.pdf) to help plan and enable authentication in ZIA: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/authentication-deployment-and-operations-guide/Authentication-Deployment-Operations-Checklist.pdf)
Additional Information
For more SaaS Security information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com/).