# Zscaler Client Connector Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/zscaler-client-connector-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1420036.pdf

This guide describes how to use Zscaler Client Connector and the steps necessary for configuring Zscaler Client Connector. Zscaler Client Connector is a lightweight application that runs on a user’s endpoint device. Zscaler Client Connector automatically forwards all user traffic to the closest Zscaler Public Service Edge and enforces security and access policies across all devices, locations, and applications.
With Zscaler Private Access (ZPA) enabled, users can securely access your organization's internal resources from any location. Using Zscaler Digital Experience (ZDX), Zscaler Client Connector synthetically probes Software as a Service (SaaS) applications or internet-based services (e.g., OneDrive, Gmail, etc.) to triage and pinpoint the source of performance issues.
To learn more, see [What is Zscaler Client Connector](/zscaler-client-connector/what-is-zscaler-client-connector)[?](/zscaler-client-connector/what-zscaler-app)
Value of Deploying User Provisioning and Authentication
Using Zscaler Client Connector provides the following benefits:
- Zero Trust policies follow users regardless of devices, locations, or applications accessed.
- Enhances the user experience and streamlines application access.
- Centralizes control and policy management.
- Tracks and monitors user and device activities for IT teams.
- Supports popular operating systems and device types (e.g., laptops, smartphones, tablets, etc.).
- Strictly enforces internet access criteria for users not enrolled in Zscaler Client Connector.
Deployment Phase
The deployment phase initially sets up and integrates Zscaler Client Connector. During the deployment phase, you configure Zscaler Client Connector to meet the needs of your infrastructure. The following sections discuss the steps to deploy Zscaler Client Connector.
Prerequisites
For Zscaler Client Connector deployment, observe the following prerequisites:
- Verify the [system requirements](/zscaler-client-connector/step-step-configuration-guide-zscaler-client-connector#step-1).
- Zscaler Client Connector does not require an additional license or subscription. Licensing for ZIA and ZPA includes Zscaler Client Connector.
Deployment Steps
The following steps explain how to deploy Zscaler Client Connector:
- Complete [system requirements and prerequisite tasks](/zscaler-client-connector/step-step-configuration-guide-zscaler-client-connector#step-1).
- Allowlist [Zscaler Client Connector processes](/zscaler-client-connector/zscaler-app-processes-whitelist) on client firewall and antivirus (AV).
- Allow [Zscaler Client Connector communication](https://config.zscaler.com/zscaler.net/zscaler-app) to the Zscaler cloud through your organization's firewall.
- [Download Zscaler Client Connector](/zscaler-client-connector/downloading-zscaler-client-connector) from an app store.
- (Optional) Customize [Zscaler Client Connector with installer options](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-msi).
- Use your organization’s device management system to [deploy Zscaler Client Connector](/zscaler-client-connector/deploying-zscaler-app-active-directory-windows).
Considerations
Review the following considerations:
- If your users are running Zscaler Client Connector in conjunction with virtual private network (VPN) clients or VPN-like applications (e.g., Microsoft DirectAccess), check that users aren’t experiencing interoperability issues.
- For a complete list of recommended steps, see [Best Practices for Zscaler Client Connector and VPN Client Interoperability](/zscaler-client-connector/best-practices-zscaler-app-and-vpn-client-interoperability).
- Ensure all authentication traffic goes directly to the identity provider (IdP) destination URL. Users who are off the trusted network and forwarding traffic via Zscaler Client Connector should not experience issues. However, check that other authentication traffic (e.g., PAC files, GRE tunnels, and IPSec tunnels) goes directly to the IdP.
- Make sure traffic destined for the IdP that goes through Zscaler is not intercepted for inspection by Zscaler:
- Adjust [SSL Inspection exemptions](/zscaler-client-connector/configuring-ssl-inspection-zscaler-app#exempting-URLs-SSL).
- Adjust [Authentication exemptions](/zia/exempting-urls-cloud-apps-authentication).
- If you are using Microsoft Windows Autopilot, see the [Zscaler and Microsoft Windows Autopilot Deployment Guide](/zscaler-technology-partners/zscaler-and-microsoft-windows-autopilot-deployment-guide).
Operations Phase
This section describes standard practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune Zscaler Client Connector during operations to meet your infrastructure needs.
Prerequisites
For Zscaler Client Connector operations, observe the following prerequisites:
- Create a standard operating procedure (SOP) for adding domain bypasses in the PAC file used by Zscaler Client Connector.
- Define a process to test configuration changes, such as diverting traffic to a different data center or bypassing a PAC file.
- Test any changes with separate app profiles or PAC files and apply the policy to test users to avoid organization-wide impact.
- Implement a process to clean up test profiles and PAC files.
Deployment Checklist
Zscaler recommends downloading the [Zscaler Client Connector Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zscaler-client-connector-deployments-operations/zscaler-client-connector-deployment-and-operations-guide/Zscaler-Client-Connector-Deployment-Operations-Checklist.pdf) to help plan and implement Zscaler Client Connector: [Download PDF](/downloads/zscaler-deployments-operations/zscaler-client-connector-deployments-operations/zscaler-client-connector-deployment-and-operations-guide/Zscaler-Client-Connector-Deployment-Operations-Checklist.pdf)
Additional Information
For more Zscaler Client Connector information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](https://community.zscaler.com/).