# About Partner Integrations
Source: https://help.zscaler.com/zia/about-partner-integrations
PDF: https://help.zscaler.com/pdf/com/en/1400581.pdf

From the Partner Integrations page, you can integrate the Zscaler service with any of the following partners and services:
- [Microsoft Cloud App Security (MCAS)](#MCAS)
- [Software-Defined Wide Area Networking (SD-WAN)](#SD-WAN)
- [Microsoft Azure Virtual WAN (VWAN)](#Azure-VWAN)
- [CrowdStrike](#CrowdStrike)
- [Microsoft Defender for Endpoint](#Microsoft-Defender-Endpoint)
- [Votiro CDR for Isolation](#Votiro-CDR)
[]About the Partner Integrations Page
On the Partner Integrations page (Administration > Partner Integrations), you can do the following:
- [Integrate with Microsoft Cloud App Security](/zia/integrating-microsoft-cloud-app-security).
- [Manage SD-WAN partner keys](/zia/configuring-sdwan-integration).
- [Integrate with Azure Virtual WAN](/zia/integrating-microsoft-azure-virtual-wan).
- [Integrate with CrowdStrike](/zia/integrating-crowdstrike).
- [Integrate with Microsoft Defender for Endpoint](/zia/integrating-microsoft-defender-endpoint).
- [Use Votiro CDR for Isolation](/zscaler-technology-partners/zscaler-and-votiro-deployment-guide).
![Screenshot highlighting the Microsoft Cloud App Security, SD-WAN, Azure Virtual WAN, CrowdStrike, and Carbon Black tabs on the Partner Integrations page.](/downloads/zia/partner-integrations/about-partner-integrations/Partner-Integrations_about-menu.png)
[]Integrate with [MCAS](/zia/integrating-microsoft-cloud-app-security) to allow the Zscaler service to discover and sync Cloud Apps.
Integrating with MCAS allows you to utilize the Zscaler service's policy management functionality (i.e., URL filtering, custom category and Cloud App control, etc.) for blocking non-sanctioned applications. Your policies within the Zscaler service will include the list of applications to be blocked as provided by MCAS. The list consists of:
-
Applications known to the Zscaler service, which have app IDs and can be added as Cloud App control policies without the need to specify the explicit URLs to block.
-
Applications not known to the Zscaler service, which are provided as a list of URLs. The service will initially treat these URLs as unsanctioned Cloud Apps to denylist them using a custom category with a block policy rule applied to it.
For more information about Zscaler and MCAS, see the [Zscaler and Microsoft Defender for Cloud Apps Deployment Guide](/zscaler-technology-partners/zscaler-and-microsoft-defender-cloud-apps-deployment-guide).
For details about Zscaler's Cloud Access Security Broker (CASB) technology partners, see the [CASB partners site](https://www.zscaler.com/partners/technology/cloud-access-security-broker) or contact Zscaler Business Development.
[]Integrate [SD-WAN partner API access](/zia/configuring-sdwan-integration) for your organization's locations and VPN credential information.
An SD-WAN partner key enables partner access to the following resources within the [cloud service API](/zia/about-api#SDWAN):
- [Locations](/zia/location-management): Allows an SD-WAN partner to export all attributes of a Zscaler service-defined location as a request. Partners can also make resource requests to add, update, and delete locations instead of manually adding them or importing them via CSV file to the ZIA Admin Portal.
- [VPN Credentials](/zia/traffic-forwarding-0#/vpnCredentials-get): Allows an SD-WAN partner to configure IPSec tunnel parameters including pre-shared keys, fully qualified domain names (FQDNs), and their associated location names as a request.
Zscaler works with multiple SD-WAN partners, and [provides a separate deployment guide for each partner](/zscaler-technology-partners/zscaler-and-sd-wan-technology-partner-deployment-guides).
To learn more, see the [SD-WAN partner site](https://www.zscaler.com/partners/technology/sd-wan) or contact Zscaler Business Development.
[]Integrate with [Azure VWAN](/zia/integrating-microsoft-azure-virtual-wan) to forward traffic to the Zscaler service.
Azure VWAN is a networking service that provides optimized and automated branch connectivity to, and through, Azure. Azure regions serve as hubs that you can connect your branches to. To learn more, refer to the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/virtual-wan/virtual-wan-about).
Zscaler's integration leverages Microsoft's Azure VWAN APIs to discover and configure Azure hubs. The integration provides a one-click configuration to create outbound IPSec tunnels from Azure hubs to Zscaler data centers. This allows you to secure internet bound traffic from virtual networks (VNets) and branch offices without needing to set up any security appliances or use virtualized alternatives on Azure internet-as-a-service platforms.
[]Integrate with [CrowdStrike](/zia/integrating-crowdstrike) to enable immediate visibility, response, and containment to zero-day, [Sandbox](/zia/about-sandbox)-detected malware with the CrowdStrike endpoint protection platform.
Zscaler's integration leverages CrowdStrike APIs to identify traces of Sandbox-detected malware on CrowdStrike endpoint devices. This integration not only complements the Zscaler [patient 0 alerting and reporting](/zia/configuring-patient-0-alert) but provides network visibility for malware that spreads east-west or via a medium that doesn't traverse the Zscaler service (e.g., USB flash drives). Identified file traces include whether the malware execution was detected or prevented by the CrowdStrike Falcon agent. The integration calls the CrowdStrike Falcon API and provides a one-click action to quarantine/contain any endpoints that might be impacted by malware. You can also go to the CrowdStrike portal to further investigate an endpoint device.
To learn more about the Zscaler and CrowdStrike integration, see the [Zscaler and CrowdStrike Deployment Guide](/zscaler-technology-partners/zscaler-and-crowdstrike-deployment-guide).
[]Integrate with [Microsoft Defender for Endpoint](/zia/integrating-microsoft-defender-endpoint) to enable immediate visibility, response, and containment to zero-day, [Sandbox](/zia/about-sandbox)-detected malware with the Microsoft Defender for Endpoint security platform.
Zscaler's integration leverages Microsoft Defender for Endpoint APIs to provide immediate visibility, and containment for advanced persistent threats detected in the Zscaler Sandbox. Through the API integration between Zscaler and Microsoft Defender for Endpoint, Malware detected by the Sandbox is correlated with Microsoft Defender for Endpoint data to identify all endpoints with this file present. Malware can spread laterally across endpoints via malware propagation vectors such as USB or Bluetooth file transfer.
The integration presents Zscaler's patient 0 alerting and reporting alongside a list of identified Microsoft Defender for Endpoint devices, enabling you to quickly assess the impact to the endpoint environment and take action. The Zscaler service shares the Sandbox data with Microsoft Defender for Endpoint so you can generate an alert and trigger an automated investigation. These investigations can expand their scope based on devices that the malicious file has spread to. You can then instruct Microsoft Defender for Endpoint to stop all ongoing process executions associated with the malicious file and quarantine it across all endpoint devices. The Zscaler service creates an indicator of compromise (IOC) in Microsoft Defender for Endpoint to prevent future executions of the file.
To learn more about the Zscaler and Microsoft Defender integration, see the [Zscaler and Microsoft Defender Deployment Guide](/zscaler-technology-partners/zscaler-and-microsoft-defender-deployment-guide).
[]Integrate with [Votiro CDR](/isolation/understanding-votiro-integration-isolation) to further sanitize files accessed through Zscaler Isolation.
Isolation provides the necessary security coverage for organizations accessing internet content. As part of the security coverage provided, files downloaded from the internet are subjected to inline scanning to ensure that any malicious content is blocked. However, users who are consumers of Isolation also use CDR services such as [Votiro](https://votiro.com/resource-center/?fwp_resource_categories=guides). Votiro allows any file downloaded or uploaded to or from internet destinations to be sanitized by the CDR services. These CDR services consume the original file being transacted, and return back a file in the same format as the original file, but sanitized. This ensures that either the active content is stripped out, or active content itself is replaced with a sanitized model, ensuring the file itself cannot be used for malicious purposes.
To learn more about the Zscaler and Votiro integration, see the [Zscaler and Votiro Deployment Guide](/zscaler-technology-partners/zscaler-and-votiro-deployment-guide).