# Understanding Disaster Recovery
Source: https://help.zscaler.com/unified/understanding-disaster-recovery
PDF: https://help.zscaler.com/pdf/com/en/1496941.pdf

Enabling disaster recovery ensures business continuity in the event of a disaster scenario that impacts the global Zscaler cloud infrastructure. Disaster recovery is for organizations that depend on the Zscaler cloud to remain operational during disaster events by providing users with access to critical applications.
Zscaler provides support for disaster recovery in both Private Applications and Internet & SaaS.
To provide application access during a global outage:
- Designated application segments, Private Service Edges, and App Connectors must be enabled for disaster recovery.
- A domain name must be configured in the [Disaster Recovery Settings](/zpa/about-disaster-recovery-settings) and the Zscaler Client Connector Profiles. This is used by the admin to trigger Disaster Recovery Mode, and is used by Zscaler Client Connector to look up which Private Service Edges to connect to in Disaster Recovery Mode.
- Two types of DNS records are used for disaster recovery:
- DNS TXT records trigger the activation of disaster recovery.
- DNS A records are used by Zscaler Client Connector to discover the Private Service Edges.
The [Zscaler DNS Record Generator](/unified/understanding-and-installing-zscaler-dns-record-generator) creates the DNS TXT records used for disaster recovery. Activating disaster recovery by uploading the DNS TXT records to the Disaster Recovery Domain Name in the [settings](/unified/about-disaster-recovery-settings) disrupts existing Zscaler Client Connector connections and must be used with caution. Both App Connectors and Private Service Edges that are enabled for disaster recovery restart after disaster recovery is activated via DNS.
Zscaler Client Connector then forwards the M-Tunnels (Microtunnels) of the applications that are designated for disaster recovery to the Private Service Edge. To learn more, see [Configuring Disaster Recovery](/unified/configuring-disaster-recovery).
Disaster recovery allows an organization to test their Business Continuity Plan (BCP) processes to ensure all disaster-recovery-related solutions and systems are working properly. The option to test disaster recovery is supported via Disaster Recovery Test Mode. When Disaster Recovery Test Mode is enabled, the Admin Portal is still accessible.
Any changes made to the cloud via the Admin Portal do not take effect until Disaster Recovery Test Mode is disabled via the DNS records, or the activation record expires. The Admin Portal is not supported during Disaster Recovery Mode.
- [Functions and Features Supported Through Disaster Recovery](#supported)
- []Application segments designated for disaster recovery are accessible when Disaster Recovery Mode is activated.
- Existing and disaster-recovery-generated App Connectors, Private Service Edges, and Zscaler Client Connectors with valid and unexpired certificates are supported.
- Users that are enrolled in the cloud prior to enabling disaster recovery are supported.
- [Functions and Features Not Supported as Part of Disaster Recovery](#drlimits)
- []Authentication and reauthentication
Reauthentication behavior is modified during Disaster Recovery Mode. The SAML assertion validity is extended by 14 days, by default, from the date the SAML assertion was issued. The SAML assertion is issued when a user authenticates or reauthenticates.
- [Browser Access](/unified/about-browser-access)
- Client-To-Client Connectivity
- [Cloud Connectors](/unified/about-cloud-connectors)
- Dashboards and Diagnostics
- Enrollment of new [App Connectors](/unified/about-app-connectors), [Private Service Edges](/unified/about-private-service-edges-private-applications), or Zscaler Client Connectors
- [AppProtection for Private Application Traffic Management](/unified/analytics/private-applications/appprotection-and-browser-protection-monitoring)
- [Log Streaming Service](/unified/logs/private-applications/log-streaming)
- [Machine Tunnels](/unified/deploying-machine-tunnels-pre-windows-login)
- [Microtenants](/unified/about-microtenants)
When in Disaster Recovery Mode, Private Service Edges and App Connectors mapped within a default or custom Microtenant provide traffic to only applications designated for disaster recovery.
- [Policies](/unified/policies)
- [Source IP Anchoring](/unified/understanding-source-ip-anchoring)
- [SCIM Configuration](/unified/about-scim)
- User enrollments
- ZscalerDeception
Prerequisites
Contact Zscaler Support to enable disaster recovery for your tenant before proceeding with the prerequisites.
[]Before enabling disaster recovery, the following prerequisites must be met:
- Deploy and maintain App Connectors and Private Service Edges. To learn more, see [App Connector Deployment Guides for Supported Platforms](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms) and [Private Service Edge Deployment Guides for Supported Platforms](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms).
In the scenario where a Private Service Edge is deployed behind a firewall, your firewalls must be configured to let the Private Service Edge establish outbound connections to the IP addresses of the Public Service Edge, and establish inbound connections from App Connectors and Zscaler Client Connectors. To learn more, see [Private Service Edge Deployment Prerequisites](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms).
- Ensure the end user's machines are running Zscaler Client Connector versions 4.0 and later for Windows, and Zscaler Client Connector version 3.7.1.38 for macOS.
- Download the Zscaler DNS Record Generator. To learn more, see [Understanding and Installing the Zscaler DNS Record Generator](/unified/understanding-and-installing-zscaler-dns-record-generator).
- Identify the critical application segments, App Connector Groups, and Private Service Edge Groups that you want to designate for disaster recovery.
- Create a separate domain name in your DNS for disaster recovery. Then enter the IP addresses of the Private Service Edge designated for disaster recovery into the DNS A record.
After the prerequisites are met, proceed to [configure disaster recovery](/unified/configuring-disaster-recovery).
Navigating Disaster Recovery
On the Disaster Recovery page, you can navigate to the following pages:
- [Disaster Recovery Application Segments](/unified/about-disaster-recovery-application-segments)
- [Disaster Recovery App Connector Groups](/unified/about-disaster-recovery-app-connector-groups)
- [Disaster Recovery Private Service Edge Groups](/zpa/about-disaster-recovery-private-service-edge-groups)
- [Disaster Recovery Settings](/unified/about-disaster-recovery-settings)
You can also download the [Zscaler DNS Record Generator](/unified/understanding-and-installing-zscaler-dns-record-generator). The Zscaler DNS Record Generator creates the DNS TXT records and the public key, which are then used to verify the activation of Disaster Recovery Mode. The public key is uploaded in the [Disaster Recovery Settings](/unified/about-disaster-recovery-settings) and when configuring Zscaler Client Connector Profiles.