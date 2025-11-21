# Access Policy Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/access-policy-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417751.pdf

This guide describes the benefits of using Access Policies and the steps necessary for configuring Zscaler Private Access (ZPA) to add Access Policies to your security posture.
ZPA Access Policy rules enable you to implement role-based access control. To configure an Access Policy rule, you must first define the users and then define which applications or segment groups they can access. For example, you would specify the users first (i.e., SalesStaff), then specify which application segments or segment groups they can access (i.e., Sales App and Intranet Group). For a complete list of ranges and limitations for Access Policy rules, see [Ranges & Limitations](/zpa/ranges-limitations#Policies).
To learn more, see [Access Policy Guide](/zpa/about-access-policy).
Value of Deploying Access Policy
Using Access Policy provides the following benefits:
- Secures access to internally hosted applications.
- Ensures only authorized and compliant users have access to only the applications they need, using a least-privilege Zero Trust model.
- Secures access to ZIA-hosted applications via [Source IP Anchoring](/zia/configuring-source-ip-anchoring).
Deployment Phase
The deployment phase initially sets up and integrates ZPA solutions into an existing network infrastructure. During the deployment phase, you configure ZPA Access Policies to meet the needs of your infrastructure. The following sections discuss steps to deploy ZPA Access Policies.
Prerequisites
For Access Policy deployment, verify and complete the following prerequisites:
- One of the following Zscaler subscriptions is required:
- ZPA core software
- Source IP Anchoring (SIPA) module (optional)
- Defined and deployed [App Connector](/zpa/about-connectors)s.
- Defined applications.
- Defined access criteria.
- (Optional) [Security Assertion Markup Language (SAML)](/zpa/about-saml-attributes) or [System for Cross-domain Identity Management (SCIM)](/zpa/about-scim) attributes.
Deployment Steps
The following steps explain how to configure a ZPA Access Policy:
- Define whether all App Connectors can communicate with the applications, or only specific App Connector groups, or Server groups can communicate with the applications.
- Define whether the policy is an **Allow **or **Block **policy.
The default policy behavior is to block access.
- [Configure the desired Access Policy](/zpa/configuring-access-policies) based on the required criteria:
- [Applications](/zpa/configuring-access-policies#apps)
- [Client Connector Posture Profiles](/zpa/configuring-access-policies#postureprofile)
- [Client Connector Trusted Networks](/zpa/configuring-access-policies#networks)
- [Client Types](/zpa/configuring-access-policies#client)
- [Cloud Connector Groups](/zpa/configuring-access-policies#CloudConnectorGroups)
- [Machine Groups](/zpa/configuring-access-policies#machinegrps)
- [SAML and SCIM Attributes](/zpa/configuring-access-policies#samlscimattribute)
Zscaler always displays the Boolean logic between criteria. For example, when a user requests access to an application, the policy rule is evaluated to check if an application segment *or* its segment group are present *and *whether any of the SAML attributes apply to the user requesting before it grants or denies access. You can always view the **Rule Action** and **Criteria **and the applied Boolean logic on the [Access Policy page](/zpa/about-accesspolicy).
- To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies).
Considerations
Review the following considerations:
- If applying any Posture Checking rules for users connected to Zscaler Client Connector, remember to configure the [Posture Checking Profiles](/zscaler-client-connector/about-device-posture-profiles) in the ZPA Admin Portal and ensure the endpoints can pass the check (i.e., a certificate check requires a certificate is deployed to the endpoint).
- ZPA Access Policies process on a specific and top-down methodology. For example, if rule 1 blocks *.web.com but rule 2 allows specific.web.com, rule 2 allows access to specific.web.com for a user. Any other subdomain of web.com is blocked. When both FQDNs are equal, ZPA performs a top-down ranking approach. So, if rule 1 is *.specific.web.com and rule 2 is specific.web.com, then rule 1 would apply, because it’s processed first.
- If you use SCIM as the provisioning method, ensure that the initial SCIM cycle is complete before using any SCIM attributes in Access Policies. After you enable SCIM, Zscaler checks if a user is present in the SCIM database. Based on this information, Zscaler decides if the user is allowed or blocked access to ZPA. Ensure the SCIM user sync is complete before enabling SCIM policies for these users. If not, the ZPA service evaluates policies on the users it does not recognize.
- After SCIM sync is enabled, Zscaler recommends waiting for a minimum of 48 hours (sometimes up to a week) before enabling SCIM policies. It can take several days for the IdP to sync all user information to ZPA completely. Zscaler recommends enabling SCIM sync in advance before enabling SCIM attributes for policy.
Operations Phase
This section describes standard practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune ZPA Access Policies during operations to meet your infrastructure needs.
Prerequisites
For Access Policy operation, complete the following prerequisites:
- Zscaler recommends regularly reviewing ZPA Access Policies (at least annually) to ensure they still meet organizational objectives. It is also best practice to ensure Access Policies are still in use, relevant, and applied to the correct users.
- Document the process to create a new Access Policy and whether all App Connectors or specific App Connector groups or Server groups have access to the applications.
Common Troubleshooting Items
The following list describes common issues related to Access Policy operation:
- Application is not accessible: Check whether an Access Policy exists and whether the default behavior is an implicit block.
- Desktop notification ZPA Blocked Access: A configured Access Policy blocks access, and the user cannot meet the Access Policy criteria. Check the Access Policies for validation.
- Application is not accessible due to failed Posture Check:
- Check the ZPA diagnostic logs to determine the reason for the failed posture check.
- Ensure the endpoint has the configuration to pass the posture check (i.e., the endpoint has the correct certificate for Certificate Posture Check type).
- Application is not accessible due to No App Connector Available:
- Check that the Access Policies define the correct App Connectors that can access the application.
- Check general network connectivity.
- Check that the App Connector is connected to the ZPA Public Service Edge or Private Service Edges.
Deployment Checklist
Zscaler recommends downloading the [Access Policy Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zpa-deployments-operations/access-policy-deployment-and-operations-guide/Access-Policy-Deployment-Operations-Checklist.pdf) to help plan and implement ZPA Access Policy: [Download PDF](/downloads/zscaler-deployments-operations/zpa-deployments-operations/access-policy-deployment-and-operations-guide/Access-Policy-Deployment-Operations-Checklist.pdf)
Additional Information
For more Access Policy information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and [Zscaler Zenith Community](https://community.zscaler.com/).