# Client Forwarding Policy Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/client-forwarding-policy-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417936.pdf

This guide describes the benefits of using Client Forwarding Policy and the steps necessary for configuring Zscaler Private Access (ZPA) to add Client Forwarding policies to your security posture.
ZPA evaluates Client Forwarding Policy rules using the most specific application segment and a top-down, first-match principle. The process occurs before ZPA evaluates Access Policy rules. When ZPA finds a match in the Client Forwarding Policy, ZPA disregards other Client Forwarding Policy rules, including conflicts.
To learn more, see [About Client Forwarding Policy](/zpa/about-client-forwarding-policy).
Value of Deploying Client Forwarding Policy
Using Client Forwarding Policy provides more granular traffic control processing to meet your organization’s needs.
Deployment Phase
The deployment phase initially sets up and integrates ZPA solutions into an existing network infrastructure. During the deployment phase, you configure ZPA Client Forwarding Policy to meet the needs of your infrastructure. The following sections discuss steps to deploy ZPA Client Forwarding Policy.
Prerequisites
To use this feature, you must set the Application Segment bypass behavior to Client Forwarding Policy.
Deployment Steps
The following steps explain how to deploy ZPA Client Forwarding Policy:
- Configure a [Client Forwarding Policy](/zpa/configuring-client-forwarding-policies).
- Set the [Application Segment bypass behavior](/zpa/configuring-bypass-settings) to Use Client Forwarding Policy.
- When creating the Client Forwarding Policy, choose a rule action:
- Bypass ZPA: If selected, applications are marked and bypassed for ZPA, and Zscaler Client Connector does not send application requests to ZPA. This setting is the equivalent of selecting Always for the Bypass setting within an application segment. To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments).
- Only Forward Allowed Applications: If selected, Zscaler Client Connector learns about and forwards traffic for applications that a user is allowed to access. The Access Policy determines the list of applications to which the user has access. When Zscaler Client Connector sets up a connection to ZPA, the service determines the list of applications that a user can access and downloads this list to Zscaler Client Connector for forwarding traffic to ZPA. Zscaler Client Connector forwards requests for applications not on the list to the local network. Requests for these applications are not logged in ZPA.
- Forward to ZPA: If selected, Zscaler Client Connector forwards application requests to ZPA. This includes requests for applications that the user is not authorized to access. By default, these requests are logged in the Diagnostic logs as Policy not configured for access.
- Select a criteria option:
- [Applications](/zpa/configuring-client-forwarding-policies#apps)
- [Client Connector Posture Profiles](/zpa/configuring-client-forwarding-policies#postureprofile)
- [Client Connect Trusted Networks](/zpa/configuring-client-forwarding-policies#networks)
- [Client Types](/zpa/configuring-client-forwarding-policies#clients)
- [Machine Groups](/zpa/configuring-client-forwarding-policies#machinegrps)
- [Platforms](/zpa/configuring-client-forwarding-policies)
- [SAML and SCIM Attribute](/zpa/configuring-client-forwarding-policies#samlscimattribute)
Considerations
Review the following considerations:
- A Client Forwarding Policy might not be required for some applications. For example, you can configure an application to bypass ZPA when users are on the trusted network directly in the [Application Segment settings](/zpa/configuring-application-segments) (without a Client Forwarding Policy). This granularity is helpful for mergers and acquisitions where application access should be granted based on trusted network criteria.
- Select Only Forward Allowed Applications if you are setting up a Client Forwarding Policy to use as part of Source IP Anchoring in Zscaler Internet Access (ZIA).
- If you have multiple Client Forwarding Policy rules, apply Bypass ZPA and Forward to ZPA rule actions to the same application segment, the Forward to ZPA rule action takes precedence.
- For application segments, the bypass setting takes precedence over any new Client Forwarding Policy rule.
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune ZPA Client Forwarding Policy during operations to meet your infrastructure needs.
Prerequisites
Ensure that you thoroughly test the Client Forwarding Policy using different forwarding methods (especially when you have defined complex criteria sets).
Common Troubleshooting Items
The following list describes common issues related to Client Forwarding Policy operation:
- The Client Forwarding Policy is not successfully applied to the application: This occurs if Only Forward Allowed Applications is selected and an Access Policy allowing access was not created. In this case, the application the user is trying to reach is not present in the list of applications downloaded by Zscaler Client Connector.
- Another reason could be the configured behavior action does not match the criteria. For example, trusted network detection or posture checks might not match the defined criteria. Zscaler Client Connector re-evaluates posture checks at startup and every 15 minutes thereafter. For Trusted Network, verify that the user's network settings are configured to one of the defined settings in the trusted network criteria.
- The criteria are not being met: In this instance, check if the criteria definitions are using either an AND or OR operator. The operator choice could explain why the Client Forwarding Policy criteria are not being met and enforced.
Deployment Checklist
Zscaler recommends downloading the [Client Forwarding Policy Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zpa-deployments-operations/client-forwarding-policy-deployment-and-operations-guide/Client-Forwarding-Policy-Deployment-Operations-Checklist.pdf) to help plan and implement ZPA Client Forwarding Policy: [Download PDF](/downloads/zscaler-deployments-operations/zpa-deployments-operations/client-forwarding-policy-deployment-and-operations-guide/Client-Forwarding-Policy-Deployment-Operations-Checklist.pdf)
Additional Information
For more Client Forwarding Policy information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com).