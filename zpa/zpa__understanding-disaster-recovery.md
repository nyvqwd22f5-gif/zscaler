# Understanding Disaster Recovery
Source: https://help.zscaler.com/zpa/understanding-disaster-recovery
PDF: https://help.zscaler.com/pdf/com/en/1485391.pdf

Enabling disaster recovery ensures business continuity in the event of a disaster scenario that impacts the global Zscaler cloud infrastructure. Disaster recovery is for organizations that depend on the Zscaler cloud to remain operational during disaster events by providing users with access to critical applications.
Zscaler provides support for disaster recovery in both ZPA and ZIA. The contents in this article are about disaster recovery in Zscaler Private Access (ZPA). To learn more about disaster recovery in ZIA, see [About Disaster Recovery](/zia/about-disaster-recovery).
To provide application access during a global ZPA outage:
- Designated application segments, ZPA Private Service Edges, and App Connectors must be enabled for disaster recovery.
- A domain name must be configured in the [Disaster Recovery Settings](/zpa/about-disaster-recovery-settings) and the [Zscaler Client Connector Profiles](/client-connector/configuring-zscaler-client-connector-profiles). This is used by the ZPA admin to trigger Disaster Recovery Mode, and is used by Zscaler Client Connector to look up which ZPA Private Service Edges to connect to in Disaster Recovery Mode.
- Two types of DNS records are used for disaster recovery:
- DNS TXT records trigger the activation of disaster recovery.
- DNS A records are used by Zscaler Client Connector to discover the ZPA Private Service Edges.
The [Zscaler DNS Record Generator](/zpa/about-zscaler-dns-record-generator) creates the DNS TXT records used for disaster recovery. Activating disaster recovery by uploading the DNS TXT records to the Disaster Recovery Domain Name in the [settings](/zpa/about-disaster-recovery-settings) disrupts existing Zscaler Client Connector connections and must be used with caution. Both App Connectors and ZPA Private Service Edges that are enabled for disaster recovery restart after disaster recovery is activated via DNS.
Zscaler Client Connector then forwards the M-Tunnels (Microtunnels) of the applications that are designated for disaster recovery to the ZPA Private Service Edge. To learn more, see [Configuring Disaster Recovery](/zpa/configuring-disaster-recovery).
Disaster recovery allows an organization to test their ZPA Business Continuity Plan (BCP) processes to ensure all disaster-recovery-related solutions and systems are working properly. The option to test disaster recovery is supported via Disaster Recovery Test Mode. When Disaster Recovery Test Mode is enabled, the ZPA Admin Portal is still accessible.
Any changes made to the ZPA cloud via the ZPA Admin Portal do not take effect until Disaster Recovery Test Mode is disabled via the DNS records, or the activation record expires. To learn more, see [Configuring Zscaler Client Connector Profiles](/client-connector/configuring-zscaler-client-connector-profiles#windows). The ZPA Admin Portal is not supported during Disaster Recovery Mode.
- [Functions and Features Supported Through Disaster Recovery](#supported)
- []Application segments designated for disaster recovery are accessible when Disaster Recovery Mode is activated.
- Existing and disaster-recovery-generated App Connectors, ZPA Private Service Edges, and Zscaler Client Connectors with valid and unexpired certificates are supported.
- Users that are enrolled in the ZPA cloud prior to enabling disaster recovery are supported.
- [Functions and Features Not Supported as Part of Disaster Recovery](#drlimits)
- []Authentication and reauthentication
Reauthentication behavior is modified during Disaster Recovery Mode. The SAML assertion validity is extended by 14 days, by default, from the date the SAML assertion was issued. The SAML assertion is issued when a user authenticates or reauthenticates.
- [Browser Access](/zpa/about-browser-access)
- [Client-To-Client Connectivity](/zpa/understanding-client-client-connectivity)
- [Cloud Connectors](/zpa/about-cloud-connectors)
- [Dashboards and Diagnostics](/zpa/dashboard-diagnostics)
- Enrollment of new [App Connectors](/zpa/about-connectors), [ZPA Private Service Edges](/zpa/about-zpa-private-service-edges), or [Zscaler Client Connectors](/z-app/what-zscaler-app)
- [AppProtection for Private Application Traffic Management](/zpa/appprotection-private-application-traffic-formerly-inspection)
- [Log Streaming Service](/zpa/log-streaming-service)
- [Machine Tunnels](/zpa/deploying-machine-tunnels-pre-windows-login)
- [Microtenants](/zpa/about-microtenants)
When in Disaster Recovery Mode, ZPA Private Service Edges and App Connectors mapped within a default or custom Microtenant provide traffic to only applications designated for disaster recovery.
- [Policies](/zpa/policies)
- [Source IP Anchoring](/zia/about-source-ip-anchoring)
- [SCIM Configuration](/zpa/about-scim)
- User enrollments
- [ZscalerDeception](/deception/what-zscaler-deception)
Prerequisites
[]Before enabling disaster recovery, the following prerequisites must be met:
- Deploy and maintain App Connectors and ZPA Private Service Edges. To learn more, see [App Connector Deployment Guides for Supported Platforms](/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms) and [Private Service Edge Deployment Guides for Supported Platforms](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms).
In the scenario where a ZPA Private Service Edge is deployed behind a firewall, your firewalls must be configured to let the ZPA Private Service Edge establish outbound connections to the IP addresses of the ZPA Public Service Edge, and establish inbound connections from App Connectors and Zscaler Client Connectors. To learn more, see [ZPA Private Service Edge Deployment Prerequisites](/zpa/zpa-service-edge-deployment-prerequisites#SpecsSizing).
- Ensure the end user's machines are running [Zscaler Client Connector](/client-connector/downloading-zscaler-client-connector) versions 4.0 and later for Windows, and Zscaler Client Connector version 3.7.1.38 for macOS.
- Download the Zscaler DNS Record Generator. To learn more, see [Understanding and Installing the Zscaler DNS Record Generator](/zpa/understanding-and-installing-zscaler-dns-record-generator).
- Identify the critical application segments, App Connector Groups, and ZPA Private Service Edge Groups that you want to designate for disaster recovery.
- Create a separate domain name in your DNS for disaster recovery. Then enter the IP addresses of the ZPA Private Service Edge designated for disaster recovery into the DNS A record.
After the prerequisites are met, proceed to [configure disaster recovery](/zpa/configuring-disaster-recovery).
Navigating Disaster Recovery
On the Disaster Recovery page (Configuring & Control > Administration Control > Disaster Recovery), you can navigate to the following pages:
- [Disaster Recovery Application Segments](/zpa/about-disaster-recovery-application-segments)
- [Disaster Recovery App Connector Groups](/zpa/about-disaster-recovery-app-connector-groups)
- [Disaster Recovery Private Service Edge Groups](/zpa/about-disaster-recovery-private-service-edge-groups)
- [Disaster Recovery Settings](/zpa/about-disaster-recovery-settings)
You can also download the [Zscaler DNS Record Generator](/zpa/understanding-and-installing-zscaler-dns-record-generator). The Zscaler DNS Record Generator creates the DNS TXT records and the public key, which are then used to verify the activation of Disaster Recovery Mode. The public key is uploaded in the [Disaster Recovery Settings](/zpa/about-disaster-recovery-settings) and when configuring [Zscaler Client Connector Profiles](/client-connector/configuring-zscaler-client-connector-profiles).