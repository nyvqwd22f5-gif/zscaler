# Configuring VDI Forwarding Profiles
Source: https://help.zscaler.com/cloud-branch-connector/configuring-vdi-forwarding-profiles
PDF: https://help.zscaler.com/pdf/com/en/1471726.pdf

This article provides information on how to configure a Virtual Desktop Infrastructure (VDI) forwarding profile and bypass information. To learn more about VDI forwarding profiles, see [About VDI Forwarding Profiles](/cloud-branch-connector/about-vdi-agent-forwarding-profiles).
To add a VDI forwarding profile:
- Log in to the Zscaler Cloud & Branch Connector Admin Portal.
- Go to **Administration** > **VDI Forwarding Profile**.
- Click **Add VDI Forwarding Profile**.
- On the **Add VDI Forwarding Profile** page:
- **Name**: Enter a name for the forwarding profile.
- **Description**: Enter a description for the forwarding profile.
- **Include IP Addresses**: Enter IP addresses to include traffic from the tunnel to the Cloud Connector or Branch Connector. Add Zscaler Private Access (ZPA) synthetic IP pools in the inclusion list. You can enter IP addresses in the following formats:
- An IP address, such as `198.51.100.100`
- An IP address with a netmask, such as `203.0.113.0/24`
- An IP address:port range, such as `192.0.2.1:80 or 192.0.2.1` for all ranges
-
An IP address:port:protocol, such as `192.0.2.1:80:TCP`, `192.0.2.1/24:80-100:UDP`, or `192.0.2.1:80` for all protocols
Including IP addresses is not required to create a VDI forwarding profile. However, doing so enables you to control specific routing behavior by excluding certain traffic destinations from being processed by Zscaler Client Connector for VDI and the Zscaler service.
-
**Exclude IP Addresses**: Enter IP addresses to exclude traffic from the tunnel to the Cloud Connector or Branch Connector. You can enter IP addresses in the following formats:
- An IP address, such as `198.51.100.100`
- An IP address with a netmask, such as `203.0.113.0/24`
- An IP address:port range, such as `192.0.2.1:80 or 192.0.2.1` for all ranges
- An IP address:port:protocol, such as `192.0.2.1:80:TCP`, `192.0.2.1/24:80-100:UDP`, or `192.0.2.1:80` for all protocols
[See image.](#AddVDIAgentForwardingProfile)
- Click **Submit**.
Bypasses
Zscaler recommends bypassing certain IP addresses and fully qualified domain names (FQDNs) depending on whether you are using Microsoft Azure or Citrix for FSLogix:
- [Azure IP Addresses and FQDNs](#AzureIPFQDN)
- [Citrix IP Addresses and FQDNs](#CitrixIPFQDN)
[]
Zscaler recommends bypassing certain IP addresses and fully qualified domain names (FQDNs) to ensure that traffic remains local to environments such as Microsoft Azure, rather than being forwarded to Zscaler Internet Access (ZIA). Services such as monitoring agents and login functionalities should remain local to Azure.
To find Azure IP ranges and service tags specific to a particular region, refer to the [Microsoft documentation](https://www.microsoft.com/en-us/download/details.aspx?id=56519) and filter the list for your desired region. For Azure Virtual Desktop (AVD), bypass required FQDNs, endpoints, and destination IP addresses referred to in the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/virtual-desktop/required-fqdn-endpoint?tabs=azure). For Microsoft 365 applications running on Zscaler Client Connector for VDI, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide#microsoft-365-common-and-office-online) to see which Microsoft 365 URLs and IP address ranges to bypass.
[]
If your Citrix environment uses any of the Rendezvous protocols, then it might need to be bypassed from Cloud Connector. To learn more, refer to the [Citrix documentation](https://support.citrix.com/s/article/CTX270584-citrix-gateway-service-pointsofpresence-pops?language=en_US). Ensure that Citrix's connectivity requirements are added to the bypass list or allow them to go through Zscaler Internet Access (ZIA) to reach their destinations. For more information on the Citrix system and connectivity requirements, refer to the [Citrix documentation](https://docs.citrix.com/en-us/citrix-cloud/overview/requirements/internet-connectivity-requirements.html). To see an updated list of Citrix FQDNs, refer to the [Citrix documentation](https://support.citrix.com/s/article/CTX270584-citrix-gateway-service-pointsofpresence-pops?language=en_US). If you are using Citrix Profile Management or any separate storage account for profile management, ensure it bypasses Cloud Connector traffic forwarding.
[]![The Add VDI Agent Forwarding Profile page](/downloads/cloud-branch-connector/zscaler-client-connector-vdi-management/configuring-vdi-templates/ConfiguringVDIForwardingProfile.png)