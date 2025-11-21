# SIEM and ZIA Integration Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/siem-zia-integration-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417481.pdf

This guide describes the benefits of integrating your security information and event management (SIEM) into Zscaler, and the steps necessary for configuring Zscaler Internet Access (ZIA) to work with your SIEM. With this integration, Zscaler can send logs related to web, firewall, DNS, and tunnel traffic to the SIEM. To learn more, see [About Nanolog Streaming Service (NSS)](/zia/about-nanolog-streaming-service).
Value of SIEM Integration with ZIA
Integrating a SIEM with ZIA provides the following benefits:
- Comprehensive real-time logging and visibility for all users and locations.
- Facilitates compliance and event correlation.
Deployment Phase
The deployment phase includes initially setting up and integrating Zscaler solutions into an existing network infrastructure. During the deployment phase, you configure ZIA to integrate with your SIEM. The following sections discuss the steps to deploy ZIA and SIEM integration.
There are primarily two ways Zscaler can send logs to the SIEM tool:
- Using Zscaler’s NSS. Zscaler uses [NSS](/zia/about-nanolog-streaming-service) to send the logs to the SIEM. The NSS is a virtual device that sits between the [Zscaler Cloud Nanolog cluster](/zia/about-zscaler-cloud-architecture) and the SIEM. NSS receives encrypted, compressed, and tokenized logs from the cloud and decrypts, uncompresses, and de-tokenizes them. Then NSS converts the logs into a format that the SIEM can process and sends it to the SIEM.
![Using Zscaler NSS](/downloads/zscaler-deployments-operations/zia-deployments-operations/siem-zia-integration-deployment-and-operations-guide/Using%20Zscaler%E2%80%99s%20NSS.png)
- Using cloud-to-cloud log streaming. For customers with a SIEM deployed in the cloud (e.g., Splunk Cloud), Zscaler can send the logs to the cloud provider via HTTPS API.
![Using Zscaler Cloud NSS](/downloads/zscaler-deployments-operations/zia-deployments-operations/siem-zia-integration-deployment-and-operations-guide/Using%20cloud-to-loud%20log%20streaming.png)
Prerequisites
NSS appliances are included with the ZIA Essentials Edition or later. You can optionally add the following:
- For cloud NSS:
- ZIA Transformational Edition and later.
- Cloud NSS subscription.
- For one-hour log recovery capability:
- ZIA Transformational Edition and later.
- NSS Log Recovery subscription.
Separate NSS appliances are required for web and firewall logging.
Deployment Steps
The following steps explain how to integrate ZIA and a SIEM system:
- Understand the SIEM infrastructure. Cloud-to-cloud logging is supported only if the SIEM infrastructure is in the cloud. Zscaler supports cloud-to-cloud logging only if the SIEM vendor supports API-based feeds.
- Only applicable to NSS deployments:
- Identify the correct sizing for the NSS. Depending on the size of the organization and the volume of traffic received by Zscaler, the size of the virtual appliance can vary. Ensure that the virtual machine (VM) is built based on the traffic volume:
- [Sizing guide for AWS](/zia/nss-deployment-guide-amazon-web-services#3).
- [Sizing guide for Azure](/zia/nss-deployment-guide-microsoft-azure).
- [Sizing guide for VMware](/zia/nss-deployment-guide-vmware-vsphere).
- Deploy the NSS. To learn more, see [Deploying NSS Virtual Appliances](/zia/deploying-nss-virtual-appliances).
- Configure the NSS feeds. To learn more, see [About NSS Feeds](/zia/about-nss-feeds).
- Configure firewalls to allow NSS traffic to pass through using the information on the Zscaler Cloud Configuration Requirements for your Zscaler Cloud (e.g., `https://config.zscaler.com/``<cloudname>``/nss`). To learn more, see [What is my cloud name for ZIA](/zia/what-my-cloud-name-zia)?
- [Configure cloud NSS feeds](/zia/about-cloud-nss-feeds) (only applicable to cloud NSS deployments).
Considerations
Review the following considerations:
- You cannot deploy NSS VMs in active-active mode, which means only one NSS server can connect to the cloud at a time. If you want fault-tolerant NSS deployment, deploy NSS in active-standby mode. In active-standby mode, the standby VM remains disconnected from the cloud and becomes active only when the other NSS is completely disconnected from the cloud. Two VMs using the same certificate to connect to the cloud can result in an inconsistent logging experience.
- For a fault-tolerant active-active solution, Zscaler recommends subscribing to two NSS services for web and firewall, and running one VM for web and one VM for firewall logs.
- Zscaler NSS buffers logs for up to one hour. If there is an interruption between the NSS and SIEM (e.g., if the SIEM is unavailable due to maintenance), NSS can buffer the logs for one hour. VM sizing is important to ensure accurate data.
- Each NSS server can support a maximum of 8 configured NSS feeds in different formats to different SIEM IP addresses on different ports.
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune ZIA and SIEM integration during the operations phase to meet your infrastructure needs.
Prerequisites
For ZIA and SIEM operations, complete the following prerequisites:
- Add [NSS feeds for alerts](/zia/adding-nss-feeds-alerts) to ensure that the operations team is alerted when there is an issue on NSS.
- Ensure that the operations team can access the NSS server in case they need to troubleshoot issues.
- Ensure that the NSS IP addresses are included in every relevant standard operating procedure (SOP) document.
Common Troubleshooting Items
The following list describes common issues related to ZIA and SIEM operation:
- [Troubleshooting commands for NSS servers](/zia/troubleshooting-deployed-nss-servers).
- [How to troubleshoot forbidden errors on Zscaler NSS](https://zscaler-support.force.com/customers/s/article/How-to-troubleshoot-issue-with-NSS-which-has-stopped-sending-logs-to-MCAS) that stop it from sending logs to Microsoft Cloud App Security (MCAS).
- [How to troubleshoot NSS cloud logs not getting received on Splunk Cloud](https://zscaler-support.force.com/customers/s/article/How-to-troubleshoot-the-issue-NSS-Cloud-logs-are-not-getting-received-on-Splunk-Cloud).
Deployment and Operations Checklist
Zscaler recommends downloading the [ZIA SIEM Integration Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/siem-zia-integration-deployment-and-operations-guide/ZIA-SIEM-Integration-Deployment-Operations-Checklist.pdf) to help plan and implement ZIA and SIEM integration: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/siem-zia-integration-deployment-and-operations-guide/ZIA-SIEM-Integration-Deployment-Operations-Checklist.pdf)
Additional Information
For more SIEM integration information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com).