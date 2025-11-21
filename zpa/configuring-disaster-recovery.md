# Configuring Disaster Recovery
Source: https://help.zscaler.com/zsdk/configuring-disaster-recovery
PDF: https://help.zscaler.com/pdf/com/en/1525921.pdf

When disaster recovery mode starts, those critical applications designated for disaster recovery are accessible, which allows your organization to continue operations securely.
Prerequisites
[]Before enabling disaster recovery, the following prerequisites in your environment must be met:
- Identify critical application segments, App Connector groups, and ZSDK Private Service Edge groups to designate for disaster recovery.
- Ensure the end user's machines are running ZSDK version 2.0 or later.
-
Create a separate domain name in your DNS for disaster recovery. Then enter the IP addresses of the Private Service Edges designated for disaster recovery into the [TXT DNS A record](#dnsa).
Ensure your TXT DNS A record has the following format: `v=1;k=all;b=off;d=``your.disaster-recovery.domain`.
[]Disaster Recovery Settings
On the Disaster Recovery Settings page (Administration Control > Disaster Recovery > Settings):
- **Max Age for Authentication**: Enter a numerical value and select an age type (**Hours**, **Days**, **Weeks**).
- **Disaster Recovery Public Key**: Upload a public key.
- **Disaster Recovery Domain Name**: Enter the domain name.
![Configure Disaster Recovery Settings](/downloads/zsdk/private-service-edge/configuring-disaster-recovery/zsdk-disaster-recovery-settings.png)
[]Disaster Recovery Configuration in ZSDK and Cloud Computing Platforms
To provide application access during a global Zscaler outage, you must configure the following:
- In the ZSDK Admin Portal:
- [Define application segments for disaster recovery.](/zsdk/defining-and-managing-application-segments#define-generalinfo)
-
[Deploy Private Service Edges](/zsdk/deploying-zsdk-private-service-edges) that are enabled for disaster recovery.
If your Private Service Edge is deployed behind a firewall, your firewall must be configured to let the Private Service Edge establish outbound connections to the IP addresses of the Public Service Edge, and establish inbound connections from App Connectors and Zscaler Client Connectors. To learn more, see [Deployment Prerequisites](/zpa/zpa-service-edge-deployment-prerequisites).
- Deploy App Connectors that are enabled for disaster recovery.
- Provide a domain name for [Disaster Recovery Settings](#Settings).
-
For your cloud computing platforms, create two types of DNS records:
-
**DNS TXT**: Triggers the activity of disaster recovery.
If this is the initial version, then enter the following: `v=1;k=all;b=on;d=dr.``domain``.com`. Replace domain with your organization's domain.
When `b=on`, disaster recovery is enabled for your organization's domain.
- []**DNS A**: Used by Zscaler Client Connector to discover the Private Service Edges. Enter the IP address for your domain name.
After the DNS records are created, upload them onto your cloud computing platforms.
Upon a successful upload, the ZSDK client attempts connections to the Private Service Edges that are enabled for disaster recovery.