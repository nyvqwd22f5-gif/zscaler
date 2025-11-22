# About Disaster Recovery App Connector Groups
Source: https://help.zscaler.com/unified/about-disaster-recovery-app-connector-groups
PDF: https://help.zscaler.com/pdf/com/en/1496966.pdf

Disaster recovery App Connector groups are App Connector groups designated as available for disaster recovery to ensure business continuity in the scenario of a disaster event.
Disaster recovery App Connector groups provide the following benefits and enable you to:
- Ensure business continuity in the event of a disaster scenario that impacts the global Zscaler cloud infrastructure.
- Provide users with access to critical App Connectors during a disaster scenario.
After an App Connector Group is designated for disaster recovery, both configuration and binary snapshots are saved in the local configuration files on your App Connector and are used for backup purposes. The Zscaler cloud maintains up to 15 prior configuration snapshots and up to 5 prior binary snapshots, and updates both snapshots periodically. To learn more, see [Understanding Disaster Recovery](/unified/understanding-disaster-recovery), [Configuring App Connectors](/unified/configuring-app-connectors), and [Managing Disaster Recovery Configuration and Binary Snapshots](/unified/managing-disaster-recovery-configuration-and-binary-snapshots).
About the Disaster Recovery App Connector Groups Page
On the Disaster Recovery App Connector Groups page (Infrastructure > Private Access > Business Continuity> Disaster Recovery), you can do the following:
- View a list of all deployed App Connector Groups that are designated for disaster recovery.
- Go to the [Disaster Recovery Application Segments](/unified/about-disaster-recovery-application-segments) page to view the application segments designated for disaster recovery.
- Go to the [Disaster Recovery Private Service Edge Groups](/unified/about-disaster-recovery-private-service-edge-groups) page to view the Private Service Edge groups designated for disaster recovery.
- Go to the [Disaster Recovery Settings](/unified/about-disaster-recovery-settings) page to configure the authentication, the disaster recovery public key, and the disaster recovery domain name.
- Download the [Zscaler DNS Record Generator](/unified/understanding-and-installing-zscaler-dns-record-generator). The Zscaler DNS Record Generator creates the DNS TXT records and the public key used to verify the activation of Disaster Recovery Mode for use with disaster recovery.
![Viewing the Disaster Recovery App Connector Groups page in the ZPA Admin Portal](/downloads/unified/networking/private-applications/disaster-recovery-administration/about-disaster-recovery-private-service-edge-groups/dr-app-connector-groups-page.png)