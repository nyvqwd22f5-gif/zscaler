# Disaster Recovery Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/zpa-disaster-recovery-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1451411.pdf

This guide describes the benefits of using disaster recovery and the steps necessary for configuring Zscaler Private Access (ZPA) to add disaster recovery to your security posture.
ZPA disaster recovery ensures business continuity if an event impacts the global Zscaler cloud infrastructure. Disaster recovery provides an organization's users access to critical applications by ensuring access even if the Zscaler cloud isn’t accessible.
To learn more, see [Understanding Disaster Recovery](/zpa/understanding-disaster-recovery) or [Zscaler Resilience](https://www.zscaler.com/zscaler-resilience).
Value of Deploying ZPA Disaster Recovery
ZPA disaster recovery provides the following benefits when Zscaler cloud infrastructure is completely unavailable:
- Business continuity with uninterrupted access to critical business applications in case of a global ZPA cloud infrastructure outage.
- Avoid costly business interruptions or loss of productivity due to a lack of access to critical business applications.
Deployment Phase
The deployment phase includes initially setting up and integrating Zscaler solutions into an existing network infrastructure. During the deployment phase, you configure disaster recovery to meet the needs of your infrastructure.
The following sections discuss steps to deploy disaster recovery in ZPA.
Prerequisites
ZPA disaster recovery might require additional licenses. Check with your Zscaler Account team to see if you have the necessary licensing requirements.
For ZPA disaster recovery deployment, verify and complete the following prerequisites:
- Enable the disaster recovery feature. Check with your Zscaler Account team to enable it.
- Identify which [critical application segments](/zpa/configuring-application-segments#define-generalinfo), [App Connector Groups](/zpa/configuring-connectors#createconnectorgroup), and [ZPA Private Service Edge Groups](/zpa/configuring-service-edges#addgroup) to designate for disaster recovery use.
- Deploy or identify which [App Connector](/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms) disaster recovery uses.
- Deploy or identify which [ZPA Private Service Edges](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) disaster recovery uses. Check with your Zscaler Account team if you are eligible to use ZPA Private Service Edges.
- Ensure the end user’s machines run [Zscaler Client Connector](/client-connector/downloading-zscaler-client-connector) version 4.0 or later for Windows.
- Ensure the end user’s machines run [Zscaler Client Connector](/client-connector/downloading-zscaler-client-connector) version 3.7.1.38 or later for macOS.
- Create a public DNS record that is customer-owned and modifiable to enable and disable disaster recovery.
- Download the [Zscaler DNS Record Generator](/zpa/about-zscaler-dns-record-generator#install) (Windows only).
- Create a separate domain name in your DNS for disaster recovery. Then enter the public IP addresses of the ZPA Private Service Edge designated for disaster recovery into the DNS A record.
Deployment Steps
The following sections cover deployment instructions for ZPA disaster recovery:
- Ensure that you’ve met the prerequisites.
- [Configure disaster recovery for an application segment](/zpa/configuring-application-segments#define-generalinfo).
- Configure disaster recovery for an [App Connector group](/zpa/configuring-connectors#createconnectorgroup).
- [Configure disaster recovery for a ZPA Private Service Edge group](/zpa/configuring-service-edges#addgroup).
- Configure the [disaster recovery settings](/zpa/about-disaster-recovery-settings).
- Capture all the public IP addresses of the ZPA Private Service Edges designated for disaster recovery and add them to the record for the disaster recovery domain name. You can find public IP of the ZPA Private Service Edge in [About ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).
- Configure the disaster recovery settings for an App Profile in Zscaler Client Connector. To learn more, see [Configuring Zscaler Client Connector App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles).
In Disaster Recovery Test Mode, App Connector in an App Connector group restart their zpa-connector services and Private Service Edges restart their zpa-service-edge service. When the services are restarted, user connections to the test App Connector and Private Service Edges are dropped. Unless part of the test group, new connections are not established with the Test Mode App Connectors and Private Service Edges. To learn more about how to enable disaster recovery test mode, see [Configuring Disaster Recovery Test Mode](/zpa/configuring-disaster-recovery#:~:text=Configuring%20Disaster%20Recovery%20Test%20Mode).
Considerations
Review the following considerations:
- Activate disaster recovery via the DNS records with caution, as it disrupts existing Zscaler Client Connector connections. The services for both App Connector (zpa-connector) and ZPA Private Service Edges (zpa-service-edge) that are enabled for disaster recovery restart after disaster recovery is activated via DNS.
- An application segment with disaster recovery enabled must be associated with a server group. The server group must be associated with at least one App Connector Group designated for disaster recovery.
- Ensure you choose the lowest possible TTL (Zscaler recommends 30 seconds) for swift DNS update propagation.
- When disaster recovery is triggered, App Connectors and Private Service Edges designated for disaster recovery usage cut connections to the Zscaler cloud and only provide access to the applications that have been designated for disaster recovery usage.
- Clients that have disaster recovery triggered only access applications designated for disaster recovery usage as long as disaster recovery is enabled. Even after ZPA services are restored, the client machines do not automatically reconnect to the Zscaler cloud unless disaster recovery is disabled.
- Disaster recovery supports the following functions and features:
- Access is allowed only through the Zscaler Client Connector.
- Application segments designated for disaster recovery are accessible when Disaster Recovery Mode is activated.
- Existing and disaster-recovery-generated App Connectors, ZPA Private Service Edges, and Zscaler Client Connectors with valid and unexpired certificates.
- Users enrolled in the ZPA Cloud prior to enabling disaster recovery.
- Disaster recovery doesn’t support the following functions and features:
- Authentication and reauthentication. (Reauthentication behavior is modified during disaster recovery. By default, the Security Assertion Markup Language (SAML) assertion validity is extended by 14 days from the date the SAML assertion was issued. The SAML assertion is issued when a user reauthenticates. You can customize the value.)
- [Browser Access](/zpa/about-browser-access).
- [Client-Based Remote Assistance](/zpa/about-client-based-remote-assistance).
- [Cloud Connectors](/zpa/about-cloud-connectors).
- [Dashboards and Diagnostics](/zpa/dashboard-diagnostics).
- Enrollment of new [App Connectors](/zpa/about-connectors), [ZPA Private Service Edges](/zpa/about-zpa-private-service-edges), or [Zscaler Client Connector](/zscaler-client-connector/what-is-zscaler-client-connector).
- [AppProtection for Private Application Traffic](/zpa/appprotection-private-application-traffic-formerly-inspection).
- [Log Streaming Service](/zpa/log-streaming-service).
- [Machine Tunnels](/zpa/deploying-machine-tunnels-pre-windows-login).
- [Policies ](/zpa/policies)or configuration updates.
- [Source IP Anchoring](/zia/about-source-ip-anchoring).
- [SCIM Configuration](/zpa/about-scim).
- User enrollments.
- [Zscaler Deception](/deception/what-zscaler-deception).
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. You can enable, monitor, and tune ZPA disaster recovery to meet your infrastructure needs.
After performing the deployment steps, customers must adjust the DNS TXT record according to the format guidelines described in [About the DNS Record Generator](/zpa/about-zscaler-dns-record-generator) to enable disaster recovery. At a minimum, ensure the following tags are set:
- v=1 to indicate the DNS record version.
- b=on to enable disaster recovery.
- k=zpa or k=all (for ZPA and ZIA).
Choose the lowest TTL for the DNS TXT record (Zscaler recommends 30 seconds) for swift DNS update propagation downstream.
For testing, make the following DNS TXT adjustments:
- v=1
- b=test
- k=zpa or k=all (for ZPA and ZIA)
In Disaster Recovery Test Mode, all App Connectors in an App Connector group that are designated for disaster recovery restart their zpa-connector services, and all ZPA Private Service Edges in a ZPA Private Service Edge group that are designated for disaster recovery restart their zpa-service-edge services. When the services restart, existing user connections to the test App Connectors and ZPA Private Service Edges that are designated for disaster recovery are dropped. New connections for regular users that are not part of the disaster recovery test group are routed through either ZPA Public Service Edges or regular ZPA Private Service Edges and App Connectors that are not designated for disaster recovery. Users participating in disaster recovery testing that are part of the disaster recovery test group also form new connections to the ZPA Private Service Edges and App Connectors that are part of the test mode. To learn more about how to enable disaster recovery test mode, see [Configuring Disaster Recovery Test Mode](/zpa/configuring-disaster-recovery#:~:text=Configuring%20Disaster%20Recovery%20Test%20Mode).
Common Troubleshooting Items
- During ZPA global outage, customers should assume that the ZPA Admin Portal is unavailable and configuration changes, client enrollments, or new user authentication are not possible.
- Zscaler Client Connector checks the DNS TXT record every 200 seconds.
- Consider DNS propagation times when updating the DNS TXT record and waiting for Safe Mode to trigger in the Zscaler Client Connector.
- You can run the journaltctl -f command on the ZPA Public Service Edge. Look for the message to confirm that disaster recovery is successfully triggered: `DR mode is activated!`
- To learn more about App Connector troubleshooting information and guidelines, see [Troubleshooting App Connectors](/zpa/troubleshooting-app-connectors).
- To learn more about ZPA Private Service Edge troubleshooting information and guidelines, see [Troubleshooting ZPA Private Service Edges](/zpa/troubleshooting-zpa-private-service-edges).
Deployment and Operations Checklist
Zscaler recommends downloading the [ZPA Disaster Recovery Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zpa-deployments-operations/zpa-disaster-recovery-deployment-and-operations-guide/ZPA-Disaster-Recovery-Deployment-Operations-Checklist.pdf) to help plan and implement ZPA disaster recovery: [Download PDF](/downloads/zscaler-deployments-operations/zpa-deployments-operations/zpa-disaster-recovery-deployment-and-operations-guide/ZPA-Disaster-Recovery-Deployment-Operations-Checklist.pdf)
Additional Information
For more disaster recovery information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com).