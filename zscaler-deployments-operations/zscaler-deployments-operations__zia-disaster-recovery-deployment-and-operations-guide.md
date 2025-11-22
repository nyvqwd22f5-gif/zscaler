# Disaster Recovery Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/zia-disaster-recovery-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1451331.pdf

This deployment and operations guide describes the benefits of using disaster recovery and the steps necessary for configuring Zscaler Internet Access (ZIA) to add disaster recovery to your security posture.
ZIA Disaster Recovery ensures business continuity when an event impacts the global Zscaler cloud infrastructure. Disaster recovery provides an organization's users access to critical applications by ensuring access even if the Zscaler cloud isn’t accessible.
To learn more, see [About Disaster Recovery](/zia/about-disaster-recovery) and [Zscaler Resilience](https://www.zscaler.com/zscaler-resilience).
Value of Deploying Disaster Recovery
ZIA disaster recovery provides the following benefits:
- Business continuity with uninterrupted security in case of:
- Brownout
- Blackout
- Catastrophic failure
- Avoids costly business interruptions or loss of productivity due to lack of access to critical apps.
Deployment Phase
The deployment phase includes initially setting up and integrating Zscaler solutions into an existing network infrastructure. During the deployment phase, you configure disaster recovery to meet the needs of your infrastructure. The deployment phase includes preparation steps needed to enable disaster recovery. The following sections discuss steps to deploy disaster recovery in ZIA.
Prerequisites
ZIA disaster recovery might require an additional license for your organization. Check with your Zscaler Account team to verify the necessary licensing requirements.
The following prerequisites are required for ZIA disaster recovery on the applicable devices:
- ZIA disaster recovery is available for certain [Zscaler Client Connector versions](/zscaler-client-connector/what-is-zscaler-client-connector):
- Zscaler Client Connector version 4.0 or later for Windows
- Zscaler Client Connector version 3.71.38 or later for macOS
- Disaster recovery must be enabled for your organization. Check with your Zscaler Account team to enable disaster recovery.
- Disaster recovery requires a modifiable, customer-owned public DNS record.
Deployment Steps
The following sections cover deployment instructions for ZIA disaster recovery:
- [Create a DNS TXT Record](/zpa/creating-dns-txt-records). Modify the record format values according to your organization’s needs. To learn more, see [About the Zscaler DNS Record Generator](/zpa/about-zscaler-dns-record-generator).
- Enable [Disaster Recovery](/zia/about-disaster-recovery) on an [App Profile](/zscaler-client-connector/configuring-zscaler-client-connector-profiles):
- Specify the **Activation Domain Name** used for the DNS text (TXT) record.
- (Optional) [Upload a public key](/zia/about-disaster-recovery) in order to create a signed DNS record.
- Specify a traffic forwarding action in case of disaster recovery:
- **Send Traffic Direct**: All traffic bypasses Zscaler Client Connector, giving the user access to all applications through direct internet access.
- **Disable Internet Access**: All traffic is dropped at the endpoint and users do not have access.
- **Pre-selected Destinations**: The admin selects to block or allow access to specific URLs using a custom PAC file:
- (Optional) Enable **Use Zscaler Pre-selected Destinations**.
- (Optional) Enable **Use Custom Destinations**.
- (Optional) Enable **Part of ZIA Disaster Recovery Test Group** if this profile is for testing purposes. To learn more, see [Configuring Disaster Recovery Test Mode](/zpa/configuring-disaster-recovery#:~:text=Configuring%20Disaster%20Recovery%20Test%20Mode).
Considerations
Review the following considerations:
- You can find Zscaler pre-selected destinations [here](https://dll7xpq8c5ev0.cloudfront.net/drdb.txt).
- You can define a combination of Zscaler pre-selected destinations and custom destinations for access in a PAC file. This is not a mutually exclusive choice.
- Custom destination URLs take precedence over Zscaler pre-selected destinations. You can block certain Zscaler pre-selected destinations by placing them in the custom destinations PAC file and forwarding the traffic to destination Block.
- An example of the custom PAC file syntax is shown in [About Disaster Recovery](/zia/about-disaster-recovery).
- You cannot use ZIA Virtual Service Edges or Private Service Edges in conjunction with disaster recovery.
- You cannot use any other traffic forwarding decisions than allowing direct access or blocking access to destinations in conjunction with disaster recovery.
- Zscaler recommends testing disaster recovery through the disaster recovery test mode with a handful of users prior to deployment in production environments.
- End users receive an HTTP 403 error if they try to open any blocked page when disaster recovery is on.
- Zscaler Client Connector shows Service Status `Safe Mode` when disaster recovery mode is on.
- When disaster recovery is triggered for a client, that client can only access destinations that are specified as accessible during disaster recovery. Limited access is enforced until disaster recovery is disabled for the client. Even when ZIA services are restored, client machines do not automatically reconnect to the Zscaler cloud until disaster recovery is disabled.
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. You can enable, monitor, and tune ZIA disaster recovery to meet your infrastructure needs.
To enable disaster recovery, customers must adjust the DNS TXT record. At minimum:
- Indicate the DNS record version with `v=1`.
- Enable disaster recovery with` b=on`.
- Enable disaster recovery for ZIA with `k=zia` (and potentially ZPA with` k=all`).
To learn more, see [About the Zscaler DNS Record Generator](/zpa/about-zscaler-dns-record-generator).
Choose the lowest time to live (TTL) possible in the DNS TXT record for swift DNS update propagation downstream (Zscaler recommends 30 seconds).
For testing, after completing the deployment steps described previously, adjust the DNS TXT record as follows:
- v=1
- b=test
- k=zia (for ZIA) or k=all (for ZIA and ZPA)
For more information see [Configuring Disaster Recovery Test Mode](/zpa/configuring-disaster-recovery#:~:text=Configuring%20Disaster%20Recovery%20Test%20Mode).
Common Troubleshooting Tips
- During a catastrophic failure, assume that the ZIA Admin Portal is inaccessible and configuration changes or client enrollments are not possible.
- Zscaler Client Connector checks the DNS TXT record every 200 seconds.
- Take DNS propagation times into account when waiting for Safe Mode to trigger in the Zscaler Client Connector after updating the DNS TXT record.
Deployment and Operations Checklist
Zscaler recommends downloading the [ZIA Disaster Recovery Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-disaster-recovery-deployment-and-operations-guide/ZIA-Disaster-Recovery-Deployment-Operations-Checklist.pdf) to help plan and implement ZIA disaster recovery: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-disaster-recovery-deployment-and-operations-guide/ZIA-Disaster-Recovery-Deployment-Operations-Checklist.pdf)
Additional Information
For more SaaS Security information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com/).