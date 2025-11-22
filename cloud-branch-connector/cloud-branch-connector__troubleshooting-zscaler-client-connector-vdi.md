# Troubleshooting Zscaler Client Connector for VDI
Source: https://help.zscaler.com/cloud-branch-connector/troubleshooting-zscaler-client-connector-vdi
PDF: https://help.zscaler.com/pdf/com/en/1494866.pdf

This article provides troubleshooting information and guidelines for Zscaler Client Connector for Virtual Desktop Infrastructure (VDI) deployment. You can review issues and corresponding solutions for Zscaler Client Connector for VDI. If you cannot reach a solution, contact Zscaler Support. Additionally, ensure that you bypass services you want to keep local to Microsoft Azure or Citrix. To learn more about bypasses, see [Configuring VDI Forwarding Profiles](/cloud-branch-connector/configuring-vdi-forwarding-profiles).
- [Registration](#Registration)
- [Authentication](#Authentication)
- [Data Path](#DataPath)
[]
The following registration troubleshooting flow chart leads you through various Zscaler Client Connector for VDI situations and potential solutions.
[See image.](#RegistrationFlowchart)
The following table lists Zscaler Client Connector for VDI registration issues and their corresponding troubleshooting actions.
[](/cloud-branch-connector/troubleshooting)[](/cloud-branch-connector/customizing-zscaler-client-connector-vdi-install-options-msi)
| **Potential Causes** | **Troubleshooting Action** |
| -------------------- | -------------------------- |
| Zscaler Client Connector for VDI is experiencing location fetch errors. | Location fetch errors can occur for multiple reasons. Collect Zscaler Client Connector for VDI's logs and contact Zscaler Support. |
| The Zscaler Cloud & Branch Connector service interface is unreachable or Cloud & Branch Connector is displayed inactive. | Test whether the Cloud & Branch Connector service interface is reachable with and without Zscaler Client Connector for VDI. To learn more, see the Cloud Connector troubleshooting documentation. |
| The Zscaler Client Connector for VDI onboard parameter is not set. | Ensure that the onboarding behavior is set to either `1` or `0`. The default is `1`, which allows Zscaler Client Connector for VDI to onboard itself to the Workload Communications (WLC) tenant. Setting the behavior to `0` disables this automatic behavior. To learn more, see Customizing Zscaler Client Connector for VDI with Install Options for MSI. |
| Routing is not configured for `185.46.212.80`. | By default, Zscaler Client Connector for VDI connects to `185.46.212.80`. Ensure that a route is configured for this destination pointing toward the Cloud Connector, Branch Connector, or a load balancer. |
[]
The following authentication troubleshooting flow chart guides you through various Zscaler Client Connector for VDI situations and potential solutions.
[See image.](#AuthenticationFlowchart)
The following table lists Zscaler Client Connector for VDI authentication issues and their corresponding troubleshooting actions.
-
- [](/cloud-branch-connector/customizing-zscaler-client-connector-vdi-install-options-msi)
[](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-sso-quick-start)[](https://help.okta.com/en-us/content/topics/directory/configuring_agentless_sso.htm)
| **Potential Causes** | **Troubleshooting Action** |
| -------------------- | -------------------------- |
| User authentication is failing. | User authentication can fail for multiple reasons:When the VDI environment completes a backup and restoration of the roaming profile, Zscaler Client Connector for VDI stores and reads the user configuraton file in the roaming profile. This restoration process can take time. Configure the `CONFIGREADTIMEOUT` parameter so that Zscaler Client Connector for VDI waits a minimum of 0 and a maximum of 300 seconds for profiles to restore.If the virtual machine (VM) loads more slowly than Zscaler Client Connector for VDI, a timeout issue might occur. Configure the timeout parameter to wait for the window to load completely before showing the authentication page. To learn more, see Customizing Zscaler Client Connector for VDI with Install Options for MSI. |
| Integrated Windows Authentication (IWA) is failing. | IWA relies on browser and/or Internet settings, so review your configured settings and refer to the Microsoft documentation. |
| Okta ADSSO authentication is failing. | Refer to the Okta documentation. |
| Profile backup and restore is not working. | Ensure that the backup and restore IP addresses are bypassed. |
| FSLogix is not able to restore the user profile. | Ensure that all FSLogix IP addresses are bypassed. |
| Zscaler Client Connector for VDI is not able to reach the identity provider (IdP). | Ensure that there is a bypass from the Zscaler Cloud & Branch Connector Admin Portal and FQDN bypasses from the Cloud Connector. |
| Zscaler Client Connector for VDI is not able to reach Zscaler authentication domains. | Ensure that all Zscaler authentication domains are bypassed. |
| You do not see the correct user when navigating to `ip.zscaler.com`. | Ensure that all bypasses and authentications are functioning. Collect the packet captures and ensure that traffic is tunneled properly. |
[]
- [ZIA](#ZIADataPath)
- [ZPA](#ZPADataPath)
[]
The following Zscaler Internet Access (ZIA) data path troubleshooting flow chart guides you through various Zscaler Client Connector for VDI situations and potential solutions.
[See image.](#ZIADataPathFlowchart)
To learn more about routing traffic through `185.46.212.80`, see [What Is Zscaler Client Connector for VDI?](/cloud-branch-connector/what-zscaler-client-connector-vdi)
The following table lists Zscaler Client Connector for VDI ZIA data path issues and their corresponding troubleshooting actions.
[](/cloud-branch-connector/what-zscaler-client-connector-vdi)
[](/cloud-branch-connector/troubleshooting)
| **Potential Causes** | **Troubleshooting Action** |
| -------------------- | -------------------------- |
| The incorrect tunnel mode is configured for Zscaler Client Connector for VDI. | You can configure Point-to-Point (P2P) or Any-to-Any (A2A) tunneling mode for Zscaler Client Connector for VDI. To determine which tunneling mode is appropriate, see What Is Zscaler Client Connector for VDI?A2A Tunneling Mode is not recommended and is being deprecated. |
| Traffic is not reaching ZIA. | Review the Cloud Connector session insights to verify whether the traffic is forwarded to ZIA. To learn more, refer to the Cloud Connector troubleshooting documentation. |
| Traffic is not reaching Cloud Connector or Branch Connector. | Ensure that workload routes are properly configured to send the traffic to Cloud Connector and the traffic forwarding rule is configured to send traffic to ZIA. |
| The incorrect policy is applied in ZIA. | In the ZIA Admin Portal, check the ZIA insights logs and match them with the rule preceding the correct rule. |
[]
The following Zscaler Private Access (ZPA) data path troubleshooting flow chart guides you through various Zscaler Client Connector for VDI situations and potential solutions.
[See image.](#ZPADataPathFlowchart)
To learn more about P2P and A2A tunneling modes, see [What Is Zscaler Client Connector for VDI?](/cloud-branch-connector/what-zscaler-client-connector-vdi)
The following table lists Zscaler Client Connector for VDI ZPA data path issues and their corresponding troubleshooting actions.
[](/cloud-branch-connector/step-step-configuration-guide-zscaler-client-connector-vdi)
| **Potential Causes** | **Troubleshooting Action** |
| -------------------- | -------------------------- |
| Server Message Block (SMB), Kerberos, Windows network, DNS, ICMP, or network file system (NFS) traffic are not able to reach the destination application. | SMB, Kerberos, Windows network, DNS, ICMP, and NFS traffic are treated as system user traffic by Zscaler Client Connector for VDI. Ensure that ZPA has a correct access policy configured for the system user.This is a Windows limitation, not a Zscaler limitation. |
| Traffic is not reaching Cloud Connector or Branch Connector. | Ensure that workload routes are properly configured to send the traffic to Cloud Connector and the traffic forwarding rule is configured to send traffic to ZPA. |
| The incorrect access policy is applied in ZPA. | Ensure that the access policy is configured with the client type as Zscaler Client Connector for VDI. If the access policy contains user attributes, enable System for Cross-domain Identity Management (SCIM). SAML is not supported. |
| The incorrect application segment is selected in ZPA. | Check the application segment configuration in ZPA to verify that it is correct. |
| Synthetic IP pool is not included in the VDI forwarding profile. | Ensure that the VDI forwarding policy includes synthetic IP pools in the Include list. |
| DNS requests are not being received. | Ensure that Cloud Connector is seeing DNS requests and able to match them to the ZPA application or FQDN. To learn more, see Step-by-Step Configuration Guide for Zscaler Client Connector for VDI. |
[]
![Registration](/downloads/cloud-branch-connector/zscaler-client-connector-vdi-management/troubleshooting-zscaler-client-connector-vdi/Registration_Troubleshooting.svg)
[]
![Authentication](/downloads/cloud-branch-connector/zscaler-client-connector-vdi-management/troubleshooting-zscaler-client-connector-vdi/Authentication_Troubleshooting.svg)
[]
![ZIA Data Path](/downloads/cloud-branch-connector/zscaler-client-connector-vdi-management/troubleshooting-zscaler-client-connector-vdi/ZIA_Troubleshooting.svg)
[]
![ZPA Data Path](/downloads/cloud-branch-connector/zscaler-client-connector-vdi-management/troubleshooting-zscaler-client-connector-vdi/ZPA_Troubleshooting.svg)