# About Disaster Recovery Private Service Edge Groups
Source: https://help.zscaler.com/unified/about-disaster-recovery-private-service-edge-groups
PDF: https://help.zscaler.com/pdf/com/en/1496986.pdf

Disaster recovery Private Service Edge groups are Private Service Edge groups designated as available for disaster recovery to ensure business continuity in the event of a disaster scenario.
Disaster recovery Private Service Edge groups provide the following benefits and enable you to:
- Ensure business continuity in the event of a disaster scenario that impacts the global Zscaler cloud infrastructure.
- Provide users with access to critical Private Service Edges during a disaster scenario.
After a Private Service Edge Group is designated for disaster recovery, both configuration and binary snapshots are saved in the local configuration files on your Private Service Edge and are used for backup purposes. The Zscaler cloud maintains up to 15 active configuration snapshots and up to 5 active binary snapshots, and updates both snapshots periodically. To learn more, see [Understanding Disaster Recovery](/unified/understanding-disaster-recovery), [Configuring Private Service Edges](/unified/configuring-private-service-edges-private-applications), and [Managing Configuration and Binary Snapshots](/unified/managing-disaster-recovery-configuration-and-binary-snapshots).
In the scenario where a Private Service Edge is deployed behind a firewall, your firewalls must be configured to let the Private Service Edge establish outbound connections to the IP addresses of the Public Service Edge, and establish inbound connections from App Connectors and Zscaler Client Connectors. To learn more, see [Private Service Edge Deployment Prerequisites](/unified/private-service-edge-deployment-prerequisites#SpecsSizing).
[]About the Disaster Recovery Private Service Edge Groups Page
On the Disaster Recovery Private Service Edge Groups page (Infrastructure > Private Access > Business Continuity> Disaster Recovery), you can do the following:
- View a list of all deployed Private Service Edge Groups that are designated for disaster recovery.
- Go to the [Disaster Recovery Application Segments](/unified/about-disaster-recovery-application-segments) page to view the application segments designated for disaster recovery.
- Go to the [Disaster Recovery App Connector Groups](/unified/about-disaster-recovery-app-connector-groups) page to view the App Connector Groups designated for disaster recovery.
- Go to the [Disaster Recovery Settings](/unified/about-disaster-recovery-settings) page to configure the authentication, disaster recovery public key, and disaster recovery domain name.
- Download the [Zscaler DNS Record Generator](/unified/understanding-and-installing-zscaler-dns-record-generator). The Zscaler DNS Record Generator creates the DNS TXT records and the public key used to verify the activation of Disaster Recovery Mode for use with disaster recovery.
![Viewing the Disaster Recovery Service Edge Groups in the ZPA Admin Portal](/downloads/unified/networking/private-applications/disaster-recovery-administration/about-disaster-recovery-app-connector-groups/dr-private-service-edge-groups-page.png)