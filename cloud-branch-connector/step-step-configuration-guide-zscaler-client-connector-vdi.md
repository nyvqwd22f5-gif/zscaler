# Step-by-Step Configuration Guide for Zscaler Client Connector for VDI
Source: https://help.zscaler.com/cloud-branch-connector/step-step-configuration-guide-zscaler-client-connector-vdi
PDF: https://help.zscaler.com/pdf/com/en/1472246.pdf

This guide takes you step-by-step through the configuration tasks you must complete to begin using Zscaler Client Connector for Virtual Desktop Infrastructure (VDI) for your organization.
To enable this feature, contact Zscaler Support.
Before you begin configuring Zscaler Client Connector for VDI, Zscaler recommends reading the following articles:
- [What Is Zscaler Client Connector for VDI?](/cloud-branch-connector/what-zscaler-vdi-agent)
- [Accessing and Navigating the Zscaler Cloud & Branch Connector Admin Portal](/cloud-branch-connector/accessing-navigating-zscaler-cloud-branch-connector-admin-portal)
- [What Is Zscaler Cloud Connector?](/cloud-branch-connector/what-zscaler-cloud-connector)
- [What Is Zscaler Branch Connector?](/cloud-branch-connector/what-zscaler-branch-connector)
- [Understanding the ZIA Cloud Architecture](/zia/understanding-zscaler-cloud-architecture)
- [Understanding the ZPA Cloud Architecture](/zpa/understanding-zpa-cloud-architecture)
Configuring Zscaler Client Connector for VDI
To configure Zscaler Client Connector for VDI, complete the following steps:
- [Step 1: Review the System Requirements](#step-1)
- [Step 2: Review the Zscaler Firewall Requirements](#step-2)
- [Step 3: Deploy Zscaler Cloud Connector or Zscaler Branch Connector](#step-3)
- [Step 4: Configure the VDI Templates](#step-4)
- [Step 5: Configure the VDI Forwarding Profile](#step-5)
- [Step 6: Configure Dynamic VDI Groups](#step-6)
- [Step 7: Customize Zscaler Client Connector for VDI with Installer Options](#step-7)
- [Step 8: Configure DNS for ZPA](#step-8)
- [Step 9: (Optional) Review Best Practices for FSLogix, Citrix, and AVD](#step-9)
[]Zscaler Client Connector for VDI currently supports only modern Windows operating systems. You must be running Windows 10 or Windows Server 2016 or later. Additionally, only Azure Virtual Desktop and Citrix, on-premises and cloud-hosted, have been tested. Other vendors might work, but have not been tested.
[]Before you begin configuring Zscaler Client Connector for VDI, you must deploy Zscaler Cloud Connector to a cloud provider or Zscaler Branch Connector to a hypervisor host.
For Cloud Connector deployment, see the following articles:
- [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector)
- [Deploying Zscaler Cloud Connector with Amazon Web Services](/cloud-branch-connector/deploying-zscaler-cloud-connector-amazon-web-services)
- [Deploying Zscaler Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure)
- [Deploying Zscaler Cloud Connector on the Google Cloud Platform](/cloud-branch-connector/deploying-zscaler-cloud-connector-google-cloud-platform)
Amazon Web Services (AWS) and Google Cloud Platform (GCP) are not supported by Zscaler Client Connector for VDI.
For Branch Connector deployment, see the following articles:
- [Downloading Branch Connector Images](/cloud-branch-connector/downloading-branch-connector-images)
- [Deployment Templates for Zscaler Branch Connector & App Connector](/cloud-branch-connector/deployment-templates-zscaler-branch-connector-app-connector)
- [Deploying Branch Connector on VMware Platforms](/cloud-branch-connector/deploying-branch-connector-vmware-platforms)
- [Deploying Branch Connector with Linux KVM](/cloud-branch-connector/deploying-branch-connector-linux-kvm)
If you leverage load balancers to distribute traffic to Cloud Connector or Branch Connector, Zscaler recommends using source IP address affinity (2-tuple) hashing.
[]The Cloud Connector and Branch Connector instances require only outbound connections to the Zscaler cloud. They do not require any inbound connections to your network from the Zscaler cloud. For user authentication, Zscaler Client Connector for VDI communicates with the Zscaler cloud using TCP/443. It also requires UDP/7443 to be open between the application software and the Cloud Connector or Branch Connector. This is how Zscaler Client Connector for VDI tunnels traffic to the Cloud Connector or Branch Connector. UDP/7443 to the Cloud Connector or Branch Connector and TCP/443 to the Zscaler cloud are required. Additionally, Zscaler Client Connector for VDI connects on TCP 9090 to the Cloud Connector service endpoint for policy updates. To view the outbound access requirements for your specific account, go to the following URL: https://config.zscaler.com/<Zscaler Cloud Name>/cloud-branch-connector.
You can find the <Zscaler Cloud Name> in the URL you use to log in to the Cloud & Branch Connector Admin Portal. For example, if you log in to connector.zscaler.net, then go to https://config.zscaler.com/zscaler.net/cloud-branch-connector. To learn more, see [What Is My Cloud Name for Zscaler Cloud & Branch Connector?](/cloud-branch-connector/what-my-cloud-name-zscaler-cloud-branch-connector)
[]The VDI templates allow you to create a set of required configurations, including the provisioning URL, authentication token, and end user authentication method. These configurations are then applied to Zscaler Client Connector for VDI.
To configure VDI templates with Zscaler Internet Access (ZIA), assign an identity provider (IdP) and System User to the template. Zscaler Client Connector for VDI uses the IdP configured in the ZIA tenant.
To configure VDI templates with Zscaler Private Access (ZPA), ensure that SCIM and [SCIM Attributes for Policy](/zpa/enabling-scim-identity-management) are enabled for ZPA user attribution to function. Zscaler Client Connector for VDI uses the IdP configured in the ZIA tenant for both ZIA and ZPA. For ZPA, the ZIA IdP provides the authentication and passes a token to ZPA, authenticating the user to the ZPA platform. For ZPA and wildcard Fully Qualified Domain Name (FQDN) forwarding to work, send all DNS requests through Cloud Connectors.
To learn more, see the following articles:
- [About VDI Templates](/cloud-branch-connector/about-vdi-agent-templates)
- [Configuring VDI Templates](/cloud-branch-connector/configuring-vdi-templates)
[]The VDI forwarding profiles allow you to create forwarding rules to include or exclude destinations from being encapsulated in the tunnels that Zscaler Client Connector for VDI creates.
To configure VDI forwarding profiles with ZIA, Zscaler recommends configuring a single 0.0.0.0/0 inclusion rule. The application automatically excludes RFC 1918 traffic (i.e., 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/24, and 224.0.0.0/4). You can adjust the exclusion list to add additional private ranges. For example, Microsoft Azure users might choose to include the Automatic Private IP Addressing (APIPA) address range of 169.254.0.0/16 and Microsoft's dedicated 168.63.129.16/32 IP. If you are implementing Conditional Access policies in Azure, consider the URL-based bypasses that Microsoft recommends for Microsoft 365 and Azure Virtual Desktop to function correctly. Execute the bypasses in the Cloud & Branch Connector Admin Portal. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide) and [Azure documentation](https://learn.microsoft.com/en-us/azure/virtual-desktop/required-fqdn-endpoint?tabs=azure).
To configure VDI forwarding profiles with ZPA, you must make additional changes to the synthetic IP pool used for ZPA. This synthetic IP pool is configured in the Cloud & Branch Connector Admin Portal. Zscaler recommends adding your synthetic IP ranges, set to 10.254.0.0/19 by default, to the inclusion list of your Zscaler VDI Agent forwarding profile to ensure that the traffic is properly tunneled to the Cloud Connector or Branch Connector. If your VDI forwarding profile excludes ZPA synthetic IP pools, then some ZPA functionalities might be unavailable.
To learn more, see the following articles:
- [About VDI Forwarding Profiles](/cloud-branch-connector/about-vdi-agent-forwarding-profiles)
- [Configuring VDI Forwarding Profiles](/cloud-branch-connector/configuring-vdi-agent-forwarding-profiles)
Zscaler Client Connector for VDI does not support ZPA features such as server-to-client connectivity for remote access, client forwarding policy for client types as Zscaler Client Connector for VDI, and double encryption. However, if the [client forwarding policy](/zpa/about-client-forwarding-policy) is required, the client type of the Cloud Connector or Branch Connector is supported, and you can use it in the same way.
[]VDI groups allow administrators to dynamically apply Maximum Transmission Unit (MTU) and forwarding profile values to VDI applications as they register VDI devices and groups.
To learn more, see the following articles:
- [About VDI Devices](/cloud-branch-connector/about-vdi-devices)
- [About VDI Groups](/cloud-branch-connector/about-vdi-groups)
- [Configuring VDI Groups](/cloud-branch-connector/configuring-vdi-groups)
[]You can configure the Zscaler Client Connector for VDI installer file with installation options that allow you to remove steps from the user-enrollment process and enable or disable specific features of Zscaler Client Connector for VDI. To learn more, see[ Customizing Zscaler Client Connector for VDI with Install Options for MSI](/cloud-branch-connector/customizing-zscaler-vdi-agent-install-options-msi).
[]
To enable Zscaler Client Connector for VDI to connect to ZPA access, route DNS queries through Cloud Connector. In Azure, Zscaler Client Connector for VDI uses the Azure DNS server with the IP address `168.63.129.16` by default. If this IP address is included in the [VDI forwarding profile](/cloud-branch-connector/configuring-vdi-forwarding-profiles) Include list, DNS queries are handled by Cloud Connector. If it is in the [VDI forwarding profile](/cloud-branch-connector/configuring-vdi-forwarding-profiles) Exclude list, ensure that the DNS request is sent toward Cloud Connector.
- If `168.63.129.16` is the primary DNS server for the Azure virtual network (VNet), you can use the private Azure outbound DNS resolver to route specific domains, such as ZPA applications, to the Cloud Connector for resolution.
- If the Azure VNet uses a custom DNS server, you can add the DNS server to the [VDI forwarding profile](/cloud-branch-connector/configuring-vdi-forwarding-profiles) Include list, and DNS requests are forwarded to Cloud Connector by default. If you add a custom DNS server to the [VDI forwarding profile](/cloud-branch-connector/configuring-vdi-forwarding-profiles) Exclude list, ensure that a route toward the Cloud Connector is configured on the Azure Virtual Desktop (AVD) subnet. If the AVD subnet is not configured to send the default route to the Cloud Connector, ensure that DNS traffic is directed toward the Cloud Connector.
- A default rule is configured to send all traffic to ZIA. If you do not want the DNS traffic to be sent to ZIA, add a direct traffic forwarding rule to the Cloud Connector cluster so that this traffic bypasses ZIA.
For ZPA use cases, include the ZPA synthetic IP pool in the [VDI forwarding profile](/cloud-branch-connector/about-vdi-forwarding-profiles).
[]
Zscaler recommends the following best practices when configuring FSLogix, Citrix, or AVD for Zscaler Client Connector for VDI:
- [FSLogix](#FSLogix)
- [Citrix](#Citrix)
- [AVD](#AVD)
[]
The following best practices apply to FSLogix:
- Storage Account Bypass: You can host the Azure storage account on a public IP address or on an Azure Private Link. Zscaler recommends using an Azure Private Link. Bypass the Azure storage account IP address in the VDI forwarding profile so the traffic can go directly from the Windows session host to the FSLogix storage account.
- Azure Storage Account Firewall Policies: Azure storage accounts are protected by firewall policies, and everything from outside the Azure VNet is dropped by default. Depending on the designated traffic flow, you can decide whether the firewall policy allows the Cloud Connector service interface IP address, the NAT gateway public IP address, or the Zscaler Public Service Edge IP address.
-
Azure resources (Microsoft Learn): Azure has a unique, global IP address, `168.63.129.16`. It is the default DNS server for all Azure instances and the gateway to other Azure resources such as the Azure Windows VM Agent. Traffic to the IP address must be bypassed latest on the Cloud Connector traffic forwarding profile for the following ports:
- UDP/53
- TCP/53
- TCP/80
- TCP/443
- TCP/32526
Microsoft owns the IP address `168.63.129.16`. If Microsoft changes this IP address, update it to match.
- DNS Resolution: To prepare for enrollment, bypass the DNS server IP address, `168.63.129.16`, in Cloud Connector traffic forwarding rules, and not in Zscaler Client Connector for VDI itself.
- When the FSLogix storage account is a default account, the FQDN of the account is always resolved as a public IP address.
- When the FSLogix storage account is using a private link connection, DNS requests for the FQDN from Azure networks are resolved into the private IP address assigned to the private link. External requests, such as requests from the Zscaler Public Service Edge, are resolved with the storage accounts' public IP address.
- Azure Instance Metadata Service: Azure instances communicate with the hypervisor host through `169.254.0.0/19`, which should be bypassed in Zscaler Client Connector for VDI.
- Cloud Connector Network Security Group: The default network security group deployed within the Azure Marketplace only allows TCP/443, UDP/443, and TCP/80. For storage accounts, enable the account IP address with TCP/443, UDP/443, TCP/80, UDP/53, TCP/53, TCP/445, and UDP/445.
[]
The following best practices apply to Citrix:
- To prevent bootup during MCS creation, ensure that the Zscaler service and ZCCVDIService are not running.
- If you are using XenApp, Zscaler recommends always using an embedded browser and SSO.
- Bypass Citrix Profile Management and Citrix Rendezvous protocols for them to function correctly. To learn more about bypasses, see [Configuring VDI Forwarding Profiles](/cloud-branch-connector/configuring-vdi-forwarding-profiles#CitrixIPFQDN).
- When installing Zscaler on a Citrix image VM, ensure that you are using the onboarding parameter 0. To learn more about command line arguments when creating a MCS golden image, see [Customizing Zscaler Client Connector for VDI with Install Options for MSI](/cloud-branch-connector/customizing-zscaler-client-connector-vdi-install-options-msi).
To learn more, refer to the [Citrix documentation](https://docs.citrix.com/en-us/citrix-cloud/overview/requirements/internet-connectivity-requirements.html).
[]
The following best practices apply to AVD:
- When using Microsoft Intune, ensure that all the command parameters are updated and formatted correctly. If you are using AVDs, search for `WindowsVirtualDesktop` in the JSON file for your region to receive the IP addresses to bypass.
- If you are configuring network security groups (NSGs), Zscaler recommends allowing traffic from Zscaler Client Connector for VDI. NSGs should not have any other proxies, third-party tools, virtual private networks (VPNs), or software that can hinder the system network.
- To learn more about Microsoft DNS, refer to [Step 8: Configure DNS for ZPA](/cloud-branch-connector/step-step-configuration-guide-zscaler-client-connector-vdi).
- To learn about best practices for Zscaler Client Connector for VDI, see [Downloading Zscaler Client Connector for VDI](/cloud-branch-connector/downloading-zscaler-client-connector-vdi) and [Customizing Zscaler Client Connector for VDI with Install Options for MSI](/cloud-branch-connector/customizing-zscaler-client-connector-vdi-install-options-msi).
To learn more about bypasses, see [Configuring VDI Forwarding Profiles](/cloud-branch-connector/configuring-vdi-forwarding-profiles#AzureIPFQDN).